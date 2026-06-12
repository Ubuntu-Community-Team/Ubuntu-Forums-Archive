---
title: "Auto update"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by techmech0 on 2007-11-23
Good evening, I am an absolute beginner to Ubuntu having first tested the water with Ubuntu via Wubi.
I liked what I saw and used, so went ahead with a complete reformat and a fresh download of Gutsy.
The automatic update procedure has run several times and has completed the suggested updates without problem, however the most recent update concerned with" compiz" will not complete and I have a message on screen which says" E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Also the second message ' E:_cache->open()failed, please report.'
Could anyone please help.
I am a moderate Windows user but am only just starting to get to grips with Ubuntu.
I am very impressed so far and am anxious to gain experience, I have found the user guide in the beginners forum and will be digesting this as fast as I can.
Many thanks for any help.
techmech0.

---

### Post by taurus on 2007-11-23
Close that window.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by mikewhatever on 2007-11-23
Close all open windows but your desktop, go to Applications>Accessories>Terminal, enter the command > sudo dpkg --configure -a

You'll be asked for the password. Type it in and hit enter.

---

### Post by overdrank on 2007-11-23
> **techmech0 said:**
> Good evening, I am an absolute beginner to Ubuntu having first tested the water with Ubuntu via Wubi.
I liked what I saw and used, so went ahead with a complete reformat and a fresh download of Gutsy.
The automatic update procedure has run several times and has completed the suggested updates without problem, however the most recent update concerned with" compiz" will not complete and I have a message on screen which says" E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Also the second message ' E:_cache->open()failed, please report.'
Could anyone please help.
I am a moderate Windows user but am only just starting to get to grips with Ubuntu.
I am very impressed so far and am anxious to gain experience, I have found the user guide in the beginners forum and will be digesting this as fast as I can.
Many thanks for any help.
techmech0.

HI and welcome, in the terminal use this command ```
sudo dpkg --configure -a
``` the terminal is located under applications, accessories.

Edit to slow

---

### Post by davidc502 on 2007-11-23
I'd go ahead and run 'dpkg --configure -a' to see if that clears up the problem.

You will do this in a command line environment. Go to Applications, system-tools, and select konsole. Copy and paste  'dpkg --configure -a' and hit enter.

---

### Post by taurus on 2007-11-23
> **davidc502 said:**
> I'd go ahead and run 'dpkg --configure -a' to see if that clears up the problem.

You will do this in a command line environment. Go to Applications, system-tools, and select konsole. Copy and paste  'dpkg --configure -a' and hit enter.

Then you will get an error message because you are NOT root!  You need to include **sudo** in front of that command.

---

### Post by techmech0 on 2007-11-23
Many thanks to all for the replies received, have run the sudo commands in terminal and resolved the problem.
Thanks once again.
techmech0

---

