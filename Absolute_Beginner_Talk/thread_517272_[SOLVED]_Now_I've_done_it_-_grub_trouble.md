---
title: "[SOLVED] Now I've done it - grub trouble"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by AnnaMary on 2007-08-04
I am new to Linux, and I think I have just lost my Ubuntu settings.  Here's what I have done - before knowing about Ubuntu, I tried Puppy.  I tried to install puppy as a dual boot with windows xp.  I followed all the directions, but I never did see an option to boot puppy when I restarted the machine.  Then I received my Ubuntu cd and forgot all about puppy.  I managed to easily set up a dual boot with windows xp and Ubuntu.  

Problem begins:   I received an updated puppy cd and wanted to try the live mode.  I restarted computer using updated puppy live cd.  Well, since puppy is living on my hard drive somewhere, it went right ahead and updated/installed itself.  I restarted the computer a couple of times, but no puppy to be found.  My options were to boot windows xp or Ubuntu. 

Enter Grub:  I did some reading and found out I needed to get grub going in order to boot puppy (or something like that.)  So, I followed the grub directions as best I could and installed it.

NOW:  When I restart the computer, I get a gnu grub 0.97 screen which gives me options to select a partition to boot from.  Only when I select windows xp do I get any results.  All other partitions give an error 15 - something about files not found!  Now I am panicking because I can't get my wonderful Ubuntu to work again!  I think grub ate it!  I don't know how to get rid of grub or find my precious Ubuntu again.

I had to log into windows to type this post.  I can only use Ubuntu now if I put in the live cd, which, of course, has none of my settings on it!!!!!  Also, I can only boot into puppy by using the live cd. 

Many thanks for taking the time to read all of this and assist me.

---

### Post by Duck2006 on 2007-08-04
Run the live CD and post the output of

sudo fdisk -l

---

### Post by AnnaMary on 2007-08-04
Thanks for the suggestion, but I do not know enough of what I am doing to make it useful.  I am running Ubuntu live right now.  I opened a terminal and typed sudo fdisk -l, and I don't know what to do with the information.  

after ubuntu@ubuntu:~$ sudo fdisk -l    the terminal says:


Disk /dev/sda: 122.9 GB, 122942324736 bytes
240 heads, 63 sectors/track, 15881 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

 
Device    Boot Start   End          Blocks    Id   System

/dev/sda1   *      1    2648   20018848+    7  HPFS/NTFS
/dev/sda2      2649   9596   52522627+    f   W95 Ext'd (LBA)
/dev/sda3      9596  15881  47512237+   83   Linux
/dev/sda5      2649    2698      377968+   83   Linux
/dev/sda6      2710    9338  50115208+    7    HPFS/NTFS
/dev/sda7      9400    9596    1477948+    82   Linux swap / Solaris
/dev/sda8      2699    2709        83128+    82   Linux swap / Solaris
/dev/sda9      9339    9389      385528+    83   Linux
/dev/sda10    9390    9399        75568+    82   LInux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$

I can surmise that this is telling me about different sections of my computer, but other than that I don't know what I am looking at or what to do next,  Please help.  Thanks!

