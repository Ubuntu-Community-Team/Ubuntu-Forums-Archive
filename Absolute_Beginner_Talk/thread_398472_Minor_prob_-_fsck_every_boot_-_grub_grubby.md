---
title: "Minor prob - fsck every boot - grub grubby"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by freebird54 on 2007-04-01
For some unknown reason, THIS (new) install of Edgy insists on running fsck on every boot up - including on the Windows partition that only sits there as an image for backup purposes.  I am not a huge fan of waiting...  Any suggestions?  (I am pretty sure the other install only ran it every 30th or so)

Also - when installing Grub - it apparently now tells it find menu.lst on the NEW install, rather than the old one - can it be changed back, and let me do the editing to allow the new one to be chosen?

Thanks in advance for any enlightenment :)

---

### Post by Herman on 2007-04-01
> For some unknown reason, THIS (new) install of Edgy insists on running fsck on every boot up - including on the Windows partition that only sits there as an image for backup purposes. I am not a huge fan of waiting... Any suggestions? (I am pretty sure the other install only ran it every 30th or so)Hello freebird54,
 That's probably a sign that something is wrong, and it seems to be something that isn't getting fixed by the regular filesystem checks. Any other clues? Have any of your filesystems, in other partitions been formatted and re-installed lately? (Windows in particular?) ...and if so, have you updated your /etc/fstab? Or, it is saying maybe "the boot sector is not the same as its backup"? That is another common cause of this type of symptom. Would this be a new hard disk or a fairly old one?
If it's your ext3 partitions that need cleaning up you can do that most easily with a [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php"), just boot GParted and right-click on the partition and click 'check'.
Or, from a Ubuntu 'Desktop' Live CD, enter a command something like this one on the unmounted filesystem, ```
sudo e2fsck -C0 -p -f -v /dev/hda2
```(where the partition containing the filesystem is /dev/hda2 and it's an ext3 filesystem).
> Also - when installing Grub - it apparently now tells it find menu.lst on the NEW install, rather than the old one - can it be changed back, and let me do the editing to allow the new one to be chosen? You can easily do that, just re-install Grub. When you do so, re-install grub *from* your old installation to MBR, here's a link,[ reinstall Grub from a grub shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")
Then just add a [configfile boot entry]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile") to your old system's menu.lst. I use those all the time. It means each operating system can update its own menu.lst, so you won't need to do it manually when a new kernel is installed during an update.

If you're still not sure what to do just ask more questions and I or someone will elaborate.
Regards, Herman

---

### Post by freebird54 on 2007-04-01
It's an older drive - it has been Win ME, XP, XP Pro (5 times), Kubuntu, Xubuntu, PCLinuxOS - currently defunct WinXP XPro (backup image) and new install of Ubuntu.  OK - will try your suggestion from Live CD.  Might just be a 'blow away' of the XP :)

As for the other - I THOUGHT that was all I had to do - but I couldn't get it to go, and the grub manual is kinda a) large b) short on examples  c) hard to find the applicable stuff because of all the neat things it can do :)   Following your suggestions will probably do it - I can frequently follow instructions.....(2 steps forward, 1 step back)

Thanks - off to reboot a few times here - I can pretend it's like Windows  :D


Wow - what a great resource those links point to!    (Thank you)10*2

---

### Post by Herman on 2007-04-01
Hmmm, I wouldn't 'blow away' anything too quick. Just wait and see what happens, we should run some tests or just observe the normal running of the machine for a while first.

You could edit your /etc/fstab file and 'comment out' the line that refers to your Windows partition. Then Ubuntu will ignore it, but you won't have the partition automatically mounted each boot-up. 
Or you could change the 2 in the <pass> column to 0, that would make Ubuntu not check it. You don't have to have Ubuntu check your Windows partition, but it's a good idea. Ubuntu can sometimes pick up problems in Windows boot sector or its backup that Windows itself can't seem to detect, or it's fancy antivirus apps.
Generally though, it's best to use Windows apps and utilities for Windows problems, and Linux programs and commands for Linux issues.

That e2fsck command should be good for your your Ubuntu filesystem, or the GParted LiveCD should be able to fix anything, but if you have NTFS it's still better to use Windows own apps, but GParted should be able to do it. It might not be the preferred option though.

If you think you might want some help with your /etc/fstab file, you can post it here,
```
sudo gedit /etc/fstab
``` and also the output from ```
ls /dev/disk/by-uuid/ -alh
``` Regards, Herman

---

### Post by freebird54 on 2007-04-01
I think I will remove the Windows partition from the 'view' of the system - as it is just a backup (I set the partition to hidden etc) and the 'real' one is on another drive and accessible.

When I ran the e2fsck commands on my 2 (/root and /home) partitions that refer to this new install, it found superblock entries from the future, and fixed them - now it appears that it does only the usual 'check and increment count' procedure - resulting in SOME saving of time.  However, it still dumps the splash screen to tell me about it, and seems slow compared to the 'other' boot - maybe it's just that much slower a drive!

I'm looking forward to cleaning up the grub mess though - but I suspect I might just 'play' a little in there with all that geat info on your page!  (Visions of configfile 'animation' from swapping grub splashes as it chains its way to the right boot disk!)

Thanks again - I guess I should mark it RESOLVED now - as the rest of the problems are all of my own making, and the resources to fix it are all at hand.

---

### Post by freebird54 on 2007-04-02
Just thought I would post a note here.  While running e2fsck fixed the problem (apparently) there was mention made of running 'CHECK' from GPartEd.  Well - I guess not this version - no such entry in the menus, or right-clickable anywhere.  It suggested in a 'features' list that check was something it could do - but no sign of anything to start it off!

Just in case it confuses anyone else...

---

### Post by mcduck on 2007-04-02
First thing I'd try is disabling fsck for windows partitions in /etc/fstab. Just change the last number in their entry lines to '0'.

---

### Post by Herman on 2007-04-02
Posted earlier by me:
>  If it's your ext3 partitions that need cleaning up you can do that most easily with a [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php"), just boot GParted and right-click on the partition and click 'check'.Okay, sorry for any confusion there, freebird54, maybe I should have emphasized more that I meant the the version of GParted that comes on its own LiveCD. It's free and it's only a small download and it's great! :) 
Ubuntu has GParted in the Ubuntu 'Desktop' Live/install CD, and we can also download and  install GParted in the hard disk install operating system too , via apt-get or synaptic. I always do. However the version of GParted I have in my Edgy install I'm typing from now is version 0.2.5 which is practically a dinosaur compared with the latest version you can get from GParted's website.
I guess it must be impossible for operating systems to keep up to date when some software is under such rapid development.
I'm downloading the latest GParted LiveCD right now, the current version of GParted is now 0.3.4-5 That version has a lot more functionality than 0.2.5 had.

