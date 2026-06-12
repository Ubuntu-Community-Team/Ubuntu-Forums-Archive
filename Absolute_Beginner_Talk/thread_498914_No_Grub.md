---
title: "No Grub"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Nessa on 2007-07-11
If I don't want a dual boot setup, can I just remove my primary drive which has xp and proceed with installing ubuntu on my slave drive? When they're both plugged in, will xp automatically load?

---

### Post by southernman on 2007-07-11
In short... Yes.

If you wanted to boot into Ubuntu, just disconnect the XP drive and power up. Seems like a lot of hassle to me.

---

### Post by Nessa on 2007-07-12
Is there an easier way to do this?

---

### Post by southernman on 2007-07-12
> **Nessa said:**
> Is there an easier way to do this?The easiest way is to just dual boot. Not sure why you said you didn't want to do that, but it's very reliable and quickly recoverable in the event you decide to stop using Ubuntu.

If need be, I'll find a linky or two for you.

---

### Post by Vajra Vrtti on 2007-07-12
Some BIOS (mine, for instance) allow you to chose from which HD you want to boot.
Just curious: why not a dual boot setup?

---

### Post by Nessa on 2007-07-12
The main thing is that most people in the house use xp. I want ubuntu. But I don't want to risk wrecking xp in any way.

---

### Post by southernman on 2007-07-12
> **Nessa said:**
> The main thing is that most people in the house use xp. I want ubuntu. But I don't want to risk wrecking xp in any way.

Admirable for sure!

Have a look at Hermanzone, It's maybe one of the more definitive grub guides written.

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

Just so you know, it's quite easy as I understand (read: have read many threads here about it) to recover a busted MBR to get back into XP. The data isn't what gets busted, just the boot record. You do need an XP cd to fix it with either fixmbr or fixboot.

Have fun! ;)

---

### Post by Nessa on 2007-07-12
Exactly... I don't have the xp cd anymore.

---

### Post by Vajra Vrtti on 2007-07-12
I completely agree with *southernman.* If you are installing Ubuntu into another HD the only thing the installation process will change in the XP volume is the MBR. As he also said, that is easily recoverable (but you need the XP install CD for that).

---

### Post by southernman on 2007-07-12
> **Nessa said:**
> Exactly... I don't have the xp cd anymore.

No problem really then.. well maybe a little more reading required, but no hill for a stepper!

Nifty little program called Super Grub can help you out in time of troubles. Yet another Hermanzone link to follow:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by confused57 on 2007-07-12
I have 2 systems set up this way:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by Nessa on 2007-07-12
I've installed ubuntu on the drive. Updating now...

I tried to print the instructions. Error though. I guess it wasn't installed.

It'll take a few hours for the update to finish.

---

### Post by Nessa on 2007-07-12
Can I go ahead and shutdown the pc, connect the windows drive as slave, power it on and just continue with the updates later?

---

### Post by confused57 on 2007-07-12
> **Nessa said:**
> Can I go ahead and shutdown the pc, connect the windows drive as slave, power it on and just continue with the updates later?
I would think you could just cancel the downloading of the updates...the repositories are rather slow tonight...then the updates should begin downloading where it left off when you cancelled after you reboot into Ubuntu.

---

### Post by Nessa on 2007-07-12
When I connect the windows drive as slave and start it up, ubuntu won't load. 

I'm given 3 options: the regular ubuntu, recovery mode and I forgot the 3rd one. Tried all 3, wouldn't work. I will try again if more info is needed.

---

### Post by Nessa on 2007-07-12
When ubuntu is the primary drive, the windows drive isn't detected. But when the windows is the primary drive, the ubuntu drive is detected. It's not in My Computer which I guess is ok since it's in a different format.

This is what I get when the ubuntu is primary and windows drive is slave:

__________________________
Error 2: Bad file or directory type

Press any key to continue...
__________________________
-Ubuntu, kernel 2.6.20-15-generic
-Ubuntu, kernel 2.6.20-15-generic (recovery mode)
-Ubuntu, memtest86+

Press enter to boot the selected OS, 'e' to edit the commands before booting,
or 'c' for a command line
__________________________

I have ubuntu installed successfully on the drive.  More ideas are welcome.

Thanks again!

---

### Post by southernman on 2007-07-12
> **Nessa said:**
> When ubuntu is the primary drive, the windows drive isn't detected. But when the windows is the primary drive, the ubuntu drive is detected. It's not in My Computer which I guess is ok since it's in a different format.

This is what I get when the ubuntu is primary and windows drive is slave:

__________________________
Error 2: Bad file or directory type

Press any key to continue...
__________________________
-Ubuntu, kernel 2.6.20-15-generic
-Ubuntu, kernel 2.6.20-15-generic (recovery mode)
-Ubuntu, memtest86+

Press enter to boot the selected OS, 'e' to edit the commands before booting,
or 'c' for a command line
__________________________

I have ubuntu installed successfully on the drive.  More ideas are welcome.

Thanks again!

I take it your Windows drive was the primary drive at install time, correct? (Windows has to feel like it's top dog or it won't let you play in it's sandbox.)

If the above answer is yes, then just leave the drives plugged in as they were and boot into the Ubuntu side if your using it. The rest of the gang can get into windows as needed. Your trying to make it more complicated than it really is, it seems. ;)

In order for Windows to read/write the files on your Ubuntu install, you have to install an additional program for that into Windows. Just google for "read write to linux partition in windows" or something of that sort.

In ubuntu you have to install ntfs-3g to enable writing files into an NTFS partition.

---

### Post by Nessa on 2007-07-12
No, I unplugged the windows drive during install. As indicated in the how to thread.

---

### Post by southernman on 2007-07-12
> **Nessa said:**
> No, I unplugged the windows drive during install. As indicated in the how to thread.

Ok. I wouldn't have done it that way personally. On to trying to solve your problem.

Did you do as instructed if Ubuntu gave errors by editing the grub menu list, with this edit:

```
rootnoverify (hd1,0) 
```

It should look like this for the windows drive option:

> title              Windows XP
rootnoverify (hd1,0) 
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

---

### Post by Nessa on 2007-07-12
Can I do that without being able to boot up ubuntu? (with the windows drive plugged in) How?

---

### Post by drowner on 2007-07-12
You can use a liveCD, the same one you used to install (if you used the LiveCD)

If you used the Alternate CD you will need a LiveCD of some sort...

---

### Post by confused57 on 2007-07-12
> **Nessa said:**
> Can I do that without being able to boot up ubuntu? (with the windows drive plugged in) How?
Which version of Ubuntu did you install & did you have the drive connected as primary master when you installed Ubuntu(with the Window's drive disconnected)?   The jumpers on both hard drives should probably be set to "Cable Select", your bios hard drive boot order should be primary master first, slave second, and you might want to check in your bios setup that both hard drives are detected correctly & the slave drive controller is enabled(or possibly set to "auto").
You could boot the live cd, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"
Do this with both hard drives connected...Ubuntu as master and Windows as slave.

While you're booted in the live cd, mount your root partition:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hda1 /media/ubuntu
```
look at the output of "sudo fdisk -l" and substitute your root partition for "/dev/hda1"(for example, "/dev/sda1")

then post the output of your menu.lst:
```
gedit /media/ubuntu/boot/grub/menu.lst
```
menu.lst is short for menu.list

I assume you can boot both the Window's drive and Ubuntu drive when each is the only hard drive connected...

---

### Post by Nessa on 2007-07-12
Just got home from work.

Here's the thing...

If windows is the primary drive, BIOS detects the 2 drives.

If ubuntu is the primary drive, BIOS only detects the ubuntu drive and I get those errors in Page 2 of this thread.

Any ideas?

ETA: Ubuntu 7.04. Yep primary master when I installed.

---

### Post by confused57 on 2007-07-12
> **Nessa said:**
> Just got home from work.

Here's the thing...

If windows is the primary drive, BIOS detects the 2 drives.

If ubuntu is the primary drive, BIOS only detects the ubuntu drive and I get those errors in Page 2 of this thread.

Any ideas?

ETA: Ubuntu 7.04. Yep primary master when I installed.
If you can boot first to the slave drive, try setting Windows as master & Ubuntu as slave & see if Ubuntu will boot set up this way.

---

### Post by Nessa on 2007-07-12
I was making it harder than it should be. I removed the changes from menu.lst and used the windows drive as primary. I'll just do F11 so I can pick the ubuntu drive when I want to use that. Thanks guys!

During installation, I had ubuntu take up the whole drive. Do I have to use the livecd if I want to add partitions?

---

### Post by drowner on 2007-07-12
> **Nessa said:**
> I was making it harder than it should be. I removed the changes from menu.lst and used the windows drive as primary. I'll just do F11 so I can pick the ubuntu drive when I want to use that. Thanks guys!

During installation, I had ubuntu take up the whole drive. Do I have to use the livecd if I want to add partitions?


yes, you can't partition a drive that you are currently using.

---

