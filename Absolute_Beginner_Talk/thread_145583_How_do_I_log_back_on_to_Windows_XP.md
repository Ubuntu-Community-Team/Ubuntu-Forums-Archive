---
title: "How do I log back on to Windows XP?"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by youBun2 on 2006-03-16
I currently run Windows XP Home Edition on my desktop that was bought last February. The file system on my main and only hard drive of 200 GB is NTFS.

Yesterday a friend gave me a copy of Ubuntu (official copy from the website) and I decided to load up the Live CD. Without a result I found that perhaps it is just the Live CD and so I went ahead and started with an installation.

Using a partioning program I managed to create a 10 GB partition for Linux etc. I carried on with the install and towards the end it asked me if I wanted to have the GNU GRUB installed on my C: (with Windows XP) as to have a choice in OS when at boot-up.

Innocent me went ahead with that choice and enjoyed the first few steps at seeing Ubuntu. I managed to create myself a user account and I logged in... it froze. I then decided to restart and load up Windows XP instead. It won't load. When I select Windows XP Home Edition it has:

root (hd0,1)
savedefault
makeactive
chainloader +1

and stops. When I checked out the same boot-up process for Ubuntu, I saw that it reads:

root hd(0,2)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/sda3 ro quiet splash
intrid /boot/initrd.img-2.6.12-9-386
savedefault
boot

and obviously loads Ubuntu and allows me to log in but freezes on the centered image.

From what I can see, it appears Windows XP doesn't load up its kernal or something like that. Are there any ways I can simply log on to my Windows system?

---

### Post by youBun2 on 2006-03-16
Please people - I'm desperately in need of sorting out this problem!

---

### Post by Brunellus on 2006-03-16
[QUOTE=youBun2]Please people - I'm desperately in need of sorting out this problem![/QUOTE]
are you quite sure you didn't delete the windows partition entirely?

---

### Post by Lord Illidan on 2006-03-16
Yeah, how did you partition your harddrive?

---

### Post by CookieOrc on 2006-03-16
Give us some more specs on your system and did you install the amd64 bit version of ubuntu? 

try booting ubuntu in recovery mode. you can enter the grub menu by typing somthing like this 

```
sudo nano /boot/grub/menu.lst
```

If I remember correctly that will let you edit your grub menu. Back the original up and play with it for a bit.

---

### Post by CookieOrc on 2006-03-16
What program did you use to make to 10 gig partition and did you back up windows at all?

---

### Post by youBun2 on 2006-03-16
I used Partition Logic 0.61 to create the 10 GB partition. I made sure that Unbuntu was installing on my 10 GB partition. What someone said to me who knows about Linux is that my mistake was installing the GNU GRUB on my 190 GB parition (that runs the normal windows xp).

I would also love to know how to run those commands as I am stuck with a boot up screen and Ubuntu doesn't fully boot and I have no idea how to run the Windows XP boot-up process.

---

### Post by CookieOrc on 2006-03-16
Okay I am not an expert and do not try this unless someone else confirms this will work.

