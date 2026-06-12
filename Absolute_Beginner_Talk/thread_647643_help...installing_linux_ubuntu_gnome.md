---
title: "help...installing linux ubuntu gnome"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by shucks on 2007-12-22
Ok so I burned the ubuntu thing on a  cd m tried to install it but it says it'll erase the previous partition which I'm assuming is my windows vista...how do I install it so that I can use either linux or windows? Right now I'm on the ubuntu thing I think with something called gnome nautiulus like desktop thing. But the desktop has nothing like theres no menu like windows or anything. I can't even turn my computer off or open my cd thing. I have the ubuntu cd still in.

oh and wheres the package manager or whatever I use to install stuff..

---

### Post by PriceChild on 2007-12-22
If you want to keep windows, then you need to resize your windows partition.

The Installer (link on the livecd desktop) has an option to resize the existing partitions and use free-ed space.

I would suggest you backup ALL important data before attempting a resize. Its not usually dangerous.... but sod's law and all :)

---

### Post by shucks on 2007-12-22
on the installer thing it says:

Prepare disk space
How do you want to partition the disk?
- Guided - use entire disk
- Manual

Which one do I do? And it says use entire disk and when I click ok for guided it says warning: this will destroy all data on any partitions you have removed or reformatted. What does that mean?

actually i just tried and got an error and had to cancel

edit - I'm using vista maybe thats a problem?

---

### Post by lgambett on 2007-12-22
If you want to be absolutely sure of the result... (I have followed this process two dozen times never losing data)
1) Defrag your Vista partition
2) Chkdsk your Vista partition
3) Get a copy of Knoppix live CD from [www.knoppix.org](www.knoppix.org)
4) Start your PC with Knoppix CD
5) With Qtparted program resize your Vista partition. Qtparted is a program very similar to Windows Partition Magic.
6) Launch again Ubuntu installation, and tell to the installer to use only free space.

It is a little bit slow but is safe and gives you full control on what is happening.

---

### Post by freesitebuilder on 2007-12-22
I had to defrag three times before my XP had moved all fragments and left a clear disk area to use.

---

