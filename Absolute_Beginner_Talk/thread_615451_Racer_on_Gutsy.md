---
title: "Racer on Gutsy"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-11-17
I tried to install Racer from [www.racer.nl](www.racer.nl)
followed their procedure, even downloaded fmod and copied its in /usr/bin.
now i am getting:

asdfg@asdfghj::~/Documents/racer0.5.0$ sudo bin/racer
bin/racer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

---

### Post by KIAaze on 2007-11-17
Try reinstalling libstdc++2.10-glibc2.2 (**make sure you have enough space left on disk before doing that since it is a very critical system package!**)
A failure during a reinstallation of libstdc++ once broke my Debian.

If that doesn't help (or if you don't want to reinstall that package right away), please post the output of:
```
ls -l /usr/lib/libstdc*
```
and
```
ldd bin/racer
```

edit:
Also, **never use sudo if not needed!**
I see that you ran "sudo bin/racer".
If racer is the game, it doesn't need any root permissions.
Those are only required during the installation process.

---

### Post by shoaibi on 2007-11-17
no its running now,
is it only playable by mouse?
and also there isn't any sound.


output on terminal when i start game:
```

chevaliar@eagles-nest:~/Documents/racer0.5.0$ sudo bin/racer
--- session separator ---
  local host: 'eagles-nest'/127.0.1.1
RTime:Reset()
RAudio ctor
RAudio:Load(); enable=0
FMOD initializing
Disabling FSOUND output (NOSOUND)
RAudio:GetSample(data/audio/heli_inside.wav)
Setting sample loop
FMOD Playing channel: 0
RMenuDestroy()
RMenu Destroy(); count=8
RMenuDestroy()
RSplineRep:ctor (this=0x86480a0)
timeLines=6
RSplineRep:Reserve(339)
SplineRep: lines=339, curLine=339
RSplineRep:ctor (this=0x862a6b0)
Loading VRML track (0x8629210)
timeLines=6
RSplineRep:Reserve(339)
SplineRep: lines=339, curLine=339
  ReadTGA: 24-bit compressed
DTexturePool:FindAll(road*)
DAABBTree:BuildTree()
DAABBTree:BuildTree() DONE
RTrack dtor
RSplineRep:dtor (this=0x86480a0)
RNetwork:ConnectToServer(); clients=0
RNetwork: waiting for connecting id...
>>>>>>>>>>>>>>> SetClientID 50
server: 127.0.0.1
client#1 (slave): 127.0.0.1
>>>>>>>>>>>>>>> GetClientID 50
RNetwork: succesfully connected to server.
RControls: indirection to 'mouse.ini'
RTime:Reset()
RTime:Start()
  ACCEPT car at gridPos 0
InNewCar: ownerClientID=50 (index 0)
REngine:Load(); engine mass=100.000000
fname_torque='torque.crv', maxTorque=180.00
RModel:Load; file 'body.dof' (buf=body.model.file)
Archive try 'body.dof' as data/cars/a110_03/body.dof
( 1.620, 0.830, 4.050 ) [Body indicated size]
( 1.554, 0.993, 3.875 ) [Body model-calc'ed size]
RModel:Load; file 'body.dof' (buf=body.model_incar.file)
Archive try 'body.dof' as data/cars/a110_03/body.dof
RModel:Load; file 'brakelights.dof' (buf=body.model_braking_l.file)
Archive try 'brakelights.dof' as data/cars/a110_03/brakelights.dof
RWing:Load(aero.wing0)
RModel:Load; file 'lwheel.dof' (buf=wheel0.model.file)
Archive try 'lwheel.dof' as data/cars/a110_03/lwheel.dof
RModel:Load; file 'rwheel.dof' (buf=wheel1.model.file)
Archive try 'rwheel.dof' as data/cars/a110_03/rwheel.dof
RModel:Load; file 'lwheel.dof' (buf=wheel2.model.file)
Archive try 'lwheel.dof' as data/cars/a110_03/lwheel.dof
RModel:Load; file 'rwheel.dof' (buf=wheel3.model.file)
Archive try 'rwheel.dof' as data/cars/a110_03/rwheel.dof
RModel:Load; file 'steer.dof' (buf=steer.model.file)
Archive try 'steer.dof' as data/cars/a110_03/steer.dof
declutch=300, clutch=300 (buf=engine.shifting.time_to_clutch)
RAudio:GetSample(data/cars/a110_03/engine.wav)
Setting sample loop
Setting sample loop
FMOD Playing channel: 1
RAudio:GetSample(data/cars/a110_03/skid.wav)
Setting sample loop
FMOD Playing channel: 2
RAudio:GetSample(data/audio/shift.wav)
Setting sample loop
Setting sample loop
RAudio:GetSample(data/audio/shift_miss.wav)
Setting sample loop
Setting sample loop
RAudio:GetSample(data/audio/starter.wav)
Setting sample loop
Setting sample loop
Driveline (RCar ctor); clutch: app=1.00, maxT=300.00, T=100.00
comp. 'engine', ratio 1.00 (cum. 12.17, 1/1.00), inertia 0.20 (effective 52.01)
  comp. 'gearbox', ratio 3.61 (cum. 12.17, 1/0.28), inertia 0.13 (effective 22.41)
    comp. 'differential', ratio 3.37 (cum. 3.37, 1/0.30), inertia 0.05 (effective 3.17)
      comp. 'wheel2', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
      comp. 'wheel3', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
RCar:CalcStaticProps(); m=728.000000
RRigid:SetMassInertia(728.000000)
RBody:DbgCheck(RCar:Load())
Type of car: owner=50, thisMachineID=50
( -34.545, 1.688, -115.958 ) [Warp from]
( -28.979, 1.688, -106.037 ) [Warp from]
( -5.567, -0.000, -9.921 ) [Warp axis]
 _                           _
|     -0.87    -0.00    -0.49 | Source matrix for quat
|      0.00     1.00    -0.00 |
|_     0.49    -0.00    -0.87_|
 _                           _
|     -0.87    -0.00    -0.49 | Result matrix from quat
|     -0.00     1.00    -0.00 |
|_     0.49    -0.00    -0.87_|
( -33.555, 2.288, -114.192 ) [vBodyPos plus warp offsetY]
Driveline (RCar ctor); clutch: app=0.00, maxT=300.00, T=0.00
comp. 'engine', ratio 1.00 (cum. 7.95, 1/1.00), inertia 0.20 (effective 21.51)
  comp. 'gearbox', ratio 2.36 (cum. 7.95, 1/0.42), inertia 0.09 (effective 8.86)
    comp. 'differential', ratio 3.37 (cum. 3.37, 1/0.30), inertia 0.05 (effective 3.17)
      comp. 'wheel2', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
      comp. 'wheel3', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
FMOD Playing channel: 3
Driveline (RCar ctor); clutch: app=0.00, maxT=300.00, T=0.00
comp. 'engine', ratio 1.00 (cum. 5.70, 1/1.00), inertia 0.20 (effective 11.93)
  comp. 'gearbox', ratio 1.69 (cum. 5.70, 1/0.59), inertia 0.07 (effective 5.44)
    comp. 'differential', ratio 3.37 (cum. 3.37, 1/0.30), inertia 0.05 (effective 3.17)
      comp. 'wheel2', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
      comp. 'wheel3', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
FMOD Playing channel: 4099
Switch back to futureGear=3
Driveline (RCar ctor); clutch: app=0.00, maxT=300.00, T=0.00
comp. 'engine', ratio 1.00 (cum. 7.95, 1/1.00), inertia 0.20 (effective 21.51)
  comp. 'gearbox', ratio 2.36 (cum. 7.95, 1/0.42), inertia 0.09 (effective 8.86)
    comp. 'differential', ratio 3.37 (cum. 3.37, 1/0.30), inertia 0.05 (effective 3.17)
      comp. 'wheel2', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
      comp. 'wheel3', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
FMOD Playing channel: 4100
Driveline (RCar ctor); clutch: app=0.00, maxT=300.00, T=0.00
comp. 'engine', ratio 1.00 (cum. 5.70, 1/1.00), inertia 0.20 (effective 11.93)
  comp. 'gearbox', ratio 1.69 (cum. 5.70, 1/0.59), inertia 0.07 (effective 5.44)
    comp. 'differential', ratio 3.37 (cum. 3.37, 1/0.30), inertia 0.05 (effective 3.17)
      comp. 'wheel2', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
      comp. 'wheel3', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
FMOD Playing channel: 4101
Switch back to futureGear=3
Driveline (RCar ctor); clutch: app=0.00, maxT=300.00, T=0.00
comp. 'engine', ratio 1.00 (cum. 7.95, 1/1.00), inertia 0.20 (effective 21.51)
  comp. 'gearbox', ratio 2.36 (cum. 7.95, 1/0.42), inertia 0.09 (effective 8.86)
    comp. 'differential', ratio 3.37 (cum. 3.37, 1/0.30), inertia 0.05 (effective 3.17)
      comp. 'wheel2', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
      comp. 'wheel3', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
FMOD Playing channel: 4102
Switch back to futureGear=2
Driveline (RCar ctor); clutch: app=0.00, maxT=300.00, T=0.00
comp. 'engine', ratio 1.00 (cum. 12.17, 1/1.00), inertia 0.20 (effective 52.01)
  comp. 'gearbox', ratio 3.61 (cum. 12.17, 1/0.28), inertia 0.13 (effective 22.41)
    comp. 'differential', ratio 3.37 (cum. 3.37, 1/0.30), inertia 0.05 (effective 3.17)
      comp. 'wheel2', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
      comp. 'wheel3', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
FMOD Playing channel: 4103
Driveline (RCar ctor); clutch: app=0.00, maxT=300.00, T=0.00
comp. 'engine', ratio 1.00 (cum. 7.95, 1/1.00), inertia 0.20 (effective 21.51)
  comp. 'gearbox', ratio 2.36 (cum. 7.95, 1/0.42), inertia 0.09 (effective 8.86)
    comp. 'differential', ratio 3.37 (cum. 3.37, 1/0.30), inertia 0.05 (effective 3.17)
      comp. 'wheel2', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
      comp. 'wheel3', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
FMOD Playing channel: 4104
Driveline (RCar ctor); clutch: app=0.00, maxT=300.00, T=0.00
comp. 'engine', ratio 1.00 (cum. 5.70, 1/1.00), inertia 0.20 (effective 11.93)
  comp. 'gearbox', ratio 1.69 (cum. 5.70, 1/0.59), inertia 0.07 (effective 5.44)
    comp. 'differential', ratio 3.37 (cum. 3.37, 1/0.30), inertia 0.05 (effective 3.17)
      comp. 'wheel2', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
      comp. 'wheel3', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
FMOD Playing channel: 4105
Driveline (RCar ctor); clutch: app=0.00, maxT=300.00, T=0.00
comp. 'engine', ratio 1.00 (cum. 4.35, 1/1.00), inertia 0.20 (effective 7.89)
  comp. 'gearbox', ratio 1.29 (cum. 4.35, 1/0.78), inertia 0.05 (effective 4.11)
    comp. 'differential', ratio 3.37 (cum. 3.37, 1/0.30), inertia 0.05 (effective 3.17)
      comp. 'wheel2', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
      comp. 'wheel3', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
FMOD Playing channel: 4106
Driveline (RCar ctor); clutch: app=0.00, maxT=300.00, T=0.00
comp. 'engine', ratio 1.00 (cum. 3.47, 1/1.00), inertia 0.20 (effective 6.06)
  comp. 'gearbox', ratio 1.03 (cum. 3.47, 1/0.97), inertia 0.04 (effective 3.65)
    comp. 'differential', ratio 3.37 (cum. 3.37, 1/0.30), inertia 0.05 (effective 3.17)
      comp. 'wheel2', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
      comp. 'wheel3', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
FMOD Playing channel: 4107
RTime:Stop()
RDriver::Update()
  Track present; write full name (carlswood_nt)
    'results.carlswoodnt.name'='Carlswood NT'
RTime:Start()
RAudio dtor
  producers=0, samples=0
RTrack dtor
DAABBTree:dtor, this=0x87079c8
RSplineRep:dtor (this=0x862a6b0)
RTime:Reset()
RAudio ctor
RAudio:Load(); enable=0
FMOD initializing
Disabling FSOUND output (NOSOUND)
RAudio:GetSample(data/audio/heli_inside.wav)
Setting sample loop
FMOD Playing channel: 0
rrSelectCar
cmdBut[0]
cmdBut[1]
cmdBut[2]
cmdBut[3]
RListBox dtor
Do()
REngine:Load(); engine mass=100.000000
fname_torque='torque.crv', maxTorque=180.00
RModel:Load; file 'body.dof' (buf=body.model.file)
Archive try 'body.dof' as data/cars/a110_03/body.dof
( 1.620, 0.830, 4.050 ) [Body indicated size]
( 1.554, 0.993, 3.875 ) [Body model-calc'ed size]
RModel:Load; file 'body.dof' (buf=body.model_incar.file)
Archive try 'body.dof' as data/cars/a110_03/body.dof
RModel:Load; file 'brakelights.dof' (buf=body.model_braking_l.file)
Archive try 'brakelights.dof' as data/cars/a110_03/brakelights.dof
RWing:Load(aero.wing0)
RModel:Load; file 'lwheel.dof' (buf=wheel0.model.file)
Archive try 'lwheel.dof' as data/cars/a110_03/lwheel.dof
RModel:Load; file 'rwheel.dof' (buf=wheel1.model.file)
Archive try 'rwheel.dof' as data/cars/a110_03/rwheel.dof
RModel:Load; file 'lwheel.dof' (buf=wheel2.model.file)
Archive try 'lwheel.dof' as data/cars/a110_03/lwheel.dof
RModel:Load; file 'rwheel.dof' (buf=wheel3.model.file)
Archive try 'rwheel.dof' as data/cars/a110_03/rwheel.dof
RModel:Load; file 'steer.dof' (buf=steer.model.file)
Archive try 'steer.dof' as data/cars/a110_03/steer.dof
declutch=300, clutch=300 (buf=engine.shifting.time_to_clutch)
RAudio:GetSample(data/cars/a110_03/engine.wav)
Setting sample loop
Setting sample loop
FMOD Playing channel: 1
RAudio:GetSample(data/cars/a110_03/skid.wav)
Setting sample loop
FMOD Playing channel: 2
RAudio:GetSample(data/audio/shift.wav)
Setting sample loop
Setting sample loop
RAudio:GetSample(data/audio/shift_miss.wav)
Setting sample loop
Setting sample loop
RAudio:GetSample(data/audio/starter.wav)
Setting sample loop
Setting sample loop
Driveline (RCar ctor); clutch: app=1.00, maxT=300.00, T=100.00
comp. 'engine', ratio 1.00 (cum. 12.17, 1/1.00), inertia 0.20 (effective 52.01)
  comp. 'gearbox', ratio 3.61 (cum. 12.17, 1/0.28), inertia 0.13 (effective 22.41)
    comp. 'differential', ratio 3.37 (cum. 3.37, 1/0.30), inertia 0.05 (effective 3.17)
      comp. 'wheel2', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
      comp. 'wheel3', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
RCar:CalcStaticProps(); m=728.000000
RRigid:SetMassInertia(728.000000)
RBody:DbgCheck(RCar:Load())
carHgt=0.466643
rrSelectTrk
cmdBut[0]
cmdBut[1]
cmdBut[2]
cmdBut[3]
TrkSelect(0)
LoadTrack: dirName=carlswood_nt
Do()
key=65363, QK_ESC=65307
key=65363, QK_ESC=65307
key=65363, QK_ESC=65307
key=65363, QK_ESC=65307
key=65363, QK_ESC=65307
key=65363, QK_ESC=65307
key=65363, QK_ESC=65307
key=65363, QK_ESC=65307
key=65363, QK_ESC=65307
key=65363, QK_ESC=65307
key=65363, QK_ESC=65307
key=65363, QK_ESC=65307
key=65363, QK_ESC=65307
key=65363, QK_ESC=65307
key=65293, QK_ESC=65307
selected trk 'carlswood_nt'
RListBox dtor
RMenuDestroy()
RMenu Destroy(); count=8
RMenuDestroy()
RSplineRep:ctor (this=0x9108ea0)
timeLines=6
RSplineRep:Reserve(339)
SplineRep: lines=339, curLine=339
RSplineRep:ctor (this=0x879f2a0)
Loading VRML track (0x879de00)
timeLines=6
RSplineRep:Reserve(339)
SplineRep: lines=339, curLine=339
  ReadTGA: 24-bit compressed
DTexturePool:FindAll(road*)
DAABBTree:BuildTree()
DAABBTree:BuildTree() DONE
RTrack dtor
RSplineRep:dtor (this=0x9108ea0)
RNetwork:ConnectToServer(); clients=0
RNetwork: waiting for connecting id...
>>>>>>>>>>>>>>> SetClientID 50
server: 127.0.0.1
client#1 (slave): 127.0.0.1
>>>>>>>>>>>>>>> GetClientID 50
RNetwork: succesfully connected to server.
RControls: indirection to 'mouse.ini'
RTime:Reset()
RTime:Start()
  ACCEPT car at gridPos 0
InNewCar: ownerClientID=50 (index 0)
REngine:Load(); engine mass=100.000000
fname_torque='torque.crv', maxTorque=180.00
RModel:Load; file 'body.dof' (buf=body.model.file)
Archive try 'body.dof' as data/cars/a110_03/body.dof
( 1.620, 0.830, 4.050 ) [Body indicated size]
( 1.554, 0.993, 3.875 ) [Body model-calc'ed size]
RModel:Load; file 'body.dof' (buf=body.model_incar.file)
Archive try 'body.dof' as data/cars/a110_03/body.dof
RModel:Load; file 'brakelights.dof' (buf=body.model_braking_l.file)
Archive try 'brakelights.dof' as data/cars/a110_03/brakelights.dof
RWing:Load(aero.wing0)
RModel:Load; file 'lwheel.dof' (buf=wheel0.model.file)
Archive try 'lwheel.dof' as data/cars/a110_03/lwheel.dof
RModel:Load; file 'rwheel.dof' (buf=wheel1.model.file)
Archive try 'rwheel.dof' as data/cars/a110_03/rwheel.dof
RModel:Load; file 'lwheel.dof' (buf=wheel2.model.file)
Archive try 'lwheel.dof' as data/cars/a110_03/lwheel.dof
RModel:Load; file 'rwheel.dof' (buf=wheel3.model.file)
Archive try 'rwheel.dof' as data/cars/a110_03/rwheel.dof
RModel:Load; file 'steer.dof' (buf=steer.model.file)
Archive try 'steer.dof' as data/cars/a110_03/steer.dof
declutch=300, clutch=300 (buf=engine.shifting.time_to_clutch)
RAudio:GetSample(data/cars/a110_03/engine.wav)
Setting sample loop
Setting sample loop
FMOD Playing channel: 1
RAudio:GetSample(data/cars/a110_03/skid.wav)
Setting sample loop
FMOD Playing channel: 2
RAudio:GetSample(data/audio/shift.wav)
Setting sample loop
Setting sample loop
RAudio:GetSample(data/audio/shift_miss.wav)
Setting sample loop
Setting sample loop
RAudio:GetSample(data/audio/starter.wav)
Setting sample loop
Setting sample loop
Driveline (RCar ctor); clutch: app=1.00, maxT=300.00, T=100.00
comp. 'engine', ratio 1.00 (cum. 12.17, 1/1.00), inertia 0.20 (effective 52.01)
  comp. 'gearbox', ratio 3.61 (cum. 12.17, 1/0.28), inertia 0.13 (effective 22.41)
    comp. 'differential', ratio 3.37 (cum. 3.37, 1/0.30), inertia 0.05 (effective 3.17)
      comp. 'wheel2', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
      comp. 'wheel3', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
RCar:CalcStaticProps(); m=728.000000
RRigid:SetMassInertia(728.000000)
RBody:DbgCheck(RCar:Load())
Type of car: owner=50, thisMachineID=50
( -34.545, 1.688, -115.958 ) [Warp from]
( -28.979, 1.688, -106.037 ) [Warp from]
( -5.567, -0.000, -9.921 ) [Warp axis]
 _                           _
|     -0.87    -0.00    -0.49 | Source matrix for quat
|      0.00     1.00    -0.00 |
|_     0.49    -0.00    -0.87_|
 _                           _
|     -0.87    -0.00    -0.49 | Result matrix from quat
|     -0.00     1.00    -0.00 |
|_     0.49    -0.00    -0.87_|
( -33.555, 2.288, -114.192 ) [vBodyPos plus warp offsetY]
Driveline (RCar ctor); clutch: app=0.00, maxT=300.00, T=0.63
comp. 'engine', ratio 1.00 (cum. 7.95, 1/1.00), inertia 0.20 (effective 21.51)
  comp. 'gearbox', ratio 2.36 (cum. 7.95, 1/0.42), inertia 0.09 (effective 8.86)
    comp. 'differential', ratio 3.37 (cum. 3.37, 1/0.30), inertia 0.05 (effective 3.17)
      comp. 'wheel2', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
      comp. 'wheel3', ratio 1.00 (cum. 1.00, 1/1.00), inertia 1.30 (effective 1.30)
FMOD Playing channel: 3
RTime:Stop()
RDriver::Update()
  Track present; write full name (carlswood_nt)
    'results.carlswoodnt.name'='Carlswood NT'
RTime:Start()
RAudio dtor
  producers=0, samples=0
RTrack dtor
DAABBTree:dtor, this=0x910a708
RSplineRep:dtor (this=0x879f2a0)
RTime:Reset()
RAudio ctor
RAudio:Load(); enable=0
FMOD initializing
Disabling FSOUND output (NOSOUND)
RAudio:GetSample(data/audio/heli_inside.wav)
Setting sample loop
FMOD Playing channel: 0
RMenuDestroy()
RMenu Destroy(); count=8
RAudio dtor
  producers=0, samples=0
QApp::Destroy()
QFont dtor
QFont dtor
QApp::Destroy()

```

PS:
Is there ay strategy game on Linux like AOE, WoW? i know about running them on wine, but i am asking of something meant to be for linux...

---

### Post by KIAaze on 2007-11-17
I never heard about racer before, so I don't know how it plays.

However, if you like racing games, you might enjoy [Torcs]("http://torcs.sourceforge.net/").
It even allows you to code your own AIs for the cars. :)

WoW=World of Warcraft? This isn't a strategy game, but an MMORPG. (unless you meant Warcraft ^^ )
I think there are several of those for GNU/Linux.
You might want to check out Neverwinter Nights (RPG), Planeshift, EVE online, Vendetta, etc

As for strategy games:
-Battle for Wesnoth
-Globulation 2
-Liquidwars
-Dark Oberon
-Glest
-BOS wars
-Boson
-TA3D
-TA Spring
-...

I'm tired of listing the same over and over again, so go here as a good starting point:
[http://linux.strangegamer.com/index.php?title=Linux_Gaming_Sites]("http://linux.strangegamer.com/index.php?title=Linux_Gaming_Sites")

And apart from Wine, some people forget about all the good games for DOS. Use DOSbox to play them.
Programs like ZSNES, PSX, SCUMMVM, AGS (Adventure Game Studio) also make for a lot of available games...

---

