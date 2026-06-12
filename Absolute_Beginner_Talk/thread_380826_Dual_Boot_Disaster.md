---
title: "Dual Boot Disaster"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by OldGrey on 2007-03-10
Hi,
I am new to Ubuntu, having only downloaded it a day or 2 ago and I really like it. However I messed up and though I can access Ubuntu, when I try to boot up Windows the computer gives up and switches off. While I can do most of what I need to in Ubuntu, I still need windows for some stuff and more to the point not all the users in the household appreciate not being able to have the choice. So can I reinstall windows (XP home) without losing Ubuntu, or should I start from scratch?

I am not a computer expert, so please be gentle.

---

### Post by teaker1s on 2007-03-10
so are we saying windows starts, crashes and reboots? if so when windows is booting tap F8 and select safe mode. most likely you want to run scandisc and defrag if you resized hard  drive

---

### Post by Gerard Barberi on 2007-03-10
> **OldGrey said:**
> Hi,
I am new to Ubuntu, having only downloaded it a day or 2 ago and I really like it. However I messed up and though I can access Ubuntu, when I try to boot up Windows the computer gives up and switches off. While I can do most of what I need to in Ubuntu, I still need windows for some stuff and more to the point not all the users in the household appreciate not being able to have the choice. So can I reinstall windows (XP home) without losing Ubuntu, or should I start from scratch?

I am not a computer expert, so please be gentle.

If you reinstall windows, it will overwrite Grub and then you will not be able to boot into ubuntu until you restore Grub.  If you reinstall ubuntu it will restore Grub.  When installing... Windows first, then linux.

Can you post the results of 

gedit /boot/grub/menu.lst

to see if there is a problem with the grub config.

---

### Post by easyease on 2007-03-10
i have the same problem but find windows starts up properly after the first crash/reboot, guess i have got used to the littkle quirk.

---

### Post by Herman on 2007-03-10
Hello OldGrey, 
You shouldn't have to re-install, but I don't really know exactly what's wrong yet, so I'm not sure. I can say it's extremely rare to need to re-install because of a booting issue.

Have you tried booting Windows from a [Super Grub Disk]("http://supergrub.forjamari.linex.org/") or a  [GAG]("http://users.bigpond.net.au/hermanzone/p12.htm") Boot Manager Disk?
Quite likely it will boot alright if you try one of those.

In most cases when Grub won't boot Windows it is a simple matter of editing a file called /boot/grub/menu.lst in Ubuntu. That's quite easy to do and would be a lot quicker and less trouble than re-installing Windows.
In order to tell you what you might need to change in /boot/grub/menu.lst, I would need to see a copy of that file posted here please, and here is the command you can use in a terminal to get the file, ```
sudo gedit /boot/grub/menu.lst
``` Other information needed before editing your menu.lst will be a copy of your partition table as seen by a partitioning program called fdisk, here's how you get that, ```
sudo fdisk -lu
``` If you can post those two files here someone might be able to help you fix your problem, I hope. Unless your problem is something different from what I think it is.
> when I try to boot up Windows the computer gives up and switches off Is there anything more you can tell me? Does it actually shut down, or is there some error message that it stops at and you have to switch it off to reboot? If so then the exact error message could be helpful.

Regards, Herman :)

---

### Post by OldGrey on 2007-03-10
Thanks for the swift replies, Sorry I did not give much detail.

The result of using fdisk was:

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   131797259    65898598+   7  HPFS/NTFS
/dev/hda2       235512900   240107489     2297295    5  Extended
/dev/hda3       131797260   235512899    51857820   83  Linux
/dev/hda5       239962968   240107489       72261    7  HPFS/NTFS
/dev/hda6       235513026   239962904     2224939+  82  Linux swap / Solaris

Partition table entries are not in disk order

Re trying to boot up windows. When I select it in the boot loader. I comes up with a screen apologising for the fact that it did not start successfully and offers various options including trying a normal reboot or starting in safe mode. If I try the former I get a brief flash of the screen you get when windows is loading then the computer restarts. If I try safe mode the screen briefly fills with a load of messages and again the pc restarts.

Regards Charles

---

### Post by Herman on 2007-03-10
Well I think teaker1s's answer would have been the best one but if you can't use Windows in safe mode either then even that solution seems unworkable. 

It doesn't seem to be a grub problem at all, since Windows begins to boot, so Grub has already done it's job. 

Would you like to try running a filesystem check on it from [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php")? You can download an .iso image for one of those for free, and it's less than 50 Mb to download. After you burn that to disk and boot it, you right-click the partition you want to run a file system check on and click 'check'. Wait while the filesystem check runs. When it is finished you can click on the little triangles to expand the output of GParted and see what GParted has to say about the file system and what has been done. Hopefully, when you reboot you'll be able to boot into Windows and it will start properly for you. That's the best suggestion I can think of. I hope it will help.

Regards, Herman :)

---

### Post by teaker1s on 2007-03-10
most solutions require actually booting windows to repair it, I did find this 
[http://www.aumha.org/win5/a/shtdwnxp.php]("http://www.aumha.org/win5/a/shtdwnxp.php")

which you may find something that matches your configuration

---

