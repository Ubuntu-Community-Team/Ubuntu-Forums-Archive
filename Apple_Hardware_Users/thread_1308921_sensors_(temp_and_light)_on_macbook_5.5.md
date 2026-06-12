---
title: "sensors (temp and light) on macbook 5.5"
date: 2009-11-01
forum: Apple Hardware Users
---

### Post by cyphaw on 2009-11-01
Hello,

I have Ubuntu installed on a macbookpro 5.5, and I wanted to monitor it, so I installed lm-sensors, sensors-applet and load the coretemp and applesmc modules and here is what I get when I run "sensors":

```
applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :  2501 RPM  (min = 2500 RPM)
temp1:       +36.0°C                                    
temp2:       +36.0°C                                    
temp3:       +35.2°C                                    
temp4:       +38.8°C                                    
temp5:       +61.0°C                                    
ERROR: Can't get value of subfeature temp6_input: I/O error
temp6:        +0.0°C                                    
temp7:       +55.0°C                                    
ERROR: Can't get value of subfeature temp8_input: I/O error
temp8:        +0.0°C                                    
ERROR: Can't get value of subfeature temp9_input: I/O error
temp9:        +0.0°C                                    
ERROR: Can't get value of subfeature temp10_input: I/O error
temp10:       +0.0°C                                    
ERROR: Can't get value of subfeature temp11_input: I/O error
temp11:       +0.0°C                                    
ERROR: Can't get value of subfeature temp12_input: I/O error
temp12:       +0.0°C                                    
ERROR: Can't get value of subfeature temp13_input: I/O error
temp13:       +0.0°C                                    
temp14:      +59.8°C                                    
temp15:      +53.2°C                                    
temp16:       +0.0°C                                    
ERROR: Can't get value of subfeature temp17_input: I/O error
temp17:       +0.0°C                                    
ERROR: Can't get value of subfeature temp18_input: I/O error
temp18:       +0.0°C                                    
temp19:      +33.8°C                                    
temp20:      +43.2°C                                    

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +56.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +56.0°C  (high = +100.0°C, crit = +100.0°C)
```

Well, that's great, I know the temp of each core, the fan speed and I know that temp5 is the graphic card (according to sensors-applet and the nvidia control pannel), that's the most important.

But what about the others ? Someone know what they are ? Someone have the same errors as me ?


Now about the light sensor : I heard that it may works, but could not find information on it.
And finally, the motion sensors : it works out of the box (you can try it with the game neverball : launch it and grab your mac to play (need the applesmc module to be loaded)). Any idea of how to use it and for what (I heard about switch to others workspaces) ?


Thanks.

cyphaw

---

### Post by karunadheera on 2010-01-27
I also installed Karmic on my MBP 5,4. I'm also getting same I/O errors for some sensors. But i see your temperatures are higher than mine.

My MBP was also earlier working on higher temperature earlier compared to OSX. I followed this tutorial and tweaked it. Im coool now :p.

