---
title: "failure to restore grub"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2006-04-01
Hi all! after failing at various attempts trying to  change the menu list to include mepis (which is on a second drive) onto my dual boot XP & Ubuntu drive Master drive) I lost the ability to boot. Anyway I have fixed the mbr with XP cd. Now I have xp but not ubuntu to boot to. I know everything is still there I just need to know how to boot back into ubuntu. I am reluctant to reinstall ubuntu as I am happy with the settings I have made.
Any help would be appreciated.
Thanks

---

### Post by KansasJoe on 2006-04-01
mepis has a live cd in which you can go load it up and go somewhere in there...think it's os (looks like a wrench i believe) and in there it gives you an option to reinstall grub

---

### Post by Sutekh on 2006-04-01
[QUOTE=Sbarton]I am reluctant to reinstall ubuntu as I am happy with the settings I have made.[/QUOTE]Then please don't.  Ubuntu can be rescued!

Try the Mepis LiveCD or you can also try the methods from the Ubuntu Wiki page dedicated to this problem.

[Ubuntu Wiki - Recovering Ubuntu After Installing Windows](wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Sbarton on 2006-04-02
Thanks for replies and sorry for delay of reply.I tried the Mepis CD but was unable to get to Ubuntu, only options were Mepis & XP it did load grub but only as above. Since then I have restored XP mbr and still have mepis on second HDD (slave) but still unable to install grub for ubuntu. If I restore grub it restores to the last version which was Mepis and not Ubuntu.](*,) 

As I do not wish to double post this post is beggining to look similar to another of my posts' Boot change needed' so I apologise now.
Thanks

---

### Post by belikralj on 2006-04-02
Try editing menu.lst again if mempis is linux and it uses grub (which I would imagine it would) you only need to modify it to include Ubuntu kernel and coppy some files to boot loader.

