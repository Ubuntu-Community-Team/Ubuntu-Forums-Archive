---
title: "How do I visit my Windows files?"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by camz on 2007-03-20
Hey guys, I'm new to Ubuntu and I'm loving it a lot, but I know absolutely nothing about it technically and may be posting asking for advice from time to time.

I'm currently running Windows XP Professional on my laptop, as well as Ubuntu 6.10 Edgy Eft, as a dual boot system.

I have heard it's possible to view your Windows files in Ubuntu, and if this is true, how do I do it.

The main reason I am doing this is because I have a problem, I am trying to get my wireless dongle (Belkin F5D7050) to work and I think you have to change the drivers. Any help on that (I have got absolutely no-where on installing the dongle) would be great too.

If the solutions involve the Terminal and commands, please give me the exact step-by-step instructions as I often have a lot of trouble following guides that are talking in a "foreign language" to me. This is why many guides have been of no use.

Thanks in advance,

Cams

---

### Post by taurus on 2007-03-20
You need to mount your Windows partition first before you can access it from Ubuntu.  Here's a guide.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Otherwise, post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
(That is a lower case letter l, not number 1.)

---

### Post by KenSentMe on 2007-03-20
> **taurus said:**
> You need to mount your Windows partition first before you can access it from Ubuntu.  Here's a guide.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Otherwise, post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudi fdisk -l
```
(That is a lower case letter l, not number 1.)

I think you mean sudo instead of sudi. However, i don't think sudo is needed at all.

---

### Post by camz on 2007-03-20
This still makes no sense. I'm really confused and it says that fdisk is an invalid option.

---

### Post by taurus on 2007-03-20
Did you use letter l as in **[COLOR="Red"]l[/COLOR]**arry when you ran that command?

```
sudo fdisk -**[COLOR="Red"]l[/COLOR]**
```

---

### Post by KenSentMe on 2007-03-20
Did you try the command 

fdisk -l

(so without sudi/sudo)?

---

### Post by KenSentMe on 2007-03-20
> **taurus said:**
> Did you use letter l as in **[COLOR="Red"]l[/COLOR]**arry when you ran that command?

Now how did you come up with that name :p

---

### Post by t4thfavor on 2007-03-20
You should see something similar to this
EDIT: Sudo is needed, I was not shown any drives without it.
```

sudo fdisk -l
Password:

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3275    26306406   83  Linux
/dev/hda2            3341        4864    12241530    f  W95 Ext'd (LBA)
/dev/hda3            3276        3340      522112+  82  Linux swap / Solaris
/dev/hda5            3341        4864    12232048+   7  HPFS/NTFS

Partition table entries are not in disk order

```

---

### Post by camz on 2007-03-20
I'm getting somewhere. Thanks for the guide. It seems to be working so far.

---

### Post by camz on 2007-03-20
That's pretty much what I saw but at the end of the columns NTFS was at the end.

---

### Post by taurus on 2007-03-20
> **camz said:**
> That's pretty much what I saw but at the end of the columns NTFS was at the end.

Can you at least post the output here so I can walk you through mounting it?  Otherwise, I am not even going to guess what partition is your Windows on.

---

### Post by t4thfavor on 2007-03-20
then you need to research the mount command, and then use it to mount the /dev/hdXX that had the ntfs tag.

something like

sudo mount /dev/hda5 /mnt/Windows_Partition

Good luck!

---

### Post by camz on 2007-03-20
A little help, that guide has helped but now I'm in File: /etc/fstab

I know the windows is mounted in hda 1 and its NTFS, but on this etc/fstab hda1 is nowhere to be seen

---

### Post by taurus on 2007-03-20
You need to add an entry to /etc/fstab for your ntfs.

```
/dev/hda1   /media/hda1   ntfs   nls=utf8,umask=0222   0   0
```
Then, you need to create a new mount point, /media/hda1, before you can mount it.

```
sudo mkdir /media/hda1
```

---

### Post by camz on 2007-03-20
Please could you make that a bit clearer? Where do I need to be to do this?

---

### Post by t4thfavor on 2007-03-20
Since this is nessicairy, after the mkdir running this command should take care of the rest.

```

sudo mount -a

```

then you should be able to navigate to the folder created in the mkdir command and see "Visit" the files for as long as you like :)

---

### Post by taurus on 2007-03-20
> **camz said:**
> Please could you make that a bit clearer? Where do I need to be to do this?

Which line are you talking here?  Do you mean the 

```
sudo mkdir /media/hda1
```?

You would type that in from a terminal.

---

### Post by camz on 2007-03-20
Guys I am very confused

---

### Post by t4thfavor on 2007-03-20
Press Alt+F2 and then type "gnome-terminal" in the box without quotes.

That my friend is a terminal window.

---

### Post by taurus on 2007-03-20
Look at post #6 of this thread, [http://www.ubuntuforums.org/showthread.php?t=389177](http://www.ubuntuforums.org/showthread.php?t=389177).

---

### Post by camz on 2007-03-20
I know what the terminal is im using it.

---

### Post by t4thfavor on 2007-03-20
Then just type the commands given into the terminal, and they should execute. 

Adding the line given to the /etc/fstab file can be done by copying and pasting. 

the text editor can be found at Applications>Accessoties>Text Editor

---

### Post by camz on 2007-03-20
Thanks so much it worked! Will this follow my changes in Windows?

---

### Post by t4thfavor on 2007-03-20
The drive is read-only, so no you can't make any changes.

---

### Post by camz on 2007-03-20
Yes I know that I cannot make changes in Ubuntu, but will it automatically change to whatever I do to it inside Windows?

---

### Post by camz on 2007-03-20
Hey guys, need a bit of help here.

Pretty new to Ubuntu, still don't understand all these commands, which is why most guides I use for this problem don't help much.

I used to use Belkin F5D7050 on Windows XP, then installed Ubuntu 6.10 to my computer as a dual boot, but on a single HD. The Belkin stick is installed and works fine on Windows, how can I get it to work on Ubuntu. Have had absolutely no progress so still at beginning. When I plug it in it doesn't respond. Would like, if possible, a step by step guide (or link to one) on getting this installed and running on Edgy, (I have the installation disc, it says the setup files can't be opened), and although I can type in the commands on Terminal, just giving me a list of what to type doesn't help as I am relatively new. A "walkthrough" would be handy.

Many Thanks,

Cams


This problem was also posted on Networking/Wireless, don't seem to be getting an answer, a little help please..

---

### Post by Efwis on 2007-03-20
here is the wiki page describing step by step how to get your dongle working.

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28Belkin%29%7C%28F5D7050%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28Belkin%29%7C%28F5D7050%29)

---

