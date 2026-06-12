---
title: "[SOLVED] no sound"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by 1scorpio on 2008-02-18
:( hi all i am having a truly bad time setting up my sound system i have sound blaster audigy platinum pro with a sound drive. i don't get any sound at all. Please help tia

---

### Post by Hobo Joe on 2008-02-18
Paste the output of:
```

sudo asoundconf list

```
(I can't count how many times I've said that tonight alone! :p)

---

### Post by 1scorpio on 2008-02-20
thanks Joe but as a new user of linux I wouldn't know where to paste it more instruction please tia 1scorpio
:???:

---

### Post by northern lights on 2008-02-20
You are asked to run the above command in your terminal and paste the output (from the terminal) here (into this thread)...

---

### Post by 1scorpio on 2008-02-21
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
Audigy2
I82801DBICH4

is this what I needed to do? 
thanks northern lights

---

### Post by deadgobby on 2008-02-21
Lets go the easy route of things. That is being the KISS method. Go into your BIOS and disable the on board sound device. Once that is disable and you boot up your system. You should hear the start up theme through your speakers or head phones. If there is no sound then open up the terminal and either copy and paste this command.
$ aplay --list-devices 
 Please post the reply here
Gobby

---

### Post by northern lights on 2008-02-21
You have two sound devices: your Sound Blaster Audigy2 (which ought to working fine with the latest Ubuntu) and an Intel onboard sound chip (I82801DBICH4).
Does neither put out any signal?
It might just be that the wrong device is set as default. Check "System > Preferences > Sound" and under the "Devices" tab manually select your card. You can also disable the onboard device in the BIOS upon bootup.

[EDIT] - late -[/EDIT]

---

### Post by superprash2003 on 2008-02-21
yes, choose the device manually.. i had the same problem CS46XX worked for me!!

---

### Post by 1scorpio on 2008-02-21
:popcorn::) Man All of you are great sooooooooooo simple

many many thanks to all

---

