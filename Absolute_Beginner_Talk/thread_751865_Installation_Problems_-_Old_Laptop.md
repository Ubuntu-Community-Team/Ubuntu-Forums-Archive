---
title: "Installation Problems - Old Laptop"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2008-04-11
Hey there, I just recently got an older sony vaio from a coworker who didn't want it, I want to put ubuntu on it as windows xp was running on it just fine before hand, here's the issue. When I use the alternate install cd and use the command "live acpi=off no apic nolapic" i can get the live cd running in text mode and installs the text only version of ubuntu I cant get xserver, I did a sudo apt-get install xserver-xorg and got all that but every time I punch in the startx it tells me command not found. Now so I try to sudo apt get install xserver and it tells me "package xserver is not available but is refered to by another package......etc" this laptop doesn't even have a slot for ethernet only the old 56k stuff, I'm adding a nic card to the pci slot but don't have it yet. Anyway I can fix this, get xserver, and boot into ubuntu graphically?? THanks!!

---

### Post by smartboyathome on 2008-04-11
It would probably be too heavy for that. You should try Xubuntu.

---

### Post by 3togo on 2008-04-11
try
sudo aptitude install ubuntu-desktop

> **Tumpster said:**
> Hey there, I just recently got an older sony vaio from a coworker who didn't want it, I want to put ubuntu on it as windows xp was running on it just fine before hand, here's the issue. When I use the alternate install cd and use the command "live acpi=off no apic nolapic" i can get the live cd running in text mode and installs the text only version of ubuntu I cant get xserver, I did a sudo apt-get install xserver-xorg and got all that but every time I punch in the startx it tells me command not found. Now so I try to sudo apt get install xserver and it tells me "package xserver is not available but is refered to by another package......etc" this laptop doesn't even have a slot for ethernet only the old 56k stuff, I'm adding a nic card to the pci slot but don't have it yet. Anyway I can fix this, get xserver, and boot into ubuntu graphically?? THanks!!

---

### Post by Ecclesia on 2008-04-11
I'm going to guess that your computer is going to be too slow on Ubuntu (or doesn't have enough ram) even for Xubuntu if you're using a computer that didn't come with a network card (how old is it?)

As much as I love Ubuntu, I have to say, I've had way more luck with Debian for turning older computers into survivors.  It's easy to install only what you need.  Recently I saved an old p3 300mhz laptop using Debian and four floppy disks (the cd rom drive was broken).  Of course, you will probably want a nic card, but you should be able to install a full system from a cd.

Alternately, try a distro designed for use on an older machine.  Elive, Damn Small, Puppy, Slitaz, etc.

---

### Post by kerry_s on 2008-04-11
what model vaio? i use a vaio pcg-f430, it's 450mhz 256mb ram(maxed).

go debian it's way better on the old stuff.
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso)

for when you get a nic card and can do custom.
net installer->
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)


also the command from a base install is->
apt-get install xorg (your wm) (what ever else)

xorg is the new meta package for X

---