[http://www.ubuntuforums.org/showthread.php?t=76652](http://www.ubuntuforums.org/showthread.php?t=76652)

instead of mounting the linux partition make the windows parition the /
and forget about all the grub stuff...As long as the information on the windows partition it may work. Also i do not know of any othere Grub othere then the GNU grub... unless he is talking about Grub legacy or Grub 2... Or a diffrent boot loader like lilo

I DO NOT KNOW IF THIS WILL WORK... Record all the steps you take so you can always roll back if you have to...

---

### Post by youBun2 on 2006-03-16
Thank you for the suggestion but as I am looking at my desktop right now, I am just thinking to myself, "I'm sure it's more simple than this," and that I only need the boot up process for the GNU GRUB I have installed on my Windows XP Home Edition partition.

It's like having two doors. I have one key (Ubuntu) that opens the lock half way then sticks, and I have lost the other key to open the Windows door.

If it is possible for anyone who has dual OS' on their desktop/laptop and could just post their boot-up process with 'exact' information then perhaps I could give that a wizz.

---

### Post by youBun2 on 2006-03-16
Alright, so I am logged in to Ubuntu 5.10 now and I will search for the new graphics driver in a short while. My main concern at this moment in time is accessing Windows XP Home Edition.

At the moment I have two partitions; sda1 and sda2

sda1 is of 10 GB in size and has Ubuntu 5.10 on it. I also noticed it had a folder named, **dualos**, within sda1.

sda2 I am unable to access as it states I am not the Administrator? :-k

Would it be possible to DELETE the dualos folder within sda1? Would that then load up Windows XP Home Edition?

---

### Post by youBun2 on 2006-03-16
bump

---

### Post by Herman on 2006-03-16
Hello, I can't stay and help you right now, I have to go in a hurry for work and be away for a long time, but in case it will help you, there is a page about Grub bootloader in my bigpond siglink website and also another page on GAG bootloader, either of which will boot Windows for you, and there is plenty of info there and more links there too to other sources, if you have time to do some reading you should find out all you need, I hope someone else helps you though as well- I really have to go now- bye and good luck - Regards, Herman. :-D

---

### Post by sn123 on 2006-03-16
Ok, I am a newbie but I do have dual boot on my laptop (Win Xp + Ubuntu) with Grub installed. One thing could be incorrect partitioning that might have screwed up the Windows partition (I used PartitionMagic in my case and during Linux installation instructed Linux to *Not Touch My NTFS partition*). Anywez here are few things that I can think off which might help you:
First let's try to find out whether your ntfs partition is still safe and found, open a console and try the fdisk command with -l switch:
```
$ sudo fdisk -l
```
this should list you the partition table, check which one of them is of type NTFS and see whether it's got * for boot flag.
Assuming that the ntfs was /dev/hda2, try to mount it as read only using mount:
```
sudo mount /dev/hda2 /media/windows/ -t ntfs -o nls=utf8,umask=0222

```
Assuming you do have /media/windows directory (or else you can create one or mount on someother folder). Once the mounting is complete, open a file-browser and browse to the /media/windows, if you can see all the directories of the Windows then atleast you have your windows partition safe and sound :).
Let me know the results of the above two commands (pls. to paste them in your post) and we will try to take it forward from there.

Best,
S

---

### Post by youBun2 on 2006-03-17
Hello again,

Alright, I followed step 1 and that was successful.

I have found the partition which is of type NTFS and it had a * for boot flag attached to it. The NTFS was /dev/sda2.

I then went on to your next step replacing /dev/hda2 with /dev/sda1/. However, when I browse to the 'media' directory, I have:

cdrom
cdrom0
cdrom1
sda1
sda2

Now knowing that my Windows partition is on sda2 I tried to access it but it gives me this message:

Error Displaying Folder

The folder contents could not be displayed.

You do not have the permissions necessary to  view the contents of "sda2".

Thank you for your help, although I am still unsure where to go from here.

---

### Post by sn123 on 2006-03-17
[QUOTE=youBun2]Hello again,

Alright, I followed step 1 and that was successful.

I have found the partition which is of type NTFS and it had a * for boot flag attached to it. The NTFS was /dev/sda2.

I then went on to your next step replacing /dev/hda2 with /dev/sda1/. However, when I browse to the 'media' directory, I have:

cdrom
cdrom0
cdrom1
sda1
sda2

Now knowing that my Windows partition is on sda2 I tried to access it but it gives me this message:

Error Displaying Folder

The folder contents could not be displayed.

You do not have the permissions necessary to  view the contents of "sda2".

Thank you for your help, although I am still unsure where to go from here.[/QUOTE]

