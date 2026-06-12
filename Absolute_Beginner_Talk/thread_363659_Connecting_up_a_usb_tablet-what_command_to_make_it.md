---
title: "Connecting up a usb tablet-what command to make it run?"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-02-17
Hi noticed that under system>preferences>removable drives and media preferences>mutltimedia that i can connect a usb tablet that i have but it needs a command to run it. can anyone help?

---

### Post by mcduck on 2007-02-17
That option is for if you want to run something automatically when a tablet is connected, for example to autostart Gimp when you plug in the tablet.

---

### Post by rapattack1 on 2007-02-17
ah so i have to configure it first? do you know how i can get ubuntu to recognise this tablet?

---

### Post by mcduck on 2007-02-17
Weelll, depends on what tablet it is ;)

For Wacom tablets you could try this one (it worked for my Intuos3): [http://www.ubuntuforums.org/showthread.php?t=25151&highlight=wacom]("http://www.ubuntuforums.org/showthread.php?t=25151&highlight=wacom")

---

### Post by rapattack1 on 2007-02-17
i can't seem to find any references to my tablet on the net to do with linux. it is mglogic epad ju-0605

---

### Post by rapattack1 on 2007-02-17
interesting page. unfortunately i am stuck at number 3 on it as i don't know what that step means. do they want me to open something else or put in a command i dunno?

---

### Post by mcduck on 2007-02-17
> **rapattack1 said:**
> interesting page. unfortunately i am stuck at number 3 on it as i don't know what that step means. do they want me to open something else or put in a command i dunno?

The step 3 is about configuring settings for X. Press alt-F2 and run 'gksudo gedit /etc/X11/xorg.conf' to open the configuration file for editing.

---

### Post by rapattack1 on 2007-02-17
ok i got to configuring in the gimp but the gimp doesn't see there is a tablet. device manager does though ....anyway will try again tomorrow.

---

### Post by mcduck on 2007-02-17
> **rapattack1 said:**
> ok i got to configuring in the gimp but the gimp doesn't see there is a tablet. device manager does though ....anyway will try again tomorrow.

One thing I've noticed is that the tablet has to be plugged in when starting the computer. Also, Wacom doesn't work with XGL..

---

### Post by rapattack1 on 2007-02-18
Ah ok. I have had it plugged in before booting anyway. i dunno but mine is not the wacom brand. what is xgl?

---

### Post by mcduck on 2007-02-18
I have absolutely no idea about any other than Wacom tablets..

XGL (or AIGLX) are related to running Beryl or Compiz window managers. If you don't know what it is then I'm sure you aren't running it :)

---

### Post by rapattack1 on 2007-02-19
it is a MGlogic Epad. that is all i know. i have only ever seen one of these devices once and that was years ago. this was given to me by a friend that has winxp and she was told it would not work in that os. she had previously used it with win98. the only info i saw on the net was in another language and my friend had paperwork/drive cd but she threw them out.

---

### Post by rapattack1 on 2007-02-22
i had a look in device manager and it says that the tablet is a 'j-series'. i haven't been able to see anything via google that makes sense to me so if anyone can shed light on this i would appreciate it.

---

