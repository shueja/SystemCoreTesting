# ChoreoLib


## Vendordep URL
`https://choreo.autos/lib/ChoreoLib2027Alpha.json`

## Changelog
### 2027.0.0-alpha-1
The first release of 2027 Choreo is just ChoreoLib 2025.0.3 (latest stable 2025 version) compiled for the SystemCore. It is compatible with Choreo GUI 2025.0.3. Minimal internal changes were necessary, most significantly the usage reporting.

### 2027.0.0-alpha-3
This release is just ChoreoLib 2026.0.3 (latest stable 2026 version) compiled for the SystemCore. It is compatible with Choreo 2026 projects, but needs Choreo GUI 2027.0.0-alpha-3, which produces WPILib 2027 compatible generated Java code.

Usage of existing API is the same.
* The sample classes have `getChassisSpeeds` still, despite the rename of `ChassisSpeeds` to `ChassisVelocities`. 
* AutoChooser is now published with `Tunables.publish("chooser", chooser);` and will show up as `/Tunables/chooser` on NetworkTables. 

**Opmode Usage (Java)**

A helper has been added for that single opmode which just runs the AutoChooser selection. Example code (make sure your `Robot` class extends `OpModeRobot`)

```java
import choreo.auto.AutoChooserOpMode;.
//...
    Tunables.publish("chooser", autoChooser);
    autoChooser.addRoutine("MyAuto", ()->{
      var routine = autoFactory.newRoutine("myroutinename");
      //...whatever setup
      return routine;
    });
    addOpMode( RobotMode.AUTONOMOUS, "RunAutoChooser", ()->new AutoChooserOpMode(autoChooser));
    publishOpModes();
```
Note that the AutoChooser object will exist for the lifetime of the robot. The `AutoChooserOpMode` object is constructed when the option is selected.
