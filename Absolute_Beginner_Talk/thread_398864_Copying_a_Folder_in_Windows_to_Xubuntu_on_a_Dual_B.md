---
title: "Copying a Folder in Windows to Xubuntu on a Dual Boot"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by murkydurky on 2007-04-01
I am trying to copy a folder from my windows partition over to my Xubuntu partition. I could install the particular program again in xubuntu, but it takes over an hour to install, and I am trying to make it a little quicker. Forgive me for the newbness on here.. it's the little things that get me! Thank you in advance!

---

### Post by maccawolf on 2007-04-01
You can't go From Winblows to Ubuntu, but you CAN go from Ubuntu to windows.
In otehr words, boot up into Ubuntu and find the file you want. then copy it into Ubuntu. Winblows won't see Linux drives, but Linux can be forced to recognize Fat32 or whatever drives. At least that is what I have found.

---

### Post by murkydurky on 2007-04-01
> **maccawolf said:**
> You can't go From Winblows to Ubuntu, but you CAN go from Ubuntu to windows.
In otehr words, boot up into Ubuntu and find the file you want. then copy it into Ubuntu. Winblows won't see Linux drives, but Linux can be forced to recognize Fat32 or whatever drives. At least that is what I have found.
Let me clarify what i am trying to do. i am currently in Xubuntu, and i wish to copy the windows directory while im in Xubuntu. i just need the "dummy" instructions for copying a folder from Windows, to Xubuntu, while in the Xubuntu OS

---

### Post by maccawolf on 2007-04-01
Gotcha. I'm a newbie too. I think you should just be able to right click the folder  (copy) and then right click to paste it where you want it, but better let more of an expert here confirm this before you do anything.

---

### Post by murkydurky on 2007-04-01
thats what i figured..but.. how do i do that? lol.. i hate to sound so green.. but i have no idea how to view my window folders from within xubuntu

---

### Post by maccawolf on 2007-04-01
In my install of Ubuntu (6.10) they automount on startup, so I just go into PLACES....COMPUTER, but I'm not too sure how to mount them. SORRY....

---

### Post by alien21010 on 2007-04-01
Well Xubuntu typically will mount your drives for you.  If it didn't, then you can force it to mount by using the following commands:

First, make a folder on the desktop to mount to:

mkdir ~/Desktop/windows

Then mount the drive:

sudo mount -t ntfs -o ro,uid=1000 /dev/hda1 ~/Desktop/windows

Where /dev/hda1 is the partition that Windows is installed on...  To find out which partition windows is on type:  sudo fdisk -l, and look for the partition that has ntfs next to it.'

From there you should be able to find what you want and copy it using Thunar or whatever graphical file manager you are using.

If you need more help post the output of sudo fdisk -l.

---

### Post by murkydurky on 2007-04-01
im in xubuntu..not Ubuntu.. i dont have the "places" menu. but im sure there is an equivelant buried somewhere >.<

---

### Post by murkydurky on 2007-04-01
> **alien21010 said:**
> Well Xubuntu typically will mount your drives for you.  If it didn't, then you can force it to mount by using the following commands:

First, make a folder on the desktop to mount to:

mkdir ~/Desktop/windows

Then mount the drive:

sudo mount -t ntfs -o ro,uid=1000 /dev/hda1 ~/Desktop/windows

Where /dev/hda1 is the partition that Windows is installed on...  To find out which partition windows is on type:  sudo fdisk -l, and look for the partition that has ntfs next to it.'

From there you should be able to find what you want and copy it using Thunar or whatever graphical file manager you are using.

If you need more help post the output of sudo fdisk -l.

YES!! Thanks everyone! Alien.. you rock :guitar:

---

