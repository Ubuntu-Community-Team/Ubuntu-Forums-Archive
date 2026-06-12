---
title: "How to dual boot to ubuntu after install?  Only XP option shows up"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by pastrami on 2007-03-07
Hey guys,
So it looks like the installation went fine with the live cd.  It got all the way to where says to reboot the computer and remove the HD.

But when it boots up it only goes to the screen where I can boot either xp or vista no option for ubuntu.

/dev/sda1 is where I'm booting xp from
/dev/sda2
     /dev/sda9 is where the root was installed.

Any suggestions?

---

### Post by Drakkor on 2007-03-07
Suggestions ? yeah , get rid of Vista and Xp,lol
Naw,just kiddng, did you install ubuntu after the Vista and XP installs ?

---

### Post by pastrami on 2007-03-07
> **Drakkor said:**
> Suggestions ? yeah , get rid of Vista and Xp,lol
Naw,just kiddng, did you install ubuntu after the Vista and XP installs ?

yup, xp and vista were there already.  I actually formatted the partition that vista was sitting on and put ubuntu on.  That's why I was expecting it to show up as one of the options after the install.

---

### Post by Bachstelze on 2007-03-07
So you had Vista installed and installe dUbuntu afterwards, right ? Does the GRUB menu appear when you boot ?

---

### Post by undertherift on 2007-03-07
I would take a step back and verify that you actually did get ubuntu installed. 

On the grub selection screen (where it says you can select XP), type 'c' to take you to command line grub. 

once in there type this:
```
find /boot/grub/stage1
```

The results should tell you which hd your ubuntu was installed to, if it was installed. If that works you can proceed with this:


```
grub> root *whatever the output was from the "find" statement*
grub>kernel /boot/vmlinuz-2.6.15-28-386 root=/dev/sda9 ro single
grub>initrd /boot/initrd.img-2.6.15-28-386
grub>boot
```

Note: the kernel that you select might not be the one thats posted here.  Hit tab, and it will show you your options. 

Good luck.

---

### Post by j.miller565 on 2007-03-07
That's really weircd, wonder what's happened

---

### Post by rsambuca on 2007-03-07
I am pretty sure that you are seeing the Vista bootloader screen, not the grub loader.

You'll probably just have to reinstall grub.

---

### Post by Drakkor on 2007-03-07
Now, I'm confused....... :confused:  You said: > I actually formatted the partition that vista was sitting on and put ubuntu on
If you did that, you would have no more vista !
I understand you have ubuntu,xp,and vista, what do you want to dual boot ?
ubuntu/vista ?

---

### Post by pastrami on 2007-03-07
> **Drakkor said:**
> Now, I'm confused....... :confused:  You said: 
If you did that, you would have no more vista !
I understand you have ubuntu,xp,and vista, what do you want to dual boot ?
ubuntu/vista ?

Sorry, initially I had xp installed, then did the vista thing on a seperate partition.  Once vista was installed, I started seeing a boot menu, either XP or Vista.

I then went ahead to formatted the partition vista was installed onto and installed Ubuntu.

My goal is to have xp and ubuntu.  Sorry for the confusion!

---

### Post by pastrami on 2007-03-07
> **undertherift said:**
> I would take a step back and verify that you actually did get ubuntu installed. 

On the grub selection screen (where it says you can select XP), type 'c' to take you to command line grub. 

once in there type this:
```
find /boot/grub/stage1
```

The results should tell you which hd your ubuntu was installed to, if it was installed. If that works you can proceed with this:


```
grub> root *whatever the output was from the "find" statement*
grub>kernel /boot/vmlinuz-2.6.15-28-386 root=/dev/sda9 ro single
grub>initrd /boot/initrd.img-2.6.15-28-386
grub>boot
```

Note: the kernel that you select might not be the one thats posted here.  Hit tab, and it will show you your options. 

Good luck.