Oh, wait a minute, here's a NEWS FLASH -> adrian15, the developer of [Super Grub Disk]("http://supergrub.forjamari.linex.org/") has combined his Super Grub Disk with GParted LiveCD and System Rescue CD     [Gparted Live + System Rescue + SGD 001]("http://forjamari.linex.org/forum/forum.php?forum_id=298") Now that combination of free software would have to be just about a compulsory  download for any self respecting Linux enthusiast. I started my GParted LIveCD download already, but as soon as that's finished I'm downloading adrain15's [Gparted Live + System Rescue + SGD 001]("http://forjamari.linex.org/forum/forum.php?forum_id=298")  CD as well! :)

Regards, Herman :)

---

### Post by freebird54 on 2007-04-02
That sounds like the answer to the problems I'm bound to cause myself as I go along!  I tried to get the 'equivalent' super boot disk for WinXP to work back when I cared about it, but never did.....but I love to have recovery tricks handy (beyond a floppy, a copy of the OS and an attitude :) )

BTW - the grubs are pretty now, no excess entries, nice splashies etc.  I cheated a wee bit though - I used the GrubEd script for some of it - if only to DIrect Edit without re-sudo'ing...

I guess I'll have to learn some GIMP to get what I want though - as soon as I figure out what that is :D

Thanks again for the great grub page - hope you don't mind if I point others to it (if you're not on here) ?

---

### Post by freebird54 on 2007-04-02
Already downloaded it - burning now.  Thanks again!

---

### Post by Herman on 2007-04-02
> First thing I'd try is disabling fsck for windows partitions in /etc/fstab. Just change the last number in their entry lines to '0'. I agree with mcduck about getting Ubuntu not to bother looking at your Windows partition during boot up.

I'm glad you liked my Grub page and I was thinking of adding a link there to tomosaur's GrubEd script there somewhere myself. 
Yes, please pass the link to it around whenever you think it might help someone.

GIMP is the Gnu Image Manipulation Program. It's for doing almost anything to digital artwork or photos, including making your own animations. GIMP's great fun. Here's two links for the GIMP,  
GIMP Image Editor [http://www.gimp.org/](http://www.gimp.org/)  
Grokking The GIMP [http://gimp-savvy.com/BOOK/index.html](http://gimp-savvy.com/BOOK/index.html)

A tip with burning your new      [Gparted Live + System Rescue + SGD 001]("http://forjamari.linex.org/forum/forum.php?forum_id=298") CD is to burn it to a CD-RW so you can write over it when the software is updated. These guys are certainly hard to keep up with.  LarryT over at GParted has a new GParted-Clonezilla livecd out now, details and download link at the bottom of this page, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
 So now I guess the next thing will be a GParted + Clonzilla +System Rescue +SGD. Well it's all great software, I use GParted and Super Grub Disk all the time.

Well freebird54, it certianly sounds like you have the right attutude and you're having fun with Linux. 
 Catch ya in a while, I have some CD burning to do, and maybe some testing. :)

Regards, Herman :)

---