create a new folder under media called Windows (actually you can can call the folder anything that you like and change the mount options approriately) and follow the steps in my previous post to mount the windows partition as read only by changing reference of dev/hda2 to dev/sda2. See if you can browse the windows partition (it would be read-only). If you can then it means the windows partition is still there alive and perhaps Grub has screwed up the MBR, there could be two ways of fixing the MBR (one by running the WinXP Rescue CD and fixing the MBR and re-installing Linux/Grub) or by trying to fix the Grub using Ubuntu Live CD and/or re-installing Grub. The next course of action depends on the status of your ntfs partion...so for now just try to mount the ntfs partition and see if you can access the windows' files.

Edit: You have to mount your ntfs partition manually before you can accesss it (follow instructions in my prev. post)
 
Good luck,
S

---

### Post by youBun2 on 2006-03-17
I have a 'media' folder but within tehre I cannot create a new folder. The option is greyed out.

---

### Post by mpettitt on 2006-03-17
You will need to use a console to create a folder in media directory, since it requires administrator access.
Open a console and type

```
cd /media
mkdir windows
```

Then follow the above steps ie.

```
sudo mount /dev/hda2 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

Then:

```
cd windows
ls
```

If this lists yours windows files, they are safe and the MBR is just needing repairing. If not, then you've managed to somehow wipe your Windows partition...

---

### Post by sn123 on 2006-03-17
[QUOTE=mpettitt]
```
cd /media
mkdir windows
```
[/QUOTE]
"mkdir windows"
change it to :
```

**sudo** mkdir windows

```
and enter your password once it prompts for it.

Best,
S

---

### Post by catlett on 2006-03-17
If you want to go back to square one just reinstall windows from a backup. Either use a backup that you created or use your recovery disks that came with your computer. When I messed up an install I just did a backup and what happens is it will erase and reformat your windows partition. This will get rid of grub. When it reinstalls your windows system it will install the windows boot manager and you will go back to your regular boot process. The only issue will be if you didn't make your own backup, the recovery disks will erase evewything and your computer will be like when you just purchased it. Don't give up on Ububtu though. Your 10 gig partition will be there when your recovery is done and you can try a more informed install.Sorry about your problem, hope you have good luck with the recovery.

---

### Post by Xecuter on 2006-03-17
Sorry, didn't notice the secound page.

^what they said!

---

### Post by sn123 on 2006-03-17
[QUOTE=catlett]If you want to go back to square one just reinstall windows from a backup. Either use a backup that you created or use your recovery disks that came with your computer. When I messed up an install I just did a backup and what happens is it will erase and reformat your windows partition. This will get rid of grub. When it reinstalls your windows system it will install the windows boot manager and you will go back to your regular boot process. The only issue will be if you didn't make your own backup, the recovery disks will erase evewything and your computer will be like when you just purchased it. Don't give up on Ububtu though. Your 10 gig partition will be there when your recovery is done and you can try a more informed install.Sorry about your problem, hope you have good luck with the recovery.[/QUOTE]

You don't have to reinstall the entire windows if only your MBR is messed up, in Windows there is a command to just fix the MBR (fixmbr in recover console) but we first need to find out whether the ntfs partition is still accessible or not.
Here are step by step guide for all the steps that have been mentioned in previous posts:
```

1) Open a console terminal
2) cd to media: $ cd /media
3) creata windows directory: $ sudo mkdir windows
4) mount the partition: $ sudo mount /dev/hda2 /media/windows/ -t ntfs -o nls=utf8,umask=0222
5) Open the file browser (nautilus) the way you normally do and browse to /media/windows directory, check if all the files and folders of windows are available or not.

