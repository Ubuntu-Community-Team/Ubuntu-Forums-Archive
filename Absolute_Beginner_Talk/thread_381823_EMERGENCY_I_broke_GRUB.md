---
title: "EMERGENCY: I broke GRUB"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Hillerd on 2007-03-11
I just broke my GRUB an cannot start Ubuntu anymore - HELP.

My system: dual boot with Windows XP SP2 as 2nd system.

What I did:
The file system was this, when everything was still working:
...
hda5 ...
hda6 - mounted as documents
hda7 - /home
hda8 - /
...

I did not need documents anymore, so with the life CD I removed it. This changed also the numbering of the hda's, which surely is the cause of my problem.
the file system now is:
...
hda5 ...
hda6 - /home
hda7 - /
...
The error message I get after booting is:
GRUB loading stage 1.5
GRUB loading please wait
ERROR 17

Can anyone help?

---

### Post by taurus on 2007-03-11
Boot from the LiveCD, mount your / filesystem, and edit grub.conf.

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda7 /mnt/ubuntu
gksudo gedit /mnt/ubuntu/boot/grub/menu.lst
```
You also need to change the entries in /etc/fstab as since both / and /home are not the same anymore.

```
gksudo gedit /mnt/ubuntu/etc/fstab
```
If you are not sure what to do, post the contain of those two files here.

---

### Post by Hillerd on 2007-03-11
I changed in menu.lst the entry
"root (hd0,7)" to "root (hd0,6)", no change.

How does GRUB find the menu.lst now, it is not anymore on hda0,7?

---

### Post by Hillerd on 2007-03-11
This is the content of menu.lst:
```

title Ubuntu, kernel .....
root (hd0,6)
kernel /boot/....
quiet splash
initrd /boot/....
savedefault
boot

title Ubuntu, kernel .....(recovery mode)
root (hd0,6)
kernel /boot/....
single
initrd /boot/....
savedefault
boot

title Ubuntu, memtest86+
root (hd0,6)
kernel /boot/.....
boot

title other operating systems:
root

title Microsoft ....
root (hd0,1)
savedefault
makeactive
chainloader +1

```

And this is how gparted shows my hard disk:
```

/dev/hda1 - fat32 (thats the WXP recovery)
/dev/hda2 - fat32 WXP C-drive
/dev/hda3- extended
   /dev/hda5 - fat32 - WXP data drive
   /dev/hda10 - ext3 - that was the space I had removed, I tried to solve the problem reassigning the space
   /dev/hda6 - ext3 - /home
   /dev/hda7 - ext3 - /
   /dev/hda9 - ext3 - for wine
   /dev/hda8 - linux swap

```

It should be correct with setting root to hd0,6, shouldn't it?

---

### Post by torgrot on 2007-03-11
Go to here [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD) and follow the instructions for re-installing grub from the liveCD.

torgrot

---

### Post by confused57 on 2007-03-11
> It should be correct with setting root to hd0,6, shouldn't it?

Yes, but you might also need to change the root in your kernel line, i.e. root=/dev/hda7.

You should probably also change your /etc/fstab to reflect /dev/hda7 for your /.

---

### Post by Hillerd on 2007-03-11
I followed the instructions of targrot, no error occured.
The I tried "grub-install /dev/hda", which I found in a german thread ([http://wiki.ubuntuusers.de/GRUB?action=show&redirect=Grub)](http://wiki.ubuntuusers.de/GRUB?action=show&redirect=Grub)). 
This gives me the error "The file /boot/grub/stage1 not read correctly".

---

### Post by Hillerd on 2007-03-11
:) A big hug to torgrot, Ubuntu is starting again. I owe you a big glass of Munich beer!

Now I just have to check and set up fstab and menu.lst and then I will add here the solution.
Some tracks were misleading, such as the german post - it could not work.

---

### Post by Hillerd on 2007-03-11
Well, the hug went to torgrot, but the invitation for the beer goes to all of you. I have really been panicking and your prompt and ready support is really very much appreciated.

So first of all, one should NEVER remove a partition which has a number lower than that of root. This messes up GRUB (now that I understand the background - it's obvious). This also means that on a dual boot, one should place the root to the most left possible in the hard drive. This means especially "no document partitions before root".

Once GRUB is messed up, the solution is
- adjusting /boot/grub/menu.lst according to the new partition names (e.g. /dev/hda7)
- adjusting /etc/fstab according to the new partition names (also the UUID of root had changed - which was very surprising to me, unless I messed something up myself where I am not aware of)
- follow these instructions: [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
  > sudo grub
  > find /boot/grub/stage1
    (shows the partitions with GRUB, in my case hda0,6)
  > root (hda0,6)
     (in my case hda0,6, in yours it will surely be different)
  > setup (hd0)
  > quit
- restart computer and be happy

I am not sure if menu.lst really has to be edited. The changes I had done were gone afterwards, so maybe this process creates a new and correct file. But this was the process I made and it works now.

---

### Post by confused57 on 2007-03-11
Glad you got it working, you might want to bookmark Herman's homepage:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
you might want to check out the grub page in the index, it explains how grub works...how to determine the new UUID, etc.

The beer sounds good, I was stationed in Augsburg for 14 months(1971-1972)...excellent beer.

---

### Post by torgrot on 2007-03-11
Well, the thanks really goto Herman, he has helped me greatly with my GRUB problems.  His web page is an absolute life saver.  

I was in Kaiserslautern and Berlin one spring and they were doing the unthinkable to me, mixing CocaCola and good German beer together about 50-50.  They don't still do that, do they?

torgrot

---

