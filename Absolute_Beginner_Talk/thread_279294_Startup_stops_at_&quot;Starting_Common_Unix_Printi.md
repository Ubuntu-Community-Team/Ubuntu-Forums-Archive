---
title: "Startup stops at: &quot;Starting Common Unix Printing System: cupsd&quot;"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by catbeef on 2006-10-17
I just installed Ubuntu and when it is booting up it stops at Starting Common Unix Printing System: cupsd

Recovery mode does the same thing.

I am running an Athlon 64 x2 in an Asus A8N-SLi.

---

### Post by catbeef on 2006-10-17
BUUUUUUUUUUUUUUUM

p

---

### Post by KaLiF101 on 2008-01-21
I got the same problem like you but i am using a p4 300 512ram

---

### Post by notascoolasu on 2008-02-03
i have same problem, anyone get up and running yet after this problem?

---

### Post by LookTJ on 2008-02-03
If you managed to get the live cd up and running, you could mount your partition and try to rename the cupsd file.

Create a folder:
```
sudo mkdir /media/ubuntupart
```Find your Linux/Ext3 partition
```
sudo fdisk -l
```Mount your partition
```
sudo mount  sudo mount -t ext3 /dev/hdXX /media/ubuntupart
```rename your cups init file:
```
sudo mv /media/ubuntupart/etc/init.d/cupsd /etc/init.d/cupsd.bak
```Then update your system if successful.

---

### Post by CompiledMonkey on 2008-02-23
I'm having the same issue with Ubuntu 7.10 on Mac OS X using Parallels.

---

### Post by Seankel on 2008-04-05
> **Taylor said:**
> If you managed to get the live cd up and running, you could mount your partition and try to rename the cupsd file.

Create a folder:
```
sudo mkdir /media/ubuntupart
```Find your Linux/Ext3 partition
```
sudo fdisk -l
```Mount your partition
```
sudo mount  sudo mount -t ext3 /dev/hdXX /media/ubuntupart
```rename your cups init file:
```
sudo mv /media/ubuntupart/etc/init.d/cupsd /etc/init.d/cupsd.bak
```Then update your system if successful.

Ok. got live session running and followed those commands except i replaced hdXX with sda1. whats next?

---

### Post by Canobuntu on 2008-04-07
Hi
I am new to Ubuntu - Hope this will help.

I have a similar problem to the one discussed in this post - i.e. Startup stops at "Starting Common Unix Printing System: cups" but I can cause it to trigger. In my case the trigger event is whether I have my  WLAN card plugged in during startup 
[LIST]
[*]WLAN card installed - Everything stops after the line "Starting Common Unix Printing System".
[*]WLAN card removed, startup happens as expected. 
[/LIST]

Once I have logged in, I can plug in the WLAN card (USR5410) and the network fires up.

I had quite a game getting the card working. Had to resort to using ndiswrapper and the USR windows drivers. However, having got it working, it seems to be stable, but I cannot leave it in the laptop during bootup.

As an aside, I think the same happens during switch off. If the card is in the machine, then it hangs after the Ubuntu "count down" screen has closed.

Not sure if this helps, but it would be good to get to the bottom of what is going on. :)

---

### Post by stevenjlm on 2008-04-16
I have the same problem as everyone else here.
I installed drivers for my wifi card through ndiswrapper following the instructions on [http://ubuntuforums.org/showthread.php?t=288341](http://ubuntuforums.org/showthread.php?t=288341) using the a driver from technology planet (not the ASUS one). There must be a driver conflict or something with ndiswrapper because this obviously comes from trying to install my Wifi card. Everything was doing what was supposed to happen according to the instructions.
Each time I try to start Ubuntu 7.10 it stops at Starting Common Unix Printing System ever since.

---

### Post by stevenjlm on 2008-04-16
Ok I found out how to fix my problem, I hope this helps someone..
I started Ubuntu on live CD, mounted my normal partition with the bugging Ubuntu, and edited the /etc/modules file. All I had to do was remove ndiswrapper from the list and my computer fired up fine just after. I guess this is either a driver problem or a ndiswrapper problem, I'll try to find out...

---

### Post by puddinman on 2008-04-17
does anyone know what the codes are for gutsy ribbon?

---

### Post by was8v on 2008-05-01
> **Canobuntu said:**
> Hi
I am new to Ubuntu - Hope this will help.

I have a similar problem to the one discussed in this post - i.e. Startup stops at "Starting Common Unix Printing System: cups" but I can cause it to trigger. In my case the trigger event is whether I have my  WLAN card plugged in during startup 
[LIST]
[*]WLAN card installed - Everything stops after the line "Starting Common Unix Printing System".
[*]WLAN card removed, startup happens as expected. 
[/LIST]

Once I have logged in, I can plug in the WLAN card (USR5410) and the network fires up.

I had quite a game getting the card working. Had to resort to using ndiswrapper and the USR windows drivers. However, having got it working, it seems to be stable, but I cannot leave it in the laptop during bootup.

As an aside, I think the same happens during switch off. If the card is in the machine, then it hangs after the Ubuntu "count down" screen has closed.

Not sure if this helps, but it would be good to get to the bottom of what is going on. :)

Is there a solution for this? I have the exact same problem. removing ndiswrapper from /etc/modules means the computer boots fine with the card installed, but obviously I have to start the ndiswrapper module manually to get it to work.

Xbuntu on an IBM X21 with D-link Dwl-G630 card.

---