Does this mean my beloved Ubuntu  with all of my settings is still lurking on my computer just out of my reach?  (I don't care if I ever see puppy or grub again)

---

### Post by logos34 on 2007-08-04
Try [SuperGrub CD]("http://supergrub.forjamari.linex.org/").  Hopefully that will allow you to boot ubuntu, and then restore grub to the way it was before.  
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

You only need one of those swaps.  After you get into ubuntu you can unmount the other linux partitions and swaps, then use Gparted to delete them.

---

### Post by AnnaMary on 2007-08-04
Okay, thanks again for the information.  I looked at the super grup instructions, etc, and it is all foreign to me.  I would rather just clean off my entire hard drive and start over completely - windows and all.  How do I do this?

Before I started using Linux, I backed up all my important files on cd's and floppy's.  If I can just wipe everything out on my machine, I can then just reload windows and Ubuntu and dual boot and reconfigure everything again.

---

### Post by ron999 on 2007-08-04
AnnaMary
Before you do anything rash.
I once messed up my GRUB and I got it back by using the instructions in a thread.
It uses CLI (Command Line Instructions) that you have to enter into a monitor.
It uses the  LiveCD to boot from first.
Why not give it a try?
This is the link:-[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by Duck2006 on 2007-08-04
> AnnaMary
Before you do anything rash.
I once messed up my GRUB and I got it back by using the instructions in a thread.
It uses CLI (Command Line Instructions) that you have to enter into a monitor.
It uses the LiveCD to boot from first.
Why not give it a try?
This is the link:-http://ubuntuforums.org/showthread.php?t=224351

I would go with this fix.

---

### Post by alienexplorers on 2007-08-04
Boot your Ubuntu live-cd.  Run terminal and type in sudo grub
Enter
find /boot/grub/stage1
you will get an output like (hd#,#)
Enter
root (hd#,#)
setup (hd#)
quit grub editor
reboot

---

### Post by AnnaMary on 2007-08-04
I am typing from Windows XP because without a live cd, it is the only OS I can get into right now.  I followed the information in the thread that was also listed here, and the terminal in live ubuntu seemed to take it well.  With great hope, I rebooted, but alas, I have the same dilemma I began with.

Here is what comes on my screen when I start up (both before and after the recent fix):

GNU GRUB version 0.97 (639K lower/515008K upper memory)

***then I get a blue box with the following***

Windows (on /dev/hda1)
Linux (on /dev/hda3)
Linux (on/dev/hda5)
Windows (on/dev/hda6)
Linux (on/dev/hda9)

Linux initrd/tmp/boot/intrd.img-2.6.20-15-generic (on/dev/hda--->

Install Grub to floppy disk (on/dev/fd0)
Install Grub to Linux partition (oon/dev/hda3)

-for help press 'c', then type 'help'
-for usage examples, type: 'cat/boot/grub/usage.txt'

*****************************************************

This is the same, now somewhat familiar, grub screen of paralysis I have had all along.  When I select Windows (on/dev/hda1), I get into windows xp with no problems.

ANY other option on the list that I select, gives me an error 15 about stuff not being found!

Even the nice long line that starts with Linux initrd with all that terrific information yields nothing for me.  

I have tried to use the help suggestions, but I don't know enough for it to make sense to me.

Okay, I am going to get out of windows, reboot with ubuntu live, and check in later to see what I can find here.

A million thanks for your effort, time, and patience with me.

---

### Post by belikralj on 2007-08-04
Error 15 sounds awfully farmiliar, I think I had it recently and I managed to fix it somehow, I just don't remember how at the moment. But you're in good hands :) these guys know their stuff so don't use your parachute just yet :)

---

### Post by AnnaMary on 2007-08-04
Thanks for the empathy post  :smile::lol::lol:

I will be back later tonight - believe it or not, the likes of me has to go and get my cousin's pc set up with dsl, etc.   He just learned email and doesn't know windows or anything yet.  I wish I knew enough of linux to get him started on the right foot.  Poor guy!

---

### Post by confused57 on 2007-08-04
> GNU GRUB version 0.97 (639K lower/515008K upper memory)

***then I get a blue box with the following***

Windows (on /dev/hda1)
Linux (on /dev/hda3)
Linux (on/dev/hda5)
Windows (on/dev/hda6)
Linux (on/dev/hda9)

Linux initrd/tmp/boot/intrd.img-2.6.20-15-generic (on/dev/hda--->

Install Grub to floppy disk (on/dev/fd0)
Install Grub to Linux partition (oon/dev/hda3)

-for help press 'c', then type 'help'
-for usage examples, type: 'cat/boot/grub/usage.txt'

This is Puppy's /boot/grub/menu.lst that is installed on your mbr...you need to use the live cd to install Ubuntu's grub to the mbr,  the link was given to you earlier how to do this, but I'll list it again:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I've installed Puppy linux before & it's not the best at setting up other Linux OS boot parameters.  Once you reinstall Ubuntu grub's IPL to the mbr, then you can add an entry to boot Puppy Linux, a symlink entry would probably be the best method:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

### Post by AnnaMary on 2007-08-04
Thank you for the information and patience to post the link again!  I have already followed these instructions to install ubuntu grub twice now from the live cd.  When I reboot, I get the screen I typed out before, and I can only log into windows xp (unless a live cd is in the drive).

I don't know what I am missing here.  In the terminal on ubuntu live, it looked as though installing grub was successful after following the directions in the link (but what do I know?)

---

### Post by AnnaMary on 2007-08-04
P.S.  I don't know what mbr, symlink, or IPL mean.

---

### Post by AnnaMary on 2007-08-04
P.S. again - I looked at the super grub page, and I don't know how to burn cd's.....can I buy one of those from somewhere?

Can I just evict all evidence of Linux from my computer, keep win xp, and reinstall ubuntu???

---

### Post by confused57 on 2007-08-04
> **AnnaMary said:**
> P.S.  I don't know what mbr, symlink, or IPL mean.

This website explains these terms quite well:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

What was the output of?:
```
find /boot/grub/stage1
```

You should receive something like:
root (hd0,2)
root (hd0,5)
root (hd0,7)

You need to determine which is the Ubuntu root partition, then you would enter the corresponding root:
```
root (hd0,2)
setup (hd0)
```

I'm guessing Ubuntu is on /dev/sda3, since it is the largest Linux partition?

Added:  Here is how to burn an iso:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

You need to burn the iso as an "image", at a slow speed(8x or less)...your cd writing program "should" have an option to burn an image to cd, you don't want to burn as a data cd, nor as a bootable cd.

Before you attempt to delete any Linux partitions, you should try to restore Window's bootloader(actually IPL)  to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
Once you're able to boot Window's without grub, then it should be safe to delete your Linux partitions and reinstall Ubuntu.

---

### Post by MQMike on 2007-08-04
GRUB is not the problem -- it is/can be your friend here.
Follow confused57.
Perhaps you could report what the find command comes up with.

---

### Post by AnnaMary on 2007-08-04
The output from "grub> find /boot/grub/stage1"    is  " (hd0,2)"

next, after "grub>", i typed "root (hd0,2)" and pressed enter

grub> came up again, and i typed "setup (hd0)" and pressed enter

Then, after telling me that /boot/grub/stage1 and stage2 exist, the terminal ran "embed /boot/grub/e2fs_stage1_5 (hd0)" ...    16 sectors are embedded.
succeeded
  Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,2)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub>

Then I typed quit after the prompt which brought me back to:

ubuntu@ubuntu:-sudo find /boot/grub/stage1
find: /boot/grub: No such file or directory
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$

---

### Post by MQMike on 2007-08-04
Looks like you reinstalled GRUB correctly then.
But now you need to re-boot to test it ans see what comes up.

(You may still have to edit the boot menu, called /boot/grub/menu.lst, but let's see; and anyone here can help with that.)

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
The following topics are covered here, by date—see the posts that follow.

HOW To:  Change the Default Operating System (Also:  Changing the timeout, boot menu, and other tips)
April 21, 2007

---

### Post by AnnaMary on 2007-08-04
Thanks for letting me know it appears I may have done something correctly.  I just tried to reboot, and I get the screen that I typed out above called " GNU GRUB version 0.97 "

Again, I can only boot into windows xp, and no ubuntu, or puppy for that matter.  Right now, I don't care about puppy, but I am having serious ubuntu withdrawal symptoms!

From this GRUB screen, when I select any Linux option, I get a variation of following:

Booting 'Linux (on /dev/hda3)
root  (hd0,2)
Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz root=dev/hda3 ro vga=normal

Error 15:  File not found
Press any key to continue.....

-------------

Pressing a key brings me back to the screen with the options I cannot access, unless I want old windows xp.

---

### Post by AnnaMary on 2007-08-04
I am now trying to follow these directions from the last link left for me:

Case 2:  Live OS CD method:  Use this (or Super Grub Disk) if you are not able to boot into any of your Linux OSs to access/edit the menu.lst.   Boot the Live OS CD (eg, your Kubuntu Live CD), open a terminal (Konsole), then as root [COLOR="Red"]make a directory, mount the filesystem containing the menu.lst you need to edit, open menu.lst as root, edit it, save, quit, unmount the filesystem, exit. [/COLOR]
Example, in Kubuntu, if the menu.lst you need is on sdb3 (=(hd1,2)).  Open Konsole (from the Live CD), and then:

sudo mkdir  /media/sdb3                          # make directory called  /media/sdb3
sudo mount  /dev/sdb3   /media/sdb3          # mount device sdb3 on directory  /media/sdb3
cd  /media/sdb3                                # change to this directory
kdesu kate  /boot/grub/menu.lst        # in text editor Kate, open menu.lst file, as root
# Then edit menu.lst, when you are done, File - Save, then File - Quit
sudo umount  /media/sdb3          # unmount the directory; note the spelling of umount
exit

What, EXACTLY, am I supposed to be typing here?

---

### Post by confused57 on 2007-08-04
Maybe you can try booting your /dev/hda3, using the CLI(Command Line Interface)...reboot your computer, when your grub boot menu is displayed, press "c", this will get you to a grub prompt, then enter:
```
configfile (hd0,2)/boot/grub/menu.lst
```
press "enter"

menu.lst is short for menu.list

If this doesn't work, then I suggest you burn a copy of the Super Grub Disk...see if it can boot your Linux partition(s).  SGD can also restore your Windows IPL(Initial Program Loader) to the mbr(master boot record).

Added:  The link MQMike gave you is for Kubuntu, here's how to mount your root partition in Ubuntu, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

---

### Post by AnnaMary on 2007-08-04
Okay, I am in windows xp again.  I tried using the configfile command given in the last post, and my evident operator error factor is just too great to be repaired.

I have enjoyed Linux so much for the past two weeks that I actually ordered a 2nd pc to have for looking at distros, etc....

Since I will need a different day to learn to burn cd's, plus I have no blanks, I will wait on that.  

My "new" used pc will be here by the end of the week, and I will install Ubuntu and get it back the way I want it and toggle with my KVM switch.  Thankfully, I will be back to doing most everything in Ubuntu again.  In the meantime, I will suffer winxp for a few days.

Eventually, I hope to try super grub cd and reclaim all the hard drive space that is on this machine that I cannot access.  It has just become my windows backup pc.

THANK YOU ALL SO MUCH FOR YOUR ASSISTANCE.  I regret that I am having so much difficulty doing what must be routine tasks to many.

---

### Post by confused57 on 2007-08-05
Sorry nothing worked for you...I believe Puppy may have installed over your Ubuntu install.
Sounds like you have a workable plan...I also have a KVM switch connected to a Ubuntu dedicated built pc(with 9 different distros) and a Dell dualbooting Windows and Ubuntu on 2 different hard drives.

There is a definite learning curve with Ubuntu & Linux, but you'll learn a lot and it's  fun in the process...you've been provided some excellent links in this thread to get you started, and a dedicated Linux pc is an excellent idea.  If you want to try Puppy, I recommend the 215CE version, very nice desktop appearance.  I'm sure you'll enjoy your experiences with linux & Ubuntu, in particular.

---

### Post by MQMike on 2007-08-05
Booting 'Linux (on /dev/hda3)
root (hd0,2)
Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz root=dev/hda3 ro vga=normal

Error 15: File not found

This is confusing, for sure.  The find command did return (hd0, 2) for Stage1, which suggests it’s the correct partition.
I wonder if this is a UUID issue?  I only toss that out in case someone else sees anything there.  That would be in the etc/fstab file for hda3.  It is also covered in a post under the How-To I referenced.

Edit: I just noticed the two posts above this one.
It is disconcerting that configfile didn't boot up Ubuntu.
Also, your sudo fdisk -l output shows lots of partitions -- wonder what all those are?
And finally, as confused57 says, it does point at the possibility that Puppy installed "over" something.

Good luck.  Sounds like you have a plan.  I am also thinking of building a second PC for such.  I have one PC now, two SATA HDs, XP on sda; and several Linux distros on sdb.  A second PC is good for backup, too.  Not data backups -- but hardware backup, so you'll have something to access the Internet if one PC fails (like a power supply or something)!

Always connected.  Good luck with your new adventures! -- Mike

---

### Post by AnnaMary on 2007-08-06
Due to operator error and sheer ignorance, I have messed up my partitions and grub, etc.  Please see my last posted issue titled "Now I've done it - grub trouble"    --- sorry I don't know how to put the link in here conveniently.

Now that I have Windows XP, Ubuntu, Puppy, and GRUB all crosswise, I would like to get rid of all linux  and grub stuff on my hard drive, while simultaneously saving xp, and then reinstalling Ubuntu for a dual-boot.

If need be, I am also willing to reinstall windows xp and just reconfigure it and add Ubuntu.  

Right now, I am looking at options such as Killdisk.com, Wipe Drive, terabyteunlimited, and Gparted (if possible).  Please keep in mind, I have no idea what I am doing, I just know what I want - Ubuntu & Win XP dual boot minus the grub issue and puppy interference.

Many thanks to all who take a moment to read my post.

---

### Post by bren on 2007-08-06
good and (over)full explanation here

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

but are you sure we cannot help you fix the current grub mess?
if you have a Ubuntu Live CD it should be possible....

in any case read the link above and you will start "to have more idea what you are doing"


bren

---

### Post by MQMike on 2007-08-06
Here’s a brief overview – please wait for others to add details, tips, etc. This should not be a problem at all.

The very first thing to do is to fix the Windows Master Boot Record (MBR) so that you can always boot into Windows after removing Ubuntu.  You need your Windows CD to fix the mbr.  (The Windows fixer will get rid of GRUB on the MBR).

After doing that, test it – turn off the PC, turn it on, see how it boots up into Windows.

Then you can run GParted, deleting all the other non-Windows partitions on your hard drive.  That wipes it all off, including GRUB.

Then, use GParted to make a partition for Ubuntu – or, just run the Ubuntu installer and you can do the partitioning from there.  (You need at least 10-15 GB for Ubuntu; some people recommend making a separate /home, etc. – wait for tips or check the many how-to’s on it.)

During the installation of Ubuntu, make sure GRUB is installed to the MBR.  After installing Ubuntu, GRUB will automatically then set up a bootloader for both Windows and for Ubuntu.

---

### Post by bodhi.zazen on 2007-08-06
Just install Ubuntu.

Repartition the Linux partitions with gparted and re-format them making at least / and swap ...

Leave the ntfs partition alone ...

Then install ...

Please refrain from starting new threads on old problems, it is like starting over for those trying to help ...

---

### Post by AnnaMary on 2007-08-07
Thank you all for assisting me.  I was able to use my windows cd to fix mbr.  Then I used gparted with ubuntu live cd.  I may need to delete more, but I am happily dual booting into Ubuntu and windows xp.  All of the links you provided were useful.  You saved my week!

I will think about learning GRUB properly another time.

Amazing how after one week with Ubuntu, and I seem to be developing allergies to windows, despite my ultra newbie status.


(And I shall try not to post in the wrong place next time.  I perceived wiping my hd as a "new" problem.  Oops!)

Again, thanks for your patience and clear direction.

---