How do I get to the grub selection screen?  I'm only seeing the selection screen that I've been getting after installing vista .... hmm, seems like I goofed big time :(

---

### Post by Drakkor on 2007-03-07
> My goal is to have xp and ubuntu
Is this one hard drive or 2 ?
Can you just start all over and install XP, then Ubuntu ?
Windows must be installed first, then install Ubuntu, with the grub bootloader on the mbr,(master boot record) , so at boot up , you can choose whick OS to load.

---

### Post by Milner_07 on 2007-03-07
Sounds like you lost your XP MBR when you instlled vista so now grub is confused.

Use the XP CD to run the fixmbr command in the recovery console.

You can then reinstall GRUB and you should have a working system.

TM

---

### Post by pastrami on 2007-03-07
> **Milner_07 said:**
> Sounds like you lost your XP MBR when you instlled vista so now grub is confused.

Use the XP CD to run the fixmbr command in the recovery console.

You can then reinstall GRUB and you should have a working system.

TM

Great, I'll give that a try tonight.  Thanks for the help guys!  :)

---

### Post by pastrami on 2007-03-08
I was able to remove the vista boot selection with fixmbr and fixboot and now it looks normal.  On the XP boot screen, i get an option between XP and the recovery console.

But still after the install, I'm not seeing the ubuntu boot option.  After the install, it says, I can either run off the live cd or reboot the computer.  

Once I see that message, I click on it and then hit the reset button.  Is there anything I doing wrong that it's not seeing the boot option for ubuntu?

thanks!

---

### Post by Malac on 2007-03-08
> **pastrami said:**
> I was able to remove the vista boot selection with fixmbr and fixboot and now it looks normal.  On the XP boot screen, i get an option between XP and the recovery console.

But still after the install, I'm not seeing the ubuntu boot option.  After the install, it says, I can either run off the live cd or reboot the computer.  

Once I see that message, I click on it and then hit the reset button.  Is there anything I doing wrong that it's not seeing the boot option for ubuntu?

thanks!
Some bios have virus protection for boot sector that prevents writes, have you checked this. Probably not on if you ran fixmbr successfully
I've seen a 6 page forum thread about this exact MBR not being written issue that turned out to be this bios protection. :)

If not does the installer ask you where you want to install GRUB?

---

### Post by pastrami on 2007-03-08
> **Malac said:**
> Some bios have virus protection for boot sector that prevents writes, have you checked this.
I've seen a 6 page forum thread about this exact MBR not being written issue that turned out to be this bios protection. :)

ah, good suggestion, I'll check it out.  Any chance you have the link handy?  :)
I have a ASUS P5LD2 mobo, with an ami bios ... not sure if that's a clue or not.

---

### Post by Drakkor on 2007-03-08
> But still after the install, I'm not seeing the ubuntu boot option. After the install, it says, I can either run off the live cd or reboot the computer.

When you install you booted from the live cd ,, after installation, you are booting from the hard drive....., right ??

---

### Post by Malac on 2007-03-08
Are you trying to install Feisty as I think there is a bug in the Herd 3 install which means GRUB won't install on certain systems.

---

### Post by pastrami on 2007-03-08
yup, after the installation I'm booting of the HD and not the cd.

I checked the bios and there doesn't seem to a bios protection option there.  If it helps I'm using  amibios 0301 v02.53

Anything else I can try?

---

### Post by Drakkor on 2007-03-08
One or two drives,and where did you install grub ?  On the mbr, I hope

---

### Post by pastrami on 2007-03-08
It's on one drive, which has two mains partitions.  I'll provide a screenshot later tonight when I get home but gpart shows the following -

/dev/sda1 -- xp boot partition
/dev/sda2 -- second partition I created awhile back.
   under sda2, I have multiple partitions one of which is /dev/sda6,7,8 where ubuntu was installed.

I'm not sure where I installed grub, I just ran the installation with live cd in hopes that it did everything correctly ...

---

### Post by Drakkor on 2007-03-08
So........as long as you fix the windows mbr, you'll have to restore the grub bootloader,
do this:
1. Boot from a Live CD, like Ubuntu 
2. Open a Terminal. 
3. Type ```
sudo grub
```" which makes a GRUB prompt appear.
    like     **grub>**

4. Type ```
find /boot/grub/stage1
```. You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.

---

### Post by pastrami on 2007-03-09
Thanks for the reply --  this is the log of what I did.

grub> find /boot/grub/stage1
 (hd1,7)

grub> root (hd1,7)

grub> setup (hd1,7)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,7)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,7)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd1,7) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.
------------------------------------------
bummer, after rebooting the system and removing the cd, on the boot options I'm only getting XP and the recovery console :(

---

### Post by Drakkor on 2007-03-09
So does it boot to the grub menu now ???

---

### Post by pastrami on 2007-03-09
nope, still the same, the only boot option I'm getting is xp and the recovery console.  :(

---

### Post by Drakkor on 2007-03-09
Yeah,didn't think so..... re-read step #6
> 6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR
Re do the instructions and you want to put ```
setup (hd1)
```
to put grub on the mbr !!

---