heres a usefull link on dual booting various systems:
[http://librenix.com/?page=Dual-boot](http://librenix.com/?page=Dual-boot)

heres one for multiple linux distro booting:
[http://os.newsforge.com/os/04/12/21/1852209.shtml](http://os.newsforge.com/os/04/12/21/1852209.shtml)

good luck! hope it helps.

---

### Post by Sutekh on 2006-04-02
[QUOTE=Sbarton]Thanks for replies and sorry for delay of reply.I tried the Mepis CD but was unable to get to Ubuntu, only options were Mepis & XP it did load grub but only as above. Since then I have restored XP mbr and still have mepis on second HDD (slave) but still unable to install grub for ubuntu. If I restore grub it restores to the last version which was Mepis and not Ubuntu.](*,) 

As I do not wish to double post this post is beggining to look similar to another of my posts' Boot change needed' so I apologise now.
Thanks[/QUOTE]
Can you get into MEPIS?  If so we need to locate and mount the partition with Ubuntu.  Then we can determine the kernel image and then edit the GRUB menu so that you can boot Windows/MEPIS and Ubuntu.

So if you can boot into MEPIS, please do so.  

Firstly how familiar are you with Linux commands and GRUB?  If none of this makes sense, we can step through it.


 - Do you know the partition name (/dev/hda1 for example) of Ubuntu?  Can you mount that partition?  

 - If you can mount the Ubuntu partition, can you list the contents of the Ubuntu partition's /boot folder?

 - Finally can you list the contents of the device.map?  This file will be on MEPIS's partition, since MEPIS's version of GRUB is booting.  The file is located in /boot/grub/device.map.  The file will have contents similar to this```
(hd0) /dev/hda
(hd1) /dev/hdb
```
 - The file contains the information that GRUB uses to 'map' device locations, such as /dev/hda1, to a format that GRUB likes, such as (hd0,0)


 - With the location of the Ubuntu partition and the contents of its' /boot partition, could you then edit the GRUB menu.lst?  Remebering that the menu is on MEPIS's /boot/grub/menu.lst file.

 - The stock standard entry for Ubuntu looks like this.  You would need to change the bold where neccessary.
```
title Ubuntu, kernel 2.6.12-9-386
**root (hd1,0)**
kernel **/boot/vmlinuz-2.6.12-9-386** **root=/dev/hdb1** ro quiet splash
initrd **/boot/initrd.img-2.6.12-9-386**
savedefault
boot

```
 - the **title** is just a description of the GRUB entry

 - the **root** is the location of the root filesystem (hdb1 -> hd1,0), or whatever s contained in the device.map

 - the **kernel** refers to the kernel image.  It is found in /boot and you must make sure you get the filename correct.  The **root=/dev/hdb1** is also important to get right

 - the **initrd** refers to the initial ramdisc.  Again found in /boot, make sure the filename is correct for the kernel you want to boot



 - I hope you can make some sense of this, just ask if something is unclear.

---

### Post by Jose Catre-Vandis on 2006-04-02
Sutekh has the message, but my experiences might also help

[http://www.ubuntuforums.org/showthread.php?p=885014#post885014](http://www.ubuntuforums.org/showthread.php?p=885014#post885014)

---

### Post by Sbarton on 2006-04-03
Thank you both for taking time and trouble to post your suggestions this has given me a lot of food for thought. When I hit problems( and I will) I'll be back.
regards.
:confused: Oops! I think I posted this somewhere else to.Sorry

---

### Post by Sbarton on 2006-04-04
[QUOTE=Sutekh]Can you get into MEPIS?  If so we need to locate and mount the partition with Ubuntu.  Then we can determine the kernel image and then edit the GRUB menu so that you can boot Windows/MEPIS and Ubuntu.

So if you can boot into MEPIS, please do so.  

Firstly how familiar are you with Linux commands and GRUB?  If none of this makes sense, we can step through it.


 - Do you know the partition name (/dev/hda1 for example) of Ubuntu?  Can you mount that partition?  

 - If you can mount the Ubuntu partition, can you list the contents of the Ubuntu partition's /boot folder?

 - Finally can you list the contents of the device.map?  This file will be on MEPIS's partition, since MEPIS's version of GRUB is booting.  The file is located in /boot/grub/device.map.  The file will have contents similar to this```
(hd0) /dev/hda
(hd1) /dev/hdb
```
 - The file contains the information that GRUB uses to 'map' device locations, such as /dev/hda1, to a format that GRUB likes, such as (hd0,0)


 - With the location of the Ubuntu partition and the contents of its' /boot partition, could you then edit the GRUB menu.lst?  Remebering that the menu is on MEPIS's /boot/grub/menu.lst file.

 - The stock standard entry for Ubuntu looks like this.  You would need to change the bold where neccessary.
```
title Ubuntu, kernel 2.6.12-9-386
**root (hd1,0)**
kernel **/boot/vmlinuz-2.6.12-9-386** **root=/dev/hdb1** ro quiet splash
initrd **/boot/initrd.img-2.6.12-9-386**
savedefault
boot

```
 - the **title** is just a description of the GRUB entry

 - the **root** is the location of the root filesystem (hdb1 -> hd1,0), or whatever s contained in the device.map

 - the **kernel** refers to the kernel image.  It is found in /boot and you must make sure you get the filename correct.  The **root=/dev/hdb1** is also important to get right

 - the **initrd** refers to the initial ramdisc.  Again found in /boot, make sure the filename is correct for the kernel you want to boot



 - I hope you can make some sense of this, just ask if something is unclear.[/QUOTE]
Here I am again! I have switched drives .Now Mepis is master.XP and Ubuntu are on the second (slave) drive .Booting into mepis I have obtained the following, Device map shows : (hd0).  /dev/hda
The following attachments show the mepis menu list and mepis fdisk details.

How can i progress from here?
Thanks

---

### Post by Sutekh on 2006-04-04
Okay thats great!

So do you want to keep the hard disc with MEPIS the master?  And do you want to use MEPIS's bootloader?

I will continue assuming that this is what you wish to do.  If it's not then it won't be too hard to swap things around.

Firstly let's change the device.map to include the second hard disc
```
(hd0) /dev/hda
(hd1) /dev/hdb
```
Now **/dev/hdb**, which contains Ubuntu and Windows is known to GRUB as **hd1**.


Next you need to mount the Ubuntu main partition (most likely /dev/hdb2), so you can do this by
```
sudo umount /dev/hdb2
sudo mkdir /media/ubuntu
sudo mount /dev/hdb2 /media/ubuntu
```
Then copy Ubuntu's GRUB entry out of it's own menu and into MEPIS's menu.  The GRUB menu entry can be found by
```
cat /media/ubuntu/boot/grub/menu.lst
```
Copy that into MEPIS's GRUB menu.  You will need to edit it a little so that the locations are correct.  

It might look something like this when you are done editing it
```
title Ubuntu, kernel 2.6.12-9-386
**root (hd1,1)**
kernel /boot/vmlinuz-2.6.12-9-386 **root=/dev/hdb2** ro quiet splash
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot
```
 - **root (hd1,1)** because we mapped /dev/hdb to hd1, and (hd1,**1**), because you count the partitions from 0.  So /dev/hdb1 is (hd1,0), /dev/hdb2 is (hd1,1), and so on.

You can post the entire menu here when you are done, if you like.

You can also add the entry for Windows too, it should be like this one
```
title		Microsoft Windows XP
**root		(hd1,0)**
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```
 - the **map** part is a little GRUB trickery that fools Windows into thinking that it is the master drive (bascially by temporarily mapping hd0 to hd1 and vice versa)

See how you go!

---

### Post by Sbarton on 2006-04-05
[QUOTE=Sutekh]Okay thats great!

So do you want to keep the hard disc with MEPIS the master?  And do you want to use MEPIS's bootloader?

I will continue assuming that this is what you wish to do.  If it's not then it won't be too hard to swap things around.

Firstly let's change the device.map to include the second hard disc
```
(hd0) /dev/hda
(hd1) /dev/hdb
```
Now **/dev/hdb**, which contains Ubuntu and Windows is known to GRUB as **hd1**.


Next you need to mount the Ubuntu main partition (most likely /dev/hdb2), so you can do this by
```
sudo umount /dev/hdb2
sudo mkdir /media/ubuntu
sudo mount /dev/hdb2 /media/ubuntu
```
Then copy Ubuntu's GRUB entry out of it's own menu and into MEPIS's menu.  The GRUB menu entry can be found by
```
cat /media/ubuntu/boot/grub/menu.lst
```
Copy that into MEPIS's GRUB menu.  You will need to edit it a little so that the locations are correct.  

It might look something like this when you are done editing it
```
title Ubuntu, kernel 2.6.12-9-386
**root (hd1,1)**
kernel /boot/vmlinuz-2.6.12-9-386 **root=/dev/hdb2** ro quiet splash
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot
```
 - **root (hd1,1)** because we mapped /dev/hdb to hd1, and (hd1,**1**), because you count the partitions from 0.  So /dev/hdb1 is (hd1,0), /dev/hdb2 is (hd1,1), and so on.

You can post the entire menu here when you are done, if you like.

You can also add the entry for Windows too, it should be like this one
```
title		Microsoft Windows XP
**root		(hd1,0)**
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```
 - the **map** part is a little GRUB trickery that fools Windows into thinking that it is the master drive (bascially by temporarily mapping hd0 to hd1 and vice versa)

See how you go![/QUOTE]

Thanks for reply, Yes I shall keep Mepis at present as Master , with XP and Ubuntu on second drive (slave). If you do not mind taking this thing one step at a time, this would help me. Now as for the instruction regarding device map, does device map have to be open to continue with the code: or is it typed into a terminal and does it need to be saved and how? Also on trying the next step to unmount hdb2 (in terminal) I received 'sudo umount command not found'
Let's stop at this point and I will look forward to your reply, if you have the patience.

---

### Post by Sutekh on 2006-04-05
Sure one step at a time is fine by me.  I apologise if I was a bit too brief.

Alright first lets mount Ubuntu and get the entry for GRUB off the partition.

You have already run
```
sudo fdisk -l
```so we know that on /dev/hdb there are two Linux partitions; /dev/hdb2 and /dev/hdb5.  We'll assume the /dev/hdb2 is Ubuntu, if not then just change all the '2's for '5's.

So first, the error you got with the mount command.  Are you sure that you used **umount** and not **unmount**?  

Also I forgot to think MEPIS not Ubuntu.  I don't think MEPIS uses sudo, does it?   So open your terminal application (Konsole?) and switch to root with
```
su
```
Then lets mount Ubuntu


 - First unmount the /dev/hdb2 partition, I want to do this so we can control where it gets mounted.  ```
umount /dev/hdb2
```
 - Second make a folder to mount Ubuntu to.```
mkdir /mnt/ubuntu
```
 - Last mount /dev/hdb2 to the folder /mnt/ubuntu.
```
mount /dev/hdb2 /mnt/ubuntu
```
Easy.


OK next lets find out what the menu entry for Ubuntu is in GRUB.  So we are looking at the menu.lst on the Ubuntu partition.
```
kwrite /mnt/ubuntu/boot/grub/menu.lst
```
Then identify the entry for Ubuntu, it will look very similar to the one I posted earlier.  

Copy and paste that here, and we'll go on.

---

### Post by Sbarton on 2006-04-05
[QUOTE=Sutekh]Sure one step at a time is fine by me.  I apologise if I was a bit too brief.

Alright first lets mount Ubuntu and get the entry for GRUB off the partition.

You have already run
```
sudo fdisk -l
```so we know that on /dev/hdb there are two Linux partitions; /dev/hdb2 and /dev/hdb5.  We'll assume the /dev/hdb2 is Ubuntu, if not then just change all the '2's for '5's.

So first, the error you got with the mount command.  Are you sure that you used **umount** and not **unmount**?  

Also I forgot to think MEPIS not Ubuntu.  I don't think MEPIS uses sudo, does it?   So open your terminal application (Konsole?) and switch to root with
```
su
```
Then lets mount Ubuntu


 - First unmount the /dev/hdb2 partition, I want to do this so we can control where it gets mounted.  ```
umount /dev/hdb2
```
 - Second make a folder to mount Ubuntu to.```
mkdir /mnt/ubuntu
```
 - Last mount /dev/hdb2 to the folder /mnt/ubuntu.
```
mount /dev/hdb2 /mnt/ubuntu
```
Easy.


OK next lets find out what the menu entry for Ubuntu is in GRUB.  So we are looking at the menu.lst on the Ubuntu partition.
```
kwrite /mnt/ubuntu/boot/grub/menu.lst
```
Then identify the entry for Ubuntu, it will look very similar to the one I posted earlier.  

Copy and paste that here, and we'll go on.[/QUOTE]

Thanks for your patience. Having followed your instructions this is the menu list  on attachment, however no reference to ubuntu, whichis on the slave. drive

---

### Post by Sbarton on 2006-04-05
Ignore post.Error with attachment. Correct one will follow

---

### Post by Sbarton on 2006-04-05
[QUOTE=Sbarton]Thanks for your patience. Having followed your instructions this is the menu list  on attachment, however no reference to ubuntu, whichis on the slave. drive[/QUOTE]
This is the result of the menu list on attachment, as you can see no ref: to ubuntu? It is still on slave drive!

---

### Post by ferebee on 2006-04-05
[QUOTE=Sbarton]This is the result of the menu list on attachment, as you can see no ref: to ubuntu? It is still on slave drive![/QUOTE]

Are you sure this is from Ubuntu's filesystem folders?

This looks like Mepis's standard menu list. You need to find  Ubuntu's menu list.
I see by your Mepis screenshot that you've got Kwikdisk; its the three boxes stacked
on top of each other to the left of the clock. Right click that and select hdb2.
Konqueror should mount the drive and open a window showing it's contents.
Open the Boot folder, then the Grub folder. Ubuntu's menu list should be there.
If this isn't it, try hdb5.

---

### Post by Sbarton on 2006-04-05
[QUOTE=ferebee]Are you sure this is from Ubuntu's filesystem folders?

This looks like Mepis's standard menu list. You need to find  Ubuntu's menu list.
I see by your Mepis screenshot that you've got Kwikdisk; its the three boxes stacked
on top of each other to the left of the clock. Right click that and select hdb2.
Konqueror should mount the drive and open a window showing it's contents.
Open the Boot folder, then the Grub folder. Ubuntu's menu list should be there.
If this isn't it, try hdb5.[/QUOTE]

Hello again! If you look at the screenshots attached you will see that they are from hdb2 and also you will see my various failed attempts to change the boot up. Most of the menu lists are Mepis  though one is a backup of the original, which has ubuntu and mepis and windows. though it neveractually booted all 3 (if that makes ant sense)
regards

---

### Post by ferebee on 2006-04-05
[QUOTE=Sbarton]Hello again! If you look at the screenshots attached you will see that they are from hdb2 and also you will see my various failed attempts to change the boot up. Most of the menu lists are Mepis  though one is a backup of the original, which has ubuntu and mepis and windows. though it neveractually booted all 3 (if that makes ant sense)
regards[/QUOTE]

If you are **absolutely **sure that Hdb2 is where Ubuntu is installed,and you
are using this kernel version, then we can try cutting and pasting this to Mepis' grub menu.lst file, as Sutekh suggested. 

```
title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot
```

This **must** go into Mepis's menu.lst, not Ubuntu's, because 
Mepis' grub is doing the the booting.

Have you looked at those other partitions just to be sure which is Ubuntu?
If you look in the home folder, does the user folder have your Ubuntu user name?
Are there files you know you downloaded or saved with Ubuntu?

---

### Post by Sutekh on 2006-04-05
Yep good idea.  Just use Konqueror and browse to /mnt/hdb2/boot and post a screenshot.  Then we can see what kernel you have installed.

Also you still need to edit the device.map.  This must be the device.map on the MEPIS partition, not the Ubuntu one.  Open the file as root```
kwrite /boot/grub/device.map
```
and add this line
```
(hd1) /dev/hdb
```
Then once you know the proper kernel version (from the screenshot) you can add the menu entry for GRUB to MEPIS's menu.lst, just like the one ferebee and I have posted.  You can also add the Windows XP entry while you are there (its back a couple of posts).

---

### Post by Sbarton on 2006-04-06
[QUOTE=ferebee]If you are **absolutely **sure that Hdb2 is where Ubuntu is installed,and you
are using this kernel version, then we can try cutting and pasting this to Mepis' grub menu.lst file, as Sutekh suggested. 

```
title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot
```

This **must** go into Mepis's menu.lst, not Ubuntu's, because 
Mepis' grub is doing the the booting.

Have you looked at those other partitions just to be sure which is Ubuntu?
If you look in the home folder, does the user folder have your Ubuntu user name?
Are there files you know you downloaded or saved with Ubuntu?[/QUOTE]


The screenshot shows hdb2 and original ubuntu bootlist (which was on hd0 master at the time, it also shows xp. On checking the Home folder I see nothing (weird). I have added the (hd1) entry as Sutekh suggested to mepis device map. I suppose now the next step is to copy your suggested entry for ubuntu to mepis bootlist? ( I have not done so as yet!)
Thanks

---

### Post by ferebee on 2006-04-06
[QUOTE=Sbarton]The screenshot shows hdb2 and original ubuntu bootlist (which was on hd0 master at the time, it also shows xp. On checking the Home folder I see nothing (weird). I have added the (hd1) entry as Sutekh suggested to mepis device map. I suppose now the next step is to copy your suggested entry for ubuntu to mepis bootlist? ( I have not done so as yet!)
Thanks[/QUOTE]

I'd say, yep add the entry that Sutekh suggested to your Mepis Grub menu.lst,
and also check your windows entry in that list and correct it to do that other little trick Sutekh
mentioned:

[QUOTE=Sutekh]You can also add the entry for Windows too, it should be like this one
Code:

title Microsoft Windows XP 
root (hd1,0) 
savedefault 
map (hd0) (hd1) 
map (hd1) (hd0) 
chainloader +1

- the map part is a little GRUB trickery that fools Windows into thinking that it is the master drive (bascially by temporarily mapping hd0 to hd1 and vice versa)[/QUOTE]

---

### Post by Sbarton on 2006-04-07
Messed up ! Have now re-installed. If you do not mind I will get back.
Many. Many thanks=D>

---

### Post by Sbarton on 2006-04-10
Success at last!:D After  a reinstall (due to my own errors) and having a broadband upgrade problem I am very happy to state I have succeeded in putting mepis on the boot menu. I must thank all those of you who have helped me along this path, also for your patience and tolerance, and of course your experience.=D> =D> 

As I had another post which began to merge with this one, I have posted my thanks on that one as well. Hope the moderators will accept that.Thanks

---

### Post by Sutekh on 2006-04-10
Okay that's great!  Well done.  Too bad you had to reinstall though.

---

