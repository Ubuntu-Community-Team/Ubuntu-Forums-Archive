---
title: "On a Mac Quicksilver2002 933mhz"
date: 2010-07-15
forum: Apple Hardware Users
---

### Post by amigammon on 2010-07-15
I have booted from the .iso cd I made on my Mac last night and was tempted to install it on a 6gb partition that I have on my main HDD but was a bit scared to go past the fourth (or so) step in manual installing where I pick that partition and *do what?* Is it going to install the OS on that partition and leave everything else alone to give me a dual booting PowerMac? It doesn't quite say. I am fearful of screwing up my little ol' machine. Can anyone direct me to something that gives a step by step in manual installation on an already created (HFC+) partition to create a dual booting PowerMac?

It was nice to see the Gnome desktop on my Mac.

cj
from a Vaio VGN-A190 running XUbuntu right now.

---

### Post by linuxopjemac on 2010-07-15
Ih you make 3 partitions out of that 6 Gb, one an Apple bootstrap partition of 1Mb for the yaboot bootloader, one of say 5,5Gb for / (root) and 500Mb as swap you'll be fine. It won't touch the other partitions.

---

### Post by amigammon on 2010-07-15
The answer starts with "Ih." Is that supposed to be "If"? So what I do is partition the partition into 3 smaller partitions? And this installation CD can do that for me without upsetting any other part of my HDD?

Thank you for your reply. I appreciate your help.

cj

---

### Post by linuxopjemac on 2010-07-16
I don't understand "ih" or "1f". What are you talking about?

Just give me an output of
sudo mac-fdisk /dev/your_device
your_device may be hda or sda or something like that
It will list all partitions

---

