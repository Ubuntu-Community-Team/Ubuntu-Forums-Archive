---
title: "Live cd wont boot ubuntu"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by Forgoten Dynasty on 2008-04-11
OOK so ive changed my bios to boot from the disk

works fine..

i click start or install ubuntu at the main menu

the pipe fills all the way 

then it brings me to what looks like terminal (just a black screen and a flashing line where i can type)

then the line stops flashing

my screen spazes for a second

the goes blank 

and by blank i mean absolutly nothing cus my screen turns off and says no input
___________________________
im using 6.06 for Intel
the computer im installing it on is a old dell dimension 4100

PS. i know the disk works cus i put it in my good computer and i booted fine

computer specs:
256 ram
intel pentenium III
40 gig HDD with 36.4 gigs remaining
windows XP professional (i want to dual boot with GRUB)

---

### Post by Crafty Kisses on 2008-04-11
At the black screen type the following, see what happens:
```
startx
```

---

### Post by JoshuaRL on 2008-04-11
I think that the problem is that you don't have enough RAM to load the Live CD.  Try downloading the Alternate CD and installing using that.  Right under the Download button on the download page is the checkbox to make it an Alternate CD.

The Alternate CD is text-based install but will work just fine.

---

### Post by Crafty Kisses on 2008-04-11
> **JoshuaRL said:**
> I think that the problem is that you don't have enough RAM to load the Live CD.  Try downloading the Alternate CD and installing using that.  Right under the Download button on the download page is the checkbox to make it an Alternate CD.

The Alternate CD is text-based install but will work just fine.

Yeah, or you might want to look into Xubuntu. :)

---

### Post by Forgoten Dynasty on 2008-04-11
thanks ill try start first then if that doesnt work ill move to the installer disk

and if that doesnt work ill move to Xubuntu

BTW thanks alot for your quick replys


EDIT: startx didn't work does anybody have a link to the text based one?

---

### Post by Forgoten Dynasty on 2008-04-12
:/ i tried the text based every thing installed perfect i even have the grub boot loader
my windows launches
ubuntu launches but does the exact same thing 
the bar fills then the screen goes black
if i push the power button (on the tower) it pops  up for a second then the computer turns off
im gunna try Xubuntu but how do i go about deleting everything that installed

---

### Post by joshrobinson on 2008-04-12
try booting into recovery mode, at the grub menu hit the esc button, and go to recovery mode, when it asks if you want to boot normal or drop to root shell, go to the drop to root shell option

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
try running this command, and when its done type
exit
then go to the boot normally option

---

### Post by JoshuaRL on 2008-04-12
Yeah, what joshrobinson said.  And do you know what type of video card you have?  It seems like that's the problem, and that's why he has you doing that command.  It will reconfigure Xorg, the Graphical User Interface (desktop we're all used to using).  One thing though, this is the correct command:
```

dpkg-reconfigure -phigh xserver-xorg

```
You won't need "sudo" in Recovery mode since you are logged in as root.  And after you finish you can try:
```

shutdown now

```

---

### Post by joshrobinson on 2008-04-12
> **JoshuaRL said:**
> Yeah, what joshrobinson said.  And do you know what type of video card you have?  It seems like that's the problem, and that's why he has you doing that command.  It will reconfigure Xorg, the Graphical User Interface (desktop we're all used to using).  One thing though, this is the correct command:
```

dpkg-reconfigure -phigh xserver-xorg

```
You won't need "sudo" in Recovery mode since you are logged in as root.  And after you finish you can try:
```

shutdown now

```

yeah i chose to leave the sudo on there, as to not confuse new users who are trying to run that command outside of recovery mode, or if the op got into gui terminal, or tty and ran it
the sudo wont hurt anything while in a root terminal

---

### Post by famous3warriors on 2008-04-12
I apologize for the rude interruption but I am having  the same problem I did exactly what you had said to do and this is the error I am getting.  xserver-org is not installed.  Does that mean I have to do a reinstall.?

---

### Post by joshrobinson on 2008-04-12
> **famous3warriors said:**
> I apologize for the rude interruption but I am having  the same problem I did exactly what you had said to do and this is the error I am getting.  xserver-org is not installed.  Does that mean I have to do a reinstall.?
its xserver-xorg not xserver-org did you do the wrong spelling in the command?

---

### Post by famous3warriors on 2008-04-12
I sure did thanks for the advice hopefully it works

---

### Post by Forgoten Dynasty on 2008-04-12
ok in windows i went to dxdiag and it says 
Name S3 Trio32/64
Manufacture: NA
and then every thing is just NA after thta

and grub doesnt go into recovery mode do you mean boot ubuntu in recovery mode because...

it says root@(router name):~#

(router name =my router name)

do i type the command there?

edit ok ive tried installing Xubuntu but i have the exact same problem
if no one can figure this out ill just rip my HDD out and put it in my new computer and install it on that HDD

---