[http://ubuntuforums.org/showthread.php?t=1215928&highlight=Macbook+Pro]("http://ubuntuforums.org/showthread.php?t=1215928&highlight=Macbook+Pro")

applesmc-isa-0300
Adapter: ISA adapter
Left side  :2461 RPM  (min = 2000 RPM)
temp1:       +26.5°C                                    
temp2:       +26.5°C                                    
temp3:       +26.0°C                                    
temp4:        +0.0°C                                    
temp5:       +35.5°C                                    
temp6:       +32.5°C                                    
temp7:       +33.0°C                                    
ERROR: Can't get value of subfeature temp8_input: I/O error
temp8:        +0.0°C                                    
ERROR: Can't get value of subfeature temp9_input: I/O error
temp9:        +0.0°C                                    
ERROR: Can't get value of subfeature temp10_input: I/O error
temp10:       +0.0°C                                    
ERROR: Can't get value of subfeature temp11_input: I/O error
temp11:       +0.0°C                                    
ERROR: Can't get value of subfeature temp12_input: I/O error
temp12:       +0.0°C                                    
ERROR: Can't get value of subfeature temp13_input: I/O error
temp13:       +0.0°C                                    
temp14:      +36.5°C                                    
temp15:      +33.8°C                                    
temp16:      +49.0°C                                    
temp17:      +30.2°C                                    
ERROR: Can't get value of subfeature temp18_input: I/O error
temp18:       +0.0°C                                    
temp19:      +25.2°C                                    
temp20:      +30.2°C   




> **cyphaw said:**
> Hello,

I have Ubuntu installed on a macbookpro 5.5, and I wanted to monitor it, so I installed lm-sensors, sensors-applet and load the coretemp and applesmc modules and here is what I get when I run "sensors":

```
applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :  2501 RPM  (min = 2500 RPM)
temp1:       +36.0°C                                    
temp2:       +36.0°C                                    
temp3:       +35.2°C                                    
temp4:       +38.8°C                                    
temp5:       +61.0°C                                    
ERROR: Can't get value of subfeature temp6_input: I/O error
temp6:        +0.0°C                                    
temp7:       +55.0°C                                    
ERROR: Can't get value of subfeature temp8_input: I/O error
temp8:        +0.0°C                                    
ERROR: Can't get value of subfeature temp9_input: I/O error
temp9:        +0.0°C                                    
ERROR: Can't get value of subfeature temp10_input: I/O error
temp10:       +0.0°C                                    
ERROR: Can't get value of subfeature temp11_input: I/O error
temp11:       +0.0°C                                    
ERROR: Can't get value of subfeature temp12_input: I/O error
temp12:       +0.0°C                                    
ERROR: Can't get value of subfeature temp13_input: I/O error
temp13:       +0.0°C                                    
temp14:      +59.8°C                                    
temp15:      +53.2°C                                    
temp16:       +0.0°C                                    
ERROR: Can't get value of subfeature temp17_input: I/O error
temp17:       +0.0°C                                    
ERROR: Can't get value of subfeature temp18_input: I/O error
temp18:       +0.0°C                                    
temp19:      +33.8°C                                    
temp20:      +43.2°C                                    

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +56.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +56.0°C  (high = +100.0°C, crit = +100.0°C)
```

Well, that's great, I know the temp of each core, the fan speed and I know that temp5 is the graphic card (according to sensors-applet and the nvidia control pannel), that's the most important.

But what about the others ? Someone know what they are ? Someone have the same errors as me ?


Now about the light sensor : I heard that it may works, but could not find information on it.
And finally, the motion sensors : it works out of the box (you can try it with the game neverball : launch it and grab your mac to play (need the applesmc module to be loaded)). Any idea of how to use it and for what (I heard about switch to others workspaces) ?


Thanks.

cyphaw

---

### Post by dennis123123 on 2010-01-28
> **cyphaw said:**
> 
Now about the light sensor : I heard that it may works, but could not find information on it.


```
cat /sys/devices/platform/applesmc.768/light 
```

returns something like (1,0) for fully dark; and (255,0) for ultra bright.
shine a torch / cover with your hand the sensor (it is next to the iSight webcam in the screen) and try it!

---

### Post by cyphaw on 2010-03-20
I just saw your answers, thanks fr them.

@karunadheera: I still have two more errors than you, I'll try to check with a friend who has the same macbook but Arch Linux.
And yes, your temperatures are way lower than mine, I'll try the tuto you mentioned. By the way, my cores are usually at 52°C and the graphic card at 60°C (and rise easily to 85 (cores and graphics) when playing games), while the minimal fan speed is 2500 rpm.

By the way, that is strange too: my fan never stops. I manually set the min speed at 2500 with
```
echo 2500 | sudo tee /sys/devices/platform/applesmc.768/fan1_min
```but even without, the minimal fan speed was 2000 rpm, is it the same on yours?

@dennis123123: Yes I saw this, and you can get the position by cating "position", in the same folder as light. Hpwever, I didn't fully understand yet what means what in the output. I think we can do some fun things with that.

---

