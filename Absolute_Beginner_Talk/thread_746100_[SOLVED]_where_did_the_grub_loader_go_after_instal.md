---
title: "[SOLVED] where did the grub loader go after installing xp?"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by bhadotia on 2008-04-05
i reinstalled my xp today but now after restarting the computer i find that the grub loader is gone my computer is automatically booting xp alone . i cannot acess my ubuntu desktop, NEED HELP PLZ!:confused::confused::confused::confused:

---

### Post by barbedsaber on 2008-04-05
windows has its own bootloader, which it loads over grub, and it doesn't recognise ubuntu.

head on over to[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")
download it, burn the iso, and boot it.

it will reinstall grub over the top of the windows bootloader

and as a tip, try and install linux after windows. in future, it takes out this irratating step.

hope that helped

---

### Post by stefangr1 on 2008-04-05
If you reinstall windows, grub is replaced with the windows mbr. You will have to install grub again.

---

### Post by bhadotia on 2008-04-05
Thanx Guys That Helped A Lot:)

---

### Post by cb951303 on 2008-04-05
it's simple to recover.
run the ubuntu live cd, chroot to your system. run grub-install ;)

---

### Post by bhadotia on 2008-04-05
> **cb951303 said:**
> it's simple to recover.
run the ubuntu live cd, chroot to your system. run grub-install ;)

sorry! but what is meant by "chroot to your system, run grub-install"?

---