```
By the way, do you have the Windows XP installation CDs?

S

---

### Post by youBun2 on 2006-03-17
Hm... I have followed those procedures and within terminal I can see my Windows files. This proves that my Windows XP files are still readable.

Thank you for the help everyone, this is great support!

Keep it coming!

---

### Post by sn123 on 2006-03-17
[QUOTE=youBun2]Hm... I have followed those procedures and within terminal I can see my Windows files. This proves that my Windows XP files are still readable.

Thank you for the help everyone, this is great support!

Keep it coming![/QUOTE]

The easiest way that I can think off is to boot from the Windows XP CD, press F12 or r when it says "Welcome..." to go into recovery console and try fixmbr command (it should fix the MBR and overwrite GRUB with XP Boot Loader), check on the net for more details on the fixmbr command (and the map command), once the MBR is fixed you should be able to boot into XP and can try reinstalling grub once everything looks fine or better still use this as your last option and wait for someone else to come with a better solution :).

Good luck,
S

---

### Post by dbcummings on 2006-03-17
One thing that is great about Ubuntu/Kubuntu (and other distros) is that as long as you leave the NTFS partition alone you should be able to throw in the installation CD, manually delete all Linux paritions, and reinstall (that is if you don't mind losing your ubuntu installation).  I've done this several times when first trying to get my partitions configured correctly.  I played with a fat32 share parition I was trying to create inside Windows and it srewed up GRUB.  I wiped out all the Linux partitions and had the installation automatically parition and install it.  This  correct the GRUB problem and I was able to access both OSs. If fixmbr doesn't work, I would try this.  When you get back into Windows, I recommend getting an external drive and dumping all your important data onto it.  Then you can install away.  Then, at least, if the install goes badly all you have to do is reinstall the OS and you don't lose your data.  I've now wiped my Windows partiion and only use Kubuntu on my desktop.  I have a dual boot on my laptop while I'm finishing up school because I am working with Microsoft software in my networking and web design classes.  After that, good bye Microsoft!

---

### Post by youBun2 on 2006-03-18
Whilst putting the Windows XP Home Edition installation CD in my computer it still means I have to get the CD. My computer never came with a distribution of Windows XP HE as in I got the CD with it on, my computer came with it pre-installed so that when I turned it on for the first time it would run the installation process.

My basic problem at the moment before I continue with my plan of dual booting two OS's is that I cannot boot Windows XP HE because the GRUB seems to have overwritten what would be my Windows XP boot process, or not included it within the GRUB installation/current version of GRUB. My distinct plan of action is that now I have backed up vital work and files using a DVD+RW I can re-install Windows XP but this time Professional Edition and during that installation create two partitions to then use one for Ubuntu, and the bigger partition for Windows XP PE.

I prefer Windows XP to Ubuntu in terms of how compatible that particular OS is with OS X. I find that compatibility between OS X and Linux in general is not up to par. Linux also can't burn certain file types where as both OS X and XP can. These cons. are what make me prefer XP and OS X over Linux as a whole. Whilst I enjoy using Ubuntu, I haven't particularly had a good run of it up to yet. I only seem to be logging on now to actually fix my system as apposed to learning about it.

Is there any where I can possibly find a tutorial at how I can replace my current GRUB with the original Windows XP HE boot process?

---

### Post by sn123 on 2006-03-18
[QUOTE=youBun2]Whilst putting the Windows XP Home Edition installation CD in my computer it still means I have to get the CD. My computer never came with a distribution of Windows XP HE as in I got the CD with it on, my computer came with it pre-installed so that when I turned it on for the first time it would run the installation process.

Is there any where I can possibly find a tutorial at how I can replace my current GRUB with the original Windows XP HE boot process?[/QUOTE]

You would need the XP Installation CDs to fix the MBR (ie remove Grub from it), just search on the keyword "fixmbr xp" on google and should have some MS link as to how to go about doing it. Till then try this so see if it allows you to boot XP from grub:
When grub menu shows up press some key (I cannot recollect which one it is, the grub menu might have a help link for that) to goto the grub menu. And then try these set of commands to load up XP:
```

grub> rootnoverify (hd0,1)
grub> makeactive
grub> chainloader +1


```
Also can you post the contents of your device.map file?
```

