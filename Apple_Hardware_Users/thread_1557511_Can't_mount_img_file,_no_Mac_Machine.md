---
title: "Can't mount img file, no Mac Machine"
date: 2010-08-20
forum: Apple Hardware Users
---

### Post by unckybob on 2010-08-20
I am trying to mount the contents of a dmg file as it is outlined at:

[https://help.ubuntu.com/community/Ma...s#DMG%20Images](https://help.ubuntu.com/community/Ma...s#DMG%20Images)

I don't have a Mac machine. 

I used:

# dmg2img example.dmg example.img

I moved "example.img" to my Desktop.

Then used the following commands:

# sudo mkdir Temp
# sudo modprobe hfsplus
# sudo mount -t hfsplus -o loop example.img Temp
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

# dmesg | tail -2
[ 996.330997] ISO 9660 Extensions: IEEE_P1282
[ 1504.171181] hfs: unable to find HFS+ superblock

I also tried:

# sudo mount -o loop example.img Temp

This made a file on my Desktop called Temp that has a little disk icon.

# ls -l Temp
-rw-r--r-- 1 root root 27 2007-11-21 10:56 autorun.inf
dr-xr-xr-x 1 root root 2048 2008-10-13 16:39 boot camp
dr-xr-xr-x 1 root root 2048 2008-11-03 10:55 dvdcdsharing
-rw-r--r-- 1 root root 517432 2008-11-03 10:46 setup.exe

Notice that the size of Temp is about 520MB.

I used a file browser to open the little disk icon. It says that "setup.exe" is a "DOS/Windows" executable.

Now if this isn't all, this is what I get in "Disk Utility" under "System" -> "Administration".

Under "Storage Devices" and "Peripheral Devices" "example.img" is listed as an 8.1 GB file. But the size of "Temp" is only about 520MB.

The filesystem is "ISO 9660".

The label is "WindowsSupport".

The "Drive Model" is "Linux Loop: example.img"

Can someone please help?

---