### Post by northern lights on 2008-04-05
[Recovering Ubuntu After Installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by barbedsaber on 2008-04-05
from looking at the guide, the super grub disk way looks easier, if you have a spare CD of course.

although, they give a usb version, so if you can boot from usb, you could do it that way.
probably easier to use the cd tho.

---

### Post by bhadotia on 2008-04-05
alright I've installed grub but it is not booting ubuntu (windows is booting), the following message is coming:

  error15: file not found.

what does that mean?

---

### Post by billgoldberg on 2008-04-05
I don't know what that error message means, but I** think** it means that grub can't find ubuntu.

Boot into ubuntu using the supergrub cd, and then you should manually point grub to the partition ubuntu is on.

I forgot how to do this, but someone here will be able to help you (or google for it).

---

### Post by bhadotia on 2008-04-05
so is any body going to to help?:popcorn:

---

### Post by bhadotia on 2008-04-05
wait! (i just noticed it) :is it necessary to use the same live cd to install grub with which the ubuntu was installed? i installed my ubuntu using a friend's dvd (which he himself got from a friend of his who got it free with chip magazine). 

 BUT, now i installed the grub loader with the live cd of my own.:confused:

---

### Post by bumanie on 2008-04-05
As far as I know you can use a different ubuntu live cd without problems. Once the live cd has arrived, go to the desktop and open terminal 
> sudo grub
> find /boot/grub/stage1
This will give an output of (hd?,?) In the next step replace the question marks with the corresponding numbers form the output.
> root (hd?,?)
> setup (hd?)
> quit
reboot and all going well, grub should be installed and boot as usual.

---

### Post by bhadotia on 2008-04-05
i did the exact same thing as above (not once but twice) but when i restarted the computer(in first attempt) it didn't shut down so i manually switched off the comp . in the next try all went well (but to no avail). any comments? also in the first try grub was installed but there also the same error came (that is why i retried (reinstalled grub that is)-thinking my manually restarting the comp might have caused some problem).

---

### Post by Nikhil Gohil on 2008-04-05
try this...........this would b e for me.....
```
sudo fdisk -l
Device Boot Start End Blocks Id System
/dev/hda1 * 1 2550 20482843+ af Unknown
/dev/hda2 2551 3825 10241437+ 83 Linux
/dev/hda3 3826 3890 522112+ 82 Linux swap / Solaris
/dev/hda4 3891 12161 66436807+ 7 HPFS/NTFS
```
here /dev/hda2 is linux partition as you can see.......then,mount your linux drive...
```
sudo mount /dev/hda2 /mnt
```
then....
```
sudo grub-install --root-directory=/mnt /dev/hda

```
then reboot....that should do it..........

EDIT: i found this [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by bhadotia on 2008-04-05
hey nikhil ' this happened when i tried your idea:


```
The file /mnt/boot/grub/stage1 not read correctly.

```


here is how i carried out the whole process:

```

ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x004f4457

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2709    20480008+   7  HPFS/NTFS
/dev/sda2            2710       10336    57657285    f  W95 Ext'd (LBA)
/dev/sda3            6040       10336    32483398+   7  HPFS/NTFS
/dev/sda5            2710        4647    14643184+  83  Linux
/dev/sda6            4647        5940     9775521   83  Linux
/dev/sda7            5940        6040      755023+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/hda
/dev/hda: Not found or not a block device.
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
The file /mnt/boot/grub/stage1 not read correctly.
ubuntu@ubuntu:~$ 

```


so what should be done now?

---

### Post by Nikhil Gohil on 2008-04-05
sorry for the late rely dude.....but you seem to have messed up ur fstab and mtab . post outputs of ```
cat /etc/mtab
``` and ```
cat /etc/fstab
```

---

### Post by bhadotia on 2008-04-06
sorry for the late reply guys but i went to sleep.


alright here is the output of what nikhil told me:

```
ubuntu@ubuntu:~$ cat /etc/mtab
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw,mode=0755 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw,mode=0755 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda7 swap swap defaults 0 0
ubuntu@ubuntu:~$ 

```

so what do you think?

---

### Post by bhadotia on 2008-04-06
plz  people' reply i need help , otherwise i'll have to reinstall my linux , i'll lose all my data , i don't want that . PLEASE REPLY

---

### Post by Duck2006 on 2008-04-06
Some reading on grub that may help.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by bhadotia on 2008-04-07
alright people i've tried alot of things . but i still can't boot ubuntu . stIll the same error 15 is showing up . i tried reinstalling my linux but when the partioner shows up it , the only option it gives is to use the entire disk and is not showing any of my partions also (but i still have my win xp and lin installed). 
 if nikhil is here , dude i've posted The output of commands you told me a day ago , so when are you gonna reply. 


NOW  I'M COMPLETELY FRUSTRATED. 



IF THERE IS ANY ONE HERE WHO KNOWS ABOUT LINUX BOOTING PROBLEMS AND ERROR15 [COLOR="Red"]PLEASE GO THROUGH THIS THREAD THOROUGHLY[/COLOR]


:(:(:(:(:(:confused:


I WILL GO CRAZY!

---

### Post by anjilslaire on 2008-04-07
demanding people to help you of their own free will and generosity won't get you far. These aren't paid support forums...

And quit shouting, please. Its rude.

---

### Post by jkeyes0 on 2008-04-07
> **bhadotia said:**
> alright people i've tried alot of things . but i still can't boot ubuntu . stIll the same error 15 is showing up . i tried reinstalling my linux but when the partioner shows up it , the only option it gives is to use the entire disk and is not showing any of my partions also (but i still have my win xp and lin installed). 
 if nikhil is here , dude i've posted The output of commands you told me a day ago , so when are you gonna reply. 


NOW  I'M COMPLETELY FRUSTRATED. 



IF THERE IS ANY ONE HERE WHO KNOWS ABOUT LINUX BOOTING PROBLEMS AND ERROR15 [COLOR="Red"]PLEASE GO THROUGH THIS THREAD THOROUGHLY[/COLOR]


:mad::mad::mad::mad::mad::mad:::confused:


I WILL GO CRAZY!


when you reinstalled XP, did you delete all the partitions and let XP format it however it wanted to? It sounds like you may have inadvertently allowed the XP install to use one of your Linux partitions to put XP on, and that's why Grub would be giving a "not found" (error 15).

---

### Post by bhadotia on 2008-04-07
Sorry , sir but its just that i'm too frustrated (having lost my ubuntu): i was actually not shouting (those capitals were actually an expression of my desperate plea) :(
I again say SORRY! if any body was irritated (my intention was not at all what the above person thought it to be):(

i BEG all the generous and helpfull members of this  forum ,to atleast post replys (even if they do not concern the present issue(grub , that is )) so that it may help me atleast feel better(i'm really frustrated):(

again, soorrrrrryyyyy.:(:(:(

---

### Post by bhadotia on 2008-04-07
no , i just formatted the partion on which my old win xp was installed and then installed the windows (on that partion only). 

besides i have a partion manager software (in xp) which is showing the linux partions as they are.

I may tell you i have even tried booting using super grub cd . but even that does not seem to work (though i've not tried my hand at all the options given there in yet ).

---

### Post by bhadotia on 2008-04-07
alright people i've decided to reinstall my linux; i will formatt my linux partions and reinstall ubuntu on them ;any advices on how to do it the best way so that such a problem doesn't occur again .:(

---

### Post by bhadotia on 2008-04-07
OK I'M  installing it now ,going offline (although there was no reply from ur side, any way thank you so much):popcorn:

---

### Post by lswest on 2008-04-07
Yeah, basically you have to re-install grub because XP install its own bootloader.  there's a how-to i wrote in my sig (second line)

---

### Post by bhadotia on 2008-04-07
actually i have reinstalled my ubuntu . i will try never to install windows again. and hopefully   with the help of good friends like you people(members of the community) , soon i will get as comfortable with ubuntu as with windows.:popcorn:

---

### Post by adrian15 on 2008-04-07
> **bhadotia said:**
> alright I've installed grub but it is not booting ubuntu (windows is booting), the following message is coming:

  error15: file not found.

what does that mean?

[There was something you should have known.](http://www.supergrubdisk.org/wiki/Howto_Fix_Grub#One_thing_you_should_know).

Maybe running fsck from a live cd might have helped.

adrian15

---

### Post by bhadotia on 2008-04-07
well any way thanks for the quick reply:lolflag:

---

### Post by anjilslaire on 2008-04-07
Glad you got it all sorted out.
Going forward, it may help to install /home to its own partition. That way, you can reinstall the OS in "/" as often as you like, without losing your settings or preferences/files.

---

### Post by bhadotia on 2008-04-07
yes i have done that. thanx.

---