$ cat /boot/grub/device.map

```

Best,
S

---

### Post by localzuk on 2006-03-18
> I prefer Windows XP to Ubuntu in terms of how compatible that particular OS is with OS X. I find that compatibility between OS X and Linux in general is not up to par. Linux also can't burn certain file types where as both OS X and XP can. These cons. are what make me prefer XP and OS X over Linux as a whole. Whilst I enjoy using Ubuntu, I haven't particularly had a good run of it up to yet. I only seem to be logging on now to actually fix my system as apposed to learning about it.

I assume you speak of mac os x? If so, OS X is much closer to Linux than Windows XP is as it is built on a BSD base - and therefore is a *nix system.

What do you mean by 'linux can't burn certain types of files'? Linux is only as good as the software you supply it with - as is any other OS. Windows comes with a *very* basic cd-writer software as standard, as does OS X. In linux and OS X you have a wide choice of free software packages to do the burning for you - whereas Windows will have a package that came with your cd-writer.

As people have said, you need a windows cd in order to fix your mbr. If you have a 'pre-installed' system, which doesn't have a cd-rom, you will need to contact your manufacturer and demand a cd with the system on (they are legally required to provide one). This normally comes in the form of an emergency system restore disk - however, this may not be much use to you.

If you have *any* windows XP disk this will do you - just put it in and boot it,  go into recovery mode as and when it asks you, and type 'fixmbr'.

---

### Post by youBun2 on 2006-03-18
[QUOTE=sn123]
Also can you post the contents of your device.map file?[/QUOTE]
(hd0)   /dev/sda

---

### Post by sn123 on 2006-03-18
[QUOTE=youBun2](hd0)   /dev/sda[/QUOTE]
did you try the commands from grub console in my last post (the only difference between them and the one which grub has by default is the **rootnoverify** which makes grub not to mount the ntfs partition before invoking the xp boot loader), give it a shot it just might work.


S

---

### Post by Herman on 2006-03-18
sn123 is doing a good job (you press 'c' at the Grub Menu for the Grub command line interface) and you should be able to boot your Windows XP with those commands given by sn123 plus one more:
```
 grub> rootnoverify (hd0,1)
grub> makeactive
grub> chainloader +1
grub> boot
``` For more info on booting with Grub: [GRUB Page]("http://www.users.bigpond.net.au/hermanzone/p15.htm")

If the operating system is bootable you should be able to boot it with Grub if you try hard enough. Otherwise you should be at least able to boot it with GAG immediately with your 'System Rescue CD' if you have one. If not, you can make your won GAG CD or floppy disk or install GAG to MBR and use that. Here is more info: [GAG Boot Loader]("http://www.users.bigpond.net.au/hermanzone/p12.htm")

If you can't do anything and you just want to restore your MBR to your old 'boot sector' then you can do that with a Windows 98 boot floppy if you have no Windows XP CD, (it works as well for XP as it does for '98SE). Here is more info on returning to a Windows MBR: [Uninstall Ubuntu]("http://www.users.bigpond.net.au/hermanzone/p18.htm")
Sorry I only have time for this quick interjection, sn123 you are doing a good job, keep trying youBun2, I hope something here is helpful, :-D Regards, Herman

---

### Post by sn123 on 2006-03-18
[QUOTE=Herman]sn123 is doing a good job (you press 'c' at the Grub Menu for the Grub command line interface) and you should be able to boot your Windows XP with those commands given by sn123 plus one more:
```
 grub> rootnoverify (hd0,1)
grub> makeactive
grub> chainloader +1
grub> boot
``` For more info on booting with Grub: 
Sorry I only have time for this quick interjection, sn123 you are doing a good job, keep trying youBun2, I hope something here is helpful, :-D Regards, Herman[/QUOTE]

oops! forgot that boot was implicit from grub menu :).
Thanks for the nice words though, I am just learning the tricks of the trade ;)

Best,
S

---