### Post by pastrami on 2007-03-09
> **Drakkor said:**
> Yeah,didn't think so..... re-read step #6

Re do the instructions and you want to put ```
setup (hd1)
```
to put grub on the mbr !!

would this mess up my xp partition?

---

### Post by Drakkor on 2007-03-09
Actually , I was thinking that it might already be messed up, but easily fixed by doing the recovery console , fixmbr,fixboot commands. If it is messed up you will get a grub error
Try it my way and see what happens, good luck ! :)
It only affects the boot partition, not windows

---

### Post by confused57 on 2007-03-09
To determine what your partition table is, you could boot up the live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"

You don't have a USB flash drive or anything else connected that grub may have installed on?

Since you only have 1 hard drive, you'd need to install grub to the mbr by:
setup (hd0)

You might want to go through your bios(again) to see if you can find something that protects your mbr from anything other than Windows code(some type of virus protection).

If you've installed grub to your root partition, you might want to look at booting Ubuntu with the GAG bootloader:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

The Super Grub Disk is also capable of booting Windows or Linux, see index of the above website.

---

### Post by pastrami on 2007-03-09
> **confused57 said:**
> To determine what your partition table is, you could boot up the live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"

You don't have a USB flash drive or anything else connected that grub may have installed on?

Since you only have 1 hard drive, you'd need to install grub to the mbr by:
setup (hd0)

You might want to go through your bios(again) to see if you can find something that protects your mbr from anything other than Windows code(some type of virus protection).

If you've installed grub to your root partition, you might want to look at booting Ubuntu with the GAG bootloader:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

The Super Grub Disk is also capable of booting Windows or Linux, see index of the above website.

This is what I get if I type - fdisk -l

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb2   *           2       24792   199133707+   f  W95 Ext'd (LBA)
/dev/hdb5               2       11737    94269388+   7  HPFS/NTFS
/dev/hdb6           11738       24792   104864256    7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10327    82951596    7  HPFS/NTFS
/dev/sda2           10328       30401   161244405    f  W95 Ext'd (LBA)
/dev/sda5           10328       16528    49809501    7  HPFS/NTFS
/dev/sda6           16529       17038     4096543+  83  Linux
/dev/sda7           17039       17165     1020096   82  Linux swap / Solaris
/dev/sda8           17166       17594     3445911   83  Linux
/dev/sda9           17595       30401   102872196    7  HPFS/NTFS

---

### Post by confused57 on 2007-03-09
> Drakkor was correct by suggesting to setup (hd1) to install grub to the sda mbr, the only problem would be you would need to set your bios to boot first to sda, however grub would recognize this drive as hd0...This would require manually editing your /boot/grub/menu.lst & changing all occurences of hd1 to hd0...See what happens by booting first to your hdb.

Try booting your IDE drive first, just to see if you get a grub menu...sometimes grub incorrectly "guesses" where to install.  

If you were successful in installing grub to your sda mbr & get a grub menu when you boot first to sda...highlight the Ubuntu entry, press "e" to edit, then change root from (hd1,7) to (hd0,7), then press "b" to boot...this is dependent on grub being installed to your sda mbr.  The relevant entry to change for your root is from hd1 to hd0, leave the partition as is,  e.g. (hd1,6) to (hd0,6).  This change is temporary, but you can make it permanent in your /boot/grub/menu.lst.

See this post for editing your menu.lst:
[http://www.ubuntuforums.org/showpost.php?p=2271759&postcount=8](http://www.ubuntuforums.org/showpost.php?p=2271759&postcount=8)

---

### Post by pastrami on 2007-03-09
yup, I have 2 drives, but the main boot drive is on sda2 and the partition that ubuntu was installed on is on sda2.  The bios is set to boot of the sda1 drive as well.  

I guess my question is why would the grub be installed on hdb instead?  Nevertheless, I'll try both suggestions later tonight.

Any particular instructions on how to edit menu.lst, can I just do it in vi via the terminal?  thanks in adv.

---

### Post by confused57 on 2007-03-09
> **pastrami said:**
> yup, I have 2 drives, but the main boot drive is on sda2 and the partition that ubuntu was installed on is on sda2.  The bios is set to boot of the sda1 drive as well.  

I guess my question is why would the grub be installed on hdb instead?  Nevertheless, I'll try both suggestions later tonight.

Any particular instructions on how to edit menu.lst, can I just do it in vi via the terminal?  thanks in adv.

I edited my last reply, hopefully this helps.   Meant to make a separate reply after yours, but kind of got in a hurry.

---

