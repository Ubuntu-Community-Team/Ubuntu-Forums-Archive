---
title: "can't get games to play right"
date: 2010-03-02
forum: Apple Hardware Users
---

### Post by jazzlukejosh on 2010-03-02
I'm running linux on an old iMac G3 power pc. I've just loaded a couple of games for my daughter but the music is staticky and the cursor flickers and goes invisible. Is there anyway to increase virtual memory or something that will make these game work??
I know the hardware is old but one of the few(only thing) things it did well with the old OSX system was play games, so I know its not the hardware.
 
Please I'd love to get this thing going right

---

### Post by gradinaruvasile on 2010-03-02
If you are using Ubuntu 9.04 - 9.10 the sound problem is most likely related to the PulseAudio server - disabling/removing it should solve the problem.

[http://n2.nabble.com/How-to-disable-PulseAudio-on-Ubuntu-9-10-a-secret-method-td3962312.html](http://n2.nabble.com/How-to-disable-PulseAudio-on-Ubuntu-9-10-a-secret-method-td3962312.html)

I only saw cursor flickering on ati cards with 3d rendered games. But im am not familiar with ppc's.

Which games did you play?

---

### Post by jazzlukejosh on 2010-03-02
So far I've only tried, Extreme tux racer and Pingus
I'm trying to create a swap file because I think its a memory thing. I'm made an ammendment in the  /etc/fstab file but I don't know how to save the change.
Appriciate any advice

---

### Post by linuxopjemac on 2010-03-02
swap you should have in a partition dedicated to that as far as I am concerned.

I give you my setup, it will help you understand...
Code:

sudo mac-fdisk /dev/hda

```

Command (? for help): p   
/dev/hda
        #                    type name                 length   base     ( size )  system
/dev/hda1     Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled               1954 @ 64       (977.0k)  NewWorld bootblock
/dev/hda3         Apple_UNIX_SVR2 untitled           37345704 @ 2018     ( 17.8G)  Linux native
/dev/hda4         Apple_UNIX_SVR2 swap                1722358 @ 37347722 (841.0M)  Linux swap

Block size=512, Number of Blocks=39070080
DeviceType=0x0, DeviceId=0x0
```

---

