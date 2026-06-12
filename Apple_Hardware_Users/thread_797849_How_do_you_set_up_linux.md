---
title: "How do you set up linux?"
date: 2008-05-17
forum: Apple Hardware Users
---

### Post by Jack Hollister on 2008-05-17
Hi im new to linux and I have a ubuntu disc and I would like to install it on my iMac (2.4ghz dual core 1gb ram 320gb hdd 24" screen with Ati 2600XT)
I just wanted to know what i have to do before I install and how to install it (with a partition)
Help would be very much appreicated
Thanks
:)

---

### Post by LeoSolaris on 2008-05-17
Welcome, glad to have ya here!

To start with, pop the LiveCD into your CD drive and start it up. You most likely will have to go into your BIOS selection screen. (That little screen that pops up for just a few seconds when you turn the computer on) Usually to activate the menu, you have to push F2 or Delete. Just watch the screen to see which one needs to be pressed. Once there, look for Boot Order, or Boot Device. Different BIOS, different categories. Set it so you boot from your CD drive before the Hard drive.

Alternatively, if there is a Boot Device choice at the start up before you go into the Set up Menu, that will work too. (Bonus: it's temporary)

Alright! Now the computer will restart, or boot from the CD if you used the alternative, and looking at a menu with Ubuntu at the top. Select Install.

Eventually you will get to a desktop. This is the live desktop, not your installed desktop. It will be slow because it is using your CD player like a hard drive. To keep the operating system you already have, there will be some things you have to do, but if you just want Ubuntu by itself, then just click on the install icon on the desktop, and select "use entire hard drive" when asked. It will do the rest.

To duel boot, things are somewhat more involved, but no worries, it's not hard.

Go to System->Administration->Gparted. From there you are going to shrink your existing partition down (click on the picture and drag it down to size, then click apply) This leaves a big blank space for Ubuntu to install itself on. Now close that and go to the install icon. This time, instead of the "use entire hard disk" option, select "use free space" option.

That's it. There are more exotic configurations for partitioning, but for the first time around, I would keep it simple. Experiment after you have mastered the basics, if you feel the urge.

Leo

P.S. Use the LiveCD to make sure everything works, like your internet, sound, and the rest of the hard ware. The graphics card will have to wait till after the install because to enable it requires a restart.

---

### Post by Jack Hollister on 2008-05-17
Thank you for your reply, I will be trying this out In the morning
Ill edit once I have done it :):)

---

### Post by seaward on 2008-05-17
Hey Jack,  there are a couple of really good resources that you can always check out for information about running Ubuntu on a Mac.  The first is [the ubuntu user documentation]("https://help.ubuntu.com/community/").  I had a quick search and found that there is a page dedicated to [Ubuntu on iMac]("https://help.ubuntu.com/community/Intel_iMac?highlight=%28imac%29").

In addition, there is a reasonably up-to-date Ubuntu Mac thread [here in the forum]("http://ubuntuforums.org/showthread.php?t=493393") with some interesting bits to read.

In order to get started running Ubuntu on your iMac, I'd recommend booting from the LiveCD by holding down the ALT/Option key when you hear the chime sound soon after switching the computer on.  This should give you a menu with a picture of a CD, labeled Windows.  Double click that CD and you'll be presented with a menu offering to Try Ubuntu Without Installing.  Press enter with this option selected and your disc will boot up.  Have a play around with Ubuntu, see if you like it.

If you do like it, check out the iMac page I linked to above and it gives you some pretty solid details on how to go about installing Ubuntu properly on your hard disk.

Have fun!

---

### Post by Aurora on 2008-05-17
> **LeoSolaris said:**
> Welcome, glad to have ya here!

To start with, pop the LiveCD into your CD drive and start it up. You most likely will have to go into your BIOS selection screen... 

With Apple hardware, it's different.  There is no BIOS selection screen; Apple does not use BIOS. And, of course, you've backed up your system, right?

There's a FAQ here:

[http://ubuntuforums.org/showthread.php?t=493393](http://ubuntuforums.org/showthread.php?t=493393)


If you're running Leopard, you can use Boot Camp Assistant.  I think you have to boot from the Mac OS installation disk.  I don't think you can partition a drive as you're using it to run the computer. Put the CD in the drive, reboot, and hold the C key down as it boots.

If you're running Tiger, you can't install Boot Camp legally anymore. You can boot the Ubuntu Live CD and use gparted to shrink your Mac OS partition to make room for an ext3 partition for Ubuntu. Put the Ubuntu CD in and reboot with the C key.  When the desktop is up (it takes a while), go to System>Administration>Partition Editor.  You can highlight the Mac OS partition and click on "Move/Resize".  It's pretty self-explanatory from there.

That should get you started.  I am just starting out with MacIntel/Linux myself, after running Linux on PPC machines then x86 PCs.  I have not actually installed yet; I'm trying to figure out whether I need a swap partition, and how large.

BTW I have never been able to boot CDs that I burned with Finder, so you may have to get an Ubuntu Live CD some other way.

---

### Post by cyberdork33 on 2008-05-17
> **seaward said:**
>  I had a quick search and found that there is a page dedicated to [Ubuntu on iMac]("https://help.ubuntu.com/community/Intel_iMac?highlight=%28imac%29").
I have written most of what is there, and it is nowhere near complete. Anyone with an iMac, please add what you can!

---

### Post by Brightbelt on 2008-05-18
Details folks. I have a 24" iMac too. For dual booting, first install [rEFit]("http://refit.sourceforge.net"); it's freeware and makes your booting menu easier. To do a dual boot, I went into 'Boot Camp Assistant' in the Utilities section of my Mac OS X and did the partition ahead of time there. 

Should you decide to install Ubuntu, and you're running your Ubuntu live CD, click the 'Install Ubuntu' on the desktop there and it's an easy start.

Once you get to the partitions section, choose to partition 'Manually'. What you're going to do is to identify the partition you set up with Boot Camp Assistant and delete it, then set up another partition of the same size and format it thusly:

Format as: 'Ext3'
Mount Point: '/' (just the slash; that's it)

Also you'll need a swap space, only 1 gb is necessary for this, so if you need to shrink your partition size to get extra space, do it, and you can use the little space left as a swap. 

From there, it's a cakewalk and Ubuntu and rEFit set up the boot menu for you. If you have problems booting after the install, boot from the CD and choose 'install from first hard disk' and when you can get a rEFit menu, there's a partition manager there which will sync your partitions. 

Many folks have trouble getting the boot into Ubuntu until their partitions have been synced by the rEFit partition editor.

Good Luck! ...Frank B.

---

### Post by Jack Hollister on 2008-05-18
Thanks I have it installed and I will be installing the drivers soon Thanks for the help :popcorn:

---

