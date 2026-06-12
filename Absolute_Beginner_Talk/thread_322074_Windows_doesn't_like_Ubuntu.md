---
title: "Windows doesn't like Ubuntu"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by Ryan H on 2006-12-19
I have had Ubuntu installed forever, and I had Windows lying around and I REALLY wanted to play Guildwars, so I installed it to play, but Windows didn't play nice and thinks it is the only operating system. Basically how do I reinstall GRUB so I can boot into my Ubuntu partition again?

Thank you.

-Ryan H

---

### Post by dbbolton on 2006-12-19
do you have it installed at all, and just need to reconfigure the menu.lst, or do you really need to install th whole deal over ?

---

### Post by rccharles on 2006-12-19
Windows XP will overwrite the master boot record. To re-install grub see:

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

I have not tried the suggestion.

Take care.

Robert

---

### Post by Ryan H on 2006-12-24
I've reinstalled GRUB but now I get this error when booting up into Ubuntu:
```

root (hd0,1)
Filesystem type unknown, partition type 0x7
Kernel /boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda2 re quiet splash

Error 17: Cannot mount selected partition

Press any key to continue. . .

```

If I press a key I get the GRUB menu with other Ubuntu Kernels, none of which work.

Any help?

-Ryan H

---

### Post by meng on 2006-12-24
Are you sure that (hd0,1) is the correct partition? Perhaps you could boot into LiveCD mode and recheck your partition table.
sudo fdisk -l

---

### Post by Step on 2006-12-24
It's trying to mount your Windows as a root partition, which will never work because it can't really boot Windows as root. You need to find which sda is your root partition and tell it to boot that instead of sda2.
Not sure how but I had the same problem.

---

### Post by Ryan H on 2006-12-24
It's either sda1 or sda3, one is Ubuntu and the other is Suse. I'm pretty sure it's sda3, how do I reconfigure GRUB for this?

-Ryan H

---

### Post by meng on 2006-12-24
sda1 = (hd0,0)
sda3 = (hd0,2)

---

### Post by Frank Golden on 2006-12-24
> **Ryan H said:**
> I've reinstalled GRUB but now I get this error when booting up into Ubuntu:
```

root (hd0,1)
Filesystem type unknown, partition type 0x7
Kernel /boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda2 re quiet splash

Error 17: Cannot mount selected partition

Press any key to continue. . .

```

If I press a key I get the GRUB menu with other Ubuntu Kernels, none of which work.

Any help?

-Ryan H

Check out 

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

and

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

These link are from   [http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

a great site on dual booting Ubuntu with XP (definitive !)

The first link is about super grub a neat grub recovery tool you can download and burn to a
CD or thumb drive if your computer can boot to a thumb drive.

The second link is a wealth of info about grub and info on restoring grub manually.

The third link is the web site/page the other two links come from.

This guy is thorough to say the least.
Must have info for anyone dual booting Ubuntu or Edgy.

---

### Post by spockrock on 2006-12-24
I think the best way to install grub is this way,

boot the live disc

open up terminal then

```
sudo grub
```
you should now see this in terminal

grub>
then do this
```
find /boot/grub/stage1
```
this then should spit out something like hdx,x; where the x's are numbers 
```
root (hdx,x)
```
use the numbers from the result of the previous command
```
setup (hd0)
quite
```

reboot and your are good, note that if you installed from the live disc, then you could of installed grub to a another drive, if you did that plx make the change to the setup line, however if you didnt the default is hd0.

---

### Post by Ryan H on 2006-12-24
That's exactly what I did, as root (hd0,2) (Which is my Ubuntu partition). But I still get the same error booting up it keeps trying to boot hd0,1. And I only have one hard drive so I don't think that is the problem.

-Ryan H

---

### Post by rccharles on 2006-12-24
> **Ryan H said:**
> It's either sda1 or sda3, one is Ubuntu and the other is Suse. I'm pretty sure it's sda3, how do I reconfigure GRUB for this?

-Ryan H

You can change the Grub boot parameters for the next boot ( or should I say current?) boot. 
On the Grub menu cursor down to the boot parameters you want to change, then press
e

cursor down to the line you want to change, then press 
e

make your changes

press the key
esc
esc

Press enter to boot


..........

Once you get a system booted, you will have to make the changes to the configuration file:
sudo nano /boot/grub/menu.lst

control-w
to save the file

Robert

---

### Post by Ryan H on 2006-12-24
I did that and this is what I came up with:
```

Booting the kernel.
mount: Mounting /dev/sda2 on /root Failed: No such device

```
Plus a longer string of mount errors resulting from the first one.

You don't think I deleted my Ubuntu partition when installing XP do you? :shock: :icon_frown: 

-Ryan H

Edit: I just realised my Ubuntu partition is on sda3. . . Which I just mounted and is infact my Ubuntu partition.
I entered root (hd0,2) which is sda3 right?

-Ryan H

---

### Post by meng on 2006-12-24
Yes, see my earlier post, but the real question is - did it work?

---

### Post by Ryan H on 2006-12-24
It worked, I booted up into the Ubuntu load screen and at Mounting Root file System it stopped and gave me the error. Why is it trying to mount /dev/sda2 instead of /dev/sda3?

Thanks.

-Ryan H

---

### Post by Ryan H on 2006-12-24
I really need help, my moms Christmas present was on my Windows partition and I can't mount it because nftsmount says it didn't boot up properly last time, so anyway I could get Windows to work again would be great. Ubuntu comes second now.

Please help me.

-Ryan H

---

### Post by meng on 2006-12-24
Please post the entire /boot/grub/menu.lst

---

### Post by Ryan H on 2006-12-25
How do I do that?

-Ryan H

---

### Post by spockrock on 2006-12-25
either write it out, or use a live disc and mount the ubuntu partition, and then copy and paste the contents of the menu.lst

ok to do that, pop in a live disc, then open up terminal....

```
mkdir ubuntu[code]
this will create a folder in live discs home folder called ubuntu, now we mount your ubuntu partition.
[code]sudo mount /dev/sda3 ubuntu/
```
now, that you have mounted your original ubuntu partition you can access the files......on it by going to that folder, so open your your menu.lst and paste here by,

```
gedit ~ubuntu/boot/grub/menu.lst
```
note this will only open the file in read-only if you want to modify it you have to use sudo.

just copy the contents and paste here.

---

### Post by Frank Golden on 2006-12-25
> **Ryan H said:**
> It worked, I booted up into the Ubuntu load screen and at Mounting Root file System it stopped and gave me the error. Why is it trying to mount /dev/sda2 instead of /dev/sda3?

Thanks.

-Ryan H
Just a guess but if you can get into the Ubuntu partition using the LiveCD open /etc/fstab
and make sure that /dev/sda3 is there and not sda2. I think installing XP changed the partition
and you need to change fstab to reflect this as well as /boot/grub/menu.lst.
You can also use a tool in windows that allows you to access your Ubuntu partition and make changes to it.
I am writing this from Ubuntu. Will boot to XP and get the name of the program for you.

Update: I'm back. The name of the program is ISF driver. You can get it here.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Once installed on your XP partition it will place an icon in you Control Panel.
This tool will let you assign a drive letter to your ext3 (Ubuntu) partition thereby giving you read/write access to
it. Be careful not to change any thing vital. Once in your Ubuntu partition locate /etc/fstab and change the entry from 
/dev/sda2 to the correct /dev/sda3. This should fix your problem. Remember to use ISF driver to remove the drive letter
after making the change to keep you or someone else from inadvertently messing up Ubuntu. This is a pretty powerful tool.
Use it sparingly.
Let us know if this fixed your problem.

---

