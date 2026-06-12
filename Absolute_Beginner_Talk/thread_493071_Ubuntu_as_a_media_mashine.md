---
title: "Ubuntu as a media mashine"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by doomstone on 2007-07-05
I have grown tiret of Windows XP Media Center.
I use this computer as my Media Center :D it have a monitor that i use for web browsing and so on, but it also have tv out so i can watch my movies thoug my tv.

So what i'm asking is basicly where can i get a guide to set my ubuntu up so i can use it as my Media Center?

---

### Post by Nekiruhs on 2007-07-05
[Mythbuntu]("http://www.mythbuntu.org/") may be what you need. It is Ubuntu with a preconfigured  Mtyh TV setup. Perfect for what you need.

---

### Post by wolfen69 on 2007-07-05
try mythtv. [http://www.mythtv.org/](http://www.mythtv.org/)  it should be available for download in synaptic.

---

### Post by doomstone on 2007-07-05
> **wolfen69 said:**
> try mythtv. [http://www.mythtv.org/](http://www.mythtv.org/)  it should be available for download in synaptic.

An't there other programs then mythtv, i remember that i have tryed it before and diden't like it

---

### Post by Nekiruhs on 2007-07-05
Not that I know of. You might want to try it anyway depending on how long ago you tried it it may have changed.

---

### Post by doomstone on 2007-07-05
I have chosen to try MythTV again, but i have some problems with the setup of the partitions

i have 3 hardrives in my pc
1: 250gb
  - Pat 1: NTFS, 25 gb - windows root system
  - Pat 2: NTFS, 220gb - Media drive
2: 300gb
  - Pat 1: NTFS, 300gb - Media drive
3: 300gb
  - Pat 1: NTFS, 300gb - Media drive

What i have done is to delete the 25g gb partition on the the first hardrive. and created a 2gb swap driver (end) and a 23gb ext3 drive (Beginning). but when i press next dose it say "No root file system is defined".
I'm a bit afraid of trying my way thoug this because i don't wonna lose my 750gb data.
What have i done wrong?

---

### Post by Nekiruhs on 2007-07-05
You have to select a partition for / it will install the system there.

---

### Post by doomstone on 2007-07-05
Thanks it is now installed and working >D
But don\t this disto come with an usable interface? i only have the option to start and stop mythtv.
Don\t it have gnome or kde_

---

### Post by Nekiruhs on 2007-07-05
can you get to a terminal (Try pressing CTRL + ALT + F1)? If you can, run ```
sudo apt-get install ubuntu-desktop
``` for Gnome or ```
sudo apt-get install kubuntu-desktop
``` for KDE.

---

