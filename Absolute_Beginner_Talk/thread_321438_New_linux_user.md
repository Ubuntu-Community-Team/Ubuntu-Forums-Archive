---
title: "New linux user"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by k4wedi on 2006-12-18
I've mananged to get ubuntu 6.10 to dual boot with windows xp on my laptop, but after that I don't know what to do to configurate things since I have never touched linux before. 

So a few questions...

1) I partioned my hard drive into 4 drives:

Windows (primary)
Linux (primary)
Swap
FAT32

When I boot up ubuntu I only see the windows drive and no other drives. Is this normal? I thought I should be seeing the linux drive.

2) How does one configurate things like touch sensitive clicking for the touch pad?

3) This is probably related to #2 but... how do I get wireless networking to work? I read that you need to add the "ndiswrapper" package via the Synaptic Package Manager to try and get my windows drivers recognized. I have no idea what this means :(

4) Why does ubuntu sometimes just freezes while is still booting (before reaching the login screen) ?

5) General tips and facts that one needs to know to get comfortable with linux

Any help would be much appreciated. :)

---

### Post by dbbolton on 2006-12-18
1- "filesystem" or simply "/" is your linux drive 
2- search for "synaptics" in synaptic package manager. there's a program that you can use to configure your touchpad (assuming it's a synaptics touchpad)
3- look in the faq/howto forum. there should be plenty of helpful threads there.
4- if you want to see what it's doing during boot, hit alt+F1. sometimes the splash screen displays one message for several processes.
5- play around. be prepared to learn. have fun.

---

### Post by macogw on 2006-12-18
for #3, what kind of wireless card do you have?  For ndiswrapper, you connect to a wired connection, then go to System > Administration > Synaptic Package Manager and search for ndiswrapper.  Check the box, and hit apply to install it.  Also download the Windows driver for it.  You're going to have to look at the HowTos for setting it up, though, sorry.  My card worked out of the box.

---

