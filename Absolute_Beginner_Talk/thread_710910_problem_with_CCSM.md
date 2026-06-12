---
title: "problem with CCSM"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by rimi on 2008-02-29
Hi Everybody,
                    I am new to ubuntu. I tried to play with advanced desktop setting by installing compiz fusion. First time it worked fine I can enable different desktop option and activate those. But after I reboot the PC although I can enable different option of advanced desktop settings but those option are not getting activated. Can any one please help me to overcome the problem. I am really hooked up with cool features of CCSM. 

Thanks in advance
Rimi

---

### Post by oedha on 2008-02-29
have you change your visual effect to custom ?
(right click desktop - change desktop background - visual efect)

---

### Post by rimi on 2008-02-29
Thanks for the reply Oedha. I tried to change  the visual effect to custom. But I can not do it this time. It says desktop effects can not be enabled. Have I messed up anything?
regards

---

### Post by oedha on 2008-02-29
what is your display card......this is the problem ?
open terminal, type :==> sudo lshw -short -C display

---

### Post by rimi on 2008-02-29
The display Card is Radeon RV250 [Mobility FireGL 9000

---

### Post by rimi on 2008-02-29
By typing compiz at command prompt gives the following information

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 02) (prog-if 00 [VGA])
        Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 32, IRQ 11
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

---

### Post by oedha on 2008-02-29
ups...ATI.....
i have no experience yet :(
but ......on some post..it said
you have to install xserver-xgl.......sorry...maybe others can help you

edit : what about this :==> [http://ubuntuforums.org/showthread.php?t=462823&highlight=Radeon+RV250](http://ubuntuforums.org/showthread.php?t=462823&highlight=Radeon+RV250)

---

### Post by rimi on 2008-02-29
Thank you a lot. Your link works. I can play with CCSM.

---

### Post by oedha on 2008-02-29
really.....:)

---

