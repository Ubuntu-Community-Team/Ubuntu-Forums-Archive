---
title: "what do these instructions mean??"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by fitzybhoy on 2007-11-02
please help me guys, im trying to install 7,10 on my 6715b and these instructions mean nothing to me ...


Live CD 

install menu click F6
add this : noapic
click enter

install hangs:

click alt+f1 then
sudo -s
killall gdm
rmmod bcm43xx
apt-get update
apt-get install xorg-driver-fglrx
depmod -a
aticonfig --initial
exit
startx

install ubuntu 
restart 
recovery mode
modprobe -r bcm43xx
nano /etc/modprobe.d/blacklist

insert this : blacklist bcm43xx

dhclient eth0
apt-get update
apt-get install xorg-driver-fglrx
aticonfig --initial
reboot

Install ndiswrapper 
in ubuntu open console 

sudo apt-get update
sudo apt-get install ndiswrapper-common
sudo apt-get install ndiswrapper-utils
sudo apt-get install cabextract

Download this windows drivers from HP (sp34152.exe)

mkdir sp
cd /sp
mv sp34152.exe /sp
cabextract sp34152.exe
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo gedit /etc/modules

insert this : ndiswrapper
sudo reboot

---

### Post by LaRoza on 2007-11-02
Where and and in what context did you get this. I looks like you or someone else was having trouble installing. Tell us what you want to do. I could go line by line and tell what these instructions mean, but that might be a waste of time without proper explanation.

---

### Post by fitzybhoy on 2007-11-02
> **LaRoza said:**
> Where and and in what context did you get this. I looks like you or someone else was having trouble installing. Tell us what you want to do. I could go line by line and tell what these instructions mean, but that might be a waste of time without proper explanation.

its a direct quote from this thread...

[http://ubuntuforums.org/showthread.php?t=579535](http://ubuntuforums.org/showthread.php?t=579535)

im burning the image as i type and wanting to install ubuntu immediately.

this is my first linux installation so not too clever with it.

---

### Post by philinux on 2007-11-02
Hopefully when you install you wont see this stuff.

---

### Post by jwo7777777 on 2007-11-02
Looks like stuff for installing on a laptop with a broadcom wireless card and a bad apic implementation.

---

### Post by fitzybhoy on 2007-11-02
> **LaRoza said:**
> Where and and in what context did you get this. I looks like you or someone else was having trouble installing. Tell us what you want to do. I could go line by line and tell what these instructions mean, but that might be a waste of time without proper explanation.

bump.

cant get into recovery mode.

hows it done?

now my laptop wont start :(

---

### Post by fitzybhoy on 2007-11-03
> **fitzybhoy said:**
> bump.

cant get into recovery mode.

hows it done?

now my laptop wont start :(

bump,

i've installed ubuntu to my laptop. i've  restarted the laptop after creating the accounts etc. i followed the instructions until i need to enter recovery mode. i'm reasonably confident i can complete installation myself.

also, after installing from the disc, will i need it to complete installation?

using PS3 internet browser just now.

---

### Post by fitzybhoy on 2007-11-03
> **fitzybhoy said:**
> bump,

i've installed ubuntu to my laptop. i've  restarted the laptop after creating the accounts etc. i followed the instructions until i need to enter recovery mode. i'm reasonably confident i can complete installation myself.

also, after installing from the disc, will i need it to complete installation?

using PS3 internet browser just now.

guys, im on the laptop just now, im at the stage just before the install.

running linux from the live CD, how do i get it into recovery mode?

---

### Post by jw5801 on 2007-11-03
I'm assuming by recovery mode they mean the root console recovery kernel bootup? When you get to the grub menu (you may have to press Esc to see it) and there should be a few options, one will be your regular bootup, one will be a recovery terminal (or something like that), and the third will be memtest. From what I can tell I think they want you to boot into the recovery terminal option and fix up your install before you try to reboot again. It might be an idea to post in the original thread if you're confused about something in it, that way you're pretty much guaranteed that the people who wrote the original post will read your response and they'll have much more idea about what they were recommending you do!

---

### Post by fitzybhoy on 2007-11-04
> **jw5801 said:**
> I'm assuming by recovery mode they mean the root console recovery kernel bootup? When you get to the grub menu (you may have to press Esc to see it) and there should be a few options, one will be your regular bootup, one will be a recovery terminal (or something like that), and the third will be memtest. From what I can tell I think they want you to boot into the recovery terminal option and fix up your install before you try to reboot again. It might be an idea to post in the original thread if you're confused about something in it, that way you're pretty much guaranteed that the people who wrote the original post will read your response and they'll have much more idea about what they were recommending you do!

thanks for the info, i've asked a few people for help via pm on the matter.

---

