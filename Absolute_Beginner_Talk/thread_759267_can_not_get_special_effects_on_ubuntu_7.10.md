---
title: "can not get special effects on ubuntu 7.10"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by garrettstarnes on 2008-04-18
Ok guys

i am running ubuntu 7.10 with an ati radeon x1400 graphics card.  i cant enable any of the desktop effects.  i keep getting this message 'The Composite extension is not available'.  I installed compiz something or other.  i am new to all of this, and am not familiar with the terminal.  my desktop effects look like something that came off of the old apples when i was in elementary school.  was just hoping someone could help me.

thanks!

---

### Post by kauboy on 2008-04-18
i joined this forum just now and am having trouble findig out "HOW TO INITIATE A THREAD!!!", dunno how to post my query, sounds dumb, but do help me out as i have no other way of asking this question, very sorry ... :(

---

### Post by garrettstarnes on 2008-04-18
go to [www.ubuntuforums.org](www.ubuntuforums.org).  Click on 'absolute beginner talk', then click on 'make new post'.  After that, you have to type your title in the little box, and your 'thread' in the larger one.  That should do it!

---

### Post by kauboy on 2008-04-18
make that ten times!!

---

### Post by LeoSolaris on 2008-04-18
for the original poster...

You will have to install the restricted device driver for your graphics card. Graphics card drivers are proprietary closed source drivers, and therefore it is entirely up to you to install them, and Ubuntu's devs make no guarantees that they work.

System->Administration->Restricted Drivers Manager and enable it. You will have to reboot to make it take effect, and it should ask you to.

Apparently ATI Drivers are not really very good, but I have heard that they have improved. I don't use ATI myself, so I don't have direct experience.

Leo

---

### Post by joshrobinson on 2008-04-18
if you have already installed your video drivers from the restricted drivers menu, run the following command
```
fglrxinfo
```

and post the output

---

### Post by garrettstarnes on 2008-04-19
user@StarnesFamilyLaptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7412 Release


and by the way, i just upgraded to version 8.04

---

### Post by joshrobinson on 2008-04-19
```
sudo apt-get install xserver-xgl
```
hold down ctrl+alt and hit backspave, login again, then try to enable the effects

---

### Post by SunnyRabbiera on 2008-04-19
> **garrettstarnes said:**
> user@StarnesFamilyLaptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7412 Release


and by the way, i just upgraded to version 8.04

just remember that hardy is still in the beta/Release canidate phases so expect some issues.

---

### Post by garrettstarnes on 2008-04-19
same thing.  i get a 'The Composite extension is not available' message.

---

### Post by joshrobinson on 2008-04-19
> **garrettstarnes said:**
> same thing.  i get a 'The Composite extension is not available' message.

ok back up your xorg.conf

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

```
sudo gedit /etc/X11/xorg.conf
```

add this at the bottom
```
Section "Extensions"
    Option "Composite" "Enable"
EndSection

```

save and close, then restart your computer

if you have problems, and you cant get into ubuntu, do the following
llogin to recovery mode when it says press esc to enter grub menu, and you can use
```
nano /etc/X11/xorg.conf
``` to remove those lines
cntrl+o to save, hit enter, then ctrl+x to quit, and reboot

---

### Post by garrettstarnes on 2008-04-19
I tried to do those commands, but i think i'm too dumb.  I got a message that said command not found.

---

### Post by garrettstarnes on 2008-04-19
everyone says that when they install ubuntu, that everything just works.  Did I do something wrong?

---

### Post by garrettstarnes on 2008-04-19
I think everybody dropped me.  If anyone out there could walk me through some of this, i would appreciate it.  I am willing to use the command line, i just don't know anything about it.
thanx

---

