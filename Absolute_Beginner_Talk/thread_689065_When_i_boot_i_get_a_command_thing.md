---
title: "When i boot i get a command thing?"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by SuperT on 2008-02-06
I just installed ubuntu but every time i boot is comes up with a thing saying "This program comes with no warrenty......." then it says "to run a command as adminsitrator (user "root"), use sudo command........." then it says ubuntu@ubuntu: where i can type a command. What do i do here or how do i fix this?

---

### Post by NightwishFan on 2008-02-06
What method did you use to install Ubuntu?

---

### Post by SuperT on 2008-02-06
I burnt the iso file to a cd and booted it on a formated hard drive. Is this what you mean?

---

### Post by oedha on 2008-02-06
how did you install it ?
what happen if you type startx

---

### Post by NightwishFan on 2008-02-06
I meant was it the live cd or an alternate text based installer. If you have it installed your user should be what you selected, and not ubuntu@ubuntu. Also make sure you do not have the live cd in the drive.

---

### Post by SuperT on 2008-02-06
It says "fatal error: Server already active for display"

---

### Post by oedha on 2008-02-06
what if ctrl+alt+F7
can you jump to desktop ?
or type init 5

---

### Post by SuperT on 2008-02-06
I tryed alt+ctrl+f7 and it did nothing. When i tryed init5 it says 

> "Fatal Server Error:
Server is already active for display 0

If this server is no longer running, remove /tmp/.xo-lock
and start again"

---

### Post by oedha on 2008-02-06
hmmm.......
sudo dpkg-reconfigure -phigh xserver-xorg
then sudo /etc/init.d/gdm restart

btw...what is your display card ? see it by lshw -short -class display

---

### Post by SuperT on 2008-02-06
> **oedha said:**
> 
btw...what is your display card ? see it by lshw -short -class display
It is a 
> 82845g/gl [Brookdale-G]/GE chipset intergrated

---

### Post by Trail on 2008-02-06
Did you install the desktop or server variant by the way?

---

### Post by SuperT on 2008-02-06
I am still having no luck with this. I have tryed everything above and have been searching the net for solutions. Many places say to delete the /tmp/.xo-lock file but when i do this it says file dose not exist?

---

### Post by SuperT on 2008-02-06
> **Trail said:**
> Did you install the desktop or server variant by the way?
The desktop.

---

### Post by SuperT on 2008-02-06
Am i less likley to have these problems with kubuntu? Because i am about to give up and people say kubuntu is better for beginners.

Ps. It asks me for my username and password so i enter it but then it dosnt prompt me to do anything else. Am i suppos to do something?

---

