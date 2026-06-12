---
title: "problems after updating ubuntu"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by iiDopDop!! on 2007-07-17
Wont work after installing updates 

--------------------------------------------------------------------------------

I can install ubuntu get it working fine, and install the updates then it said i need to reboot but then started some more straigth away.
then i turned it off after the second lot of updates where done.

but the problem comes in when i reboot and try to start ubuntu again.
it says Kernel Modules arent working in its test thingy example...

Hardware [OK]
Kernel modules 
Something Else [OK]

then it says error program apt-get is currently un-installed please type sudo apt-get install apt-get to install then i type that in and get the same message probably because im trying to install something with something i dont have how can i fix this??

plus our internets capped from 8meg down to like 128kb down so it takes 8 hours just to get the updates so i dont wanna go gettin the updates again.

---

### Post by confused57 on 2007-07-17
> then it says error program apt-get is currently un-installed please type sudo apt-get install apt-get to install then i type that in and get the same message probably because im trying to install something with something i dont have how can i fix this??

Good point...I don't know what may have caused this, but you could try:
```
sudo aptitude install apt-get
```

Probably won't work, but worth trying.

Added:  Have you tried?:
```
sudo apt-get update
sudo apt-get upgrade
```

If the above doesn't work:
```
sudo apt-get -f install
```
this "may" repair any broken dependencies

---

### Post by Unstable Element on 2007-07-17
I had the same problem, 
aptitude uninstalled all packages, including, apt-get, aptitude, kernel-sources, kernel-image, etc. And installed 2 packages I needed..

This was the end of our Ubuntu server, won't start won't let us get to our data no nothing.. A solution would be very much appreciated

---

### Post by iiDopDop!! on 2007-07-19
i tried these and it didnt work

sudo aptitude install apt-get
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install

i think its something wrong with the kernel because when i go through the grub to pick ubuntu it has 5 options ones memory test. then theres2 different kernels tand 2 recovery modes but they all go to the same sorta problem page thingy and my dad just bought a new vista system so this computer im trying to fix is mine now but i gotts share it with my sisters coz they like the games that are on ubuntu

---

### Post by meierfra on 2007-07-19
Maybe there is a way to undo what you did. But I don't know.

apt-get is just a front-end for "dpkg". If  "dpkg" did not get uninstalled,  you can  reinstall apt-get as follows:

download  apt.deb from [http://packages.debian.org/stable/admin/apt]("http://packages.debian.org/stable/admin/apt")

Right-click the file to install it. (If this does not work, let me know)

It might complain about missing files or unmet dependencies. But you should be able to find all the missing fiiles through the above link.

---

### Post by az on 2007-07-19
There is no "apt-get" package, the package is named "apt".

But anyway, the problem, is that one of your smarty-pants package manager uninstalled a bunch of packages that you need.  That is not supposed to happen.

I doubt that you are getting a message that says that you are missing the "apt-get" package.


To fix, run:

sudo apt-get -f install

and then

sudo apt-get install ubuntu-desktop


If you have problems, post the output of what you get when you run those.

---

### Post by meierfra on 2007-07-19
Before you try my earlier suggestion, try

sudo aptitude install apt

---

### Post by confused57 on 2007-07-19
> **iiDopDop!! said:**
> i tried these and it didnt work

sudo aptitude install apt-get
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install

i think its something wrong with the kernel because when i go through the grub to pick ubuntu it has 5 options ones memory test. then theres2 different kernels tand 2 recovery modes but they all go to the same sorta problem page thingy and my dad just bought a new vista system so this computer im trying to fix is mine now but i gotts share it with my sisters coz they like the games that are on ubuntu
   I think it is a inaccurate error message, because of a recent experience that I had.  I installed Mandriva on a partition that I had Sabayon installed on...when I booted into Gutsy, I received the same error message and ended up with a root prompt.   The problem was that the UUID had changed on the partition that previously had Sabayon & was being mounted in Gutsy...what I did was accessed Gutsy's /etc/fstab & commented out the fstab entry for this partition, pressed "Esc" and Gutsy booted into a GUI.
  What I'm guessing is that possibly with a kernel update, your Window's partition that is mounted at boot may have changed from /dev/sda? to /dev/hda?, or vice-versa...none of your UUID's should have changed with just a normal update of your system, so this is my best guesstimate.
  If you're dropped to a root prompt when you boot Ubuntu, you might try either commenting out(place a # in front of) the Window's entry for now or change the sda/hda designation.  If you want to try this and you get a root prompt, enter:
```
cp /etc/fstab /etc/fstab_backup
nano /etc/fstab
```
make the changes, then...ctrl+x, y, enter...to save.

May not be your problem, but thought I'd share how I "fixed" this error in Gutsy...good luck.

Added:  Thanks az, you're right...think I was suffering from a case of temporary magnesia.

---

