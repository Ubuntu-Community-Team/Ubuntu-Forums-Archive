---
title: "Dual booting help please"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Newbie29 on 2007-04-21
Hello,
I am trying to install Ubuntu Linux on my computer alongside the currently installed XP. I have found a video tutorial telling me how to do this, but the problem is that in that method I'd have to completely reinstall Windows and delete all my data which is something I don't want to do.

This is what I have right now:
1-Windows XP
2-A 38.9 GB "C:" drive with only 14.2 GB free
3-A 35.6 GB "D:" drive with about 25.0 GB availabe

Now, what I want to do is to install Ubuntu Linux on my "D:" drive and give it about 20 GB GB of space.

Could someone give me the instructions on how to do this or give me a link to a tutorial somewhere telling me how to do this.

p.s. I am going to reinstall Windows soon, but I don't have the CD yet, I am going to get it from my friend, but untill then, is there anyway to dual boot without reinstalling.

Thank You in advance.

---

### Post by Newbie29 on 2007-04-21
Hello,

I am trying to install Ubuntu Linux on my computer alongside the currently installed XP. I have found a video tutorial telling me how to do this, but the problem is that in that method I'd have to completely reinstall Windows and delete all my data which is something I don't want to do.

This is what I have right now:
1-Windows XP
2-A 38.9 GB "C:" drive with only 14.2 GB free
3-A 35.6 GB "D:" drive with about 25.0 GB availabe

Now, what I want to do is to install Ubuntu Linux on my "D:" drive and give it about 20 GB GB of space.

Could someone give me the instructions on how to do this or give me a link to a tutorial somewhere telling me how to do this.

p.s. I am going to reinstall Windows soon, but I don't have the CD yet, I am going to get it from my friend, but untill then, is there anyway to dual boot without reinstalling.

Thank You in advance.

---

### Post by AAM on 2007-04-21
Dear Newbie 29

Firstly, if you are going to do a Windows re-install at some time soon, do it first! Windows writes its bootloader to the Master Boot record (MBR) taking into account no other OS (after all it's the only one, isnt it?). GRUB with Ubuntu is much more kind and plays with multiple OS's.

**[COLOR="Blue"]Before installing, copy off all the stuff on the drive you are going to put Ubuntu on, because it will be wiped in the process.[/COLOR]**

When it comes time to install Ubuntu, put in the liveCD and boot, then click on the install icon and walk through the installation process. When it comes to partitioning the hard drive, you will be asked what you wish to do. Select the **manual** route and find your MS-designated D: drive and partition that. Give yourself 3 'sub'-partitions on partition - 8-10GB for the '/' (or root) partition (ext3 or reiserfs and bootable), twice your RAM for swap, and the rest as your **/home** partition (ext3 or reiserfs and non-bootable).

Assuming all your hardware is detected (have it plugged in when installing), you should be right to go!

[do some searching to make sure that these instructions are correct and you understand them properly]

---

### Post by mikewhatever on 2007-04-21
Here you are [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
Keep in mind that when you reinstall Windows, it overwrites grub boot loader in the MBR, so that your Ubuntu would become unbootable. You can reinstall grub using Ubuntu installation CD, here is how [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by aysiu on 2007-04-21
If you're planning to reinstall Windows soon, I'd advise on waiting to do the dual boot until you reinstall Windows... for two reasons:
1. Reinstalling Windows deletes everything anyway, so if you mess up the dual boot, you'll have lost nothing.
2. Reinstalling Windows *after* you've set up a dual boot often screws up the dual boot, since Windows' boot loader overwrites the Master Boot Record, and Windows won't automatically detect Ubuntu and add it to the boot menu. Ubuntu will, however, automatically detect Windows and add it to the boot menu.

Here's a tutorial:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Sef on 2007-04-21
There is no need to reinstall Windows.  Just follow one of the tutorials below.

> Here you are [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

That is for booting from a Live CD.

If you are using the alternate cd, then use the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/") tutorial.

---

### Post by UbieNoobie on 2007-04-21
Well I have lots of questions I'm going to be asking about Ubuntu but I have to say the whole dual booting thing worked smooth as silk for me. I started with a new 250GB hard-drive so I just made 50GB and 150GB partitions, installed XP to the 50GB, formatted the 150GB from windows and then installed Ubuntu allowing it to use all the remaining 50GB. Both systems seem to be working perfectly. Now I just need to work what the heck I'm doing in Ubuntu.

---

### Post by rillip on 2007-04-21
I haven't installed with XP before, but did with 2000 without issue.  Being that they're built on the same framework, I can't image it's too terribly difficult.  As always, I'd recommend a backup to a different physical media (not a partition on that drive, a different drive, a shared network drive, a CD, whatever fits your situation).  Here's how my install went

I had Windows on the drive usijng 100% of the drive (i.e. I had one partition for the "c:" drive).

I put in the Ubuntu LiveCD.  I resized the partition to the size I wanted (half the drive in my case) and told it to make three partitions from the new one, one for /, one for /swap and.... frankly, can't remember the other one.  /home?  I didn't do anything fancy, just did whatever it was it suggested.

It installed grub and Ubuntu, I rebooted and had a menu screen showing Ubuntu and Windows.

Windows continued to work fine for me.

Now it sounds to me like you've created seperate partitions on one physical drive from your post, but I can't tell if you're talking about three drives or one drive with three partitions.  I also don't know if they're logical partitions on an extended partition or just regular partitions.  If it's three seperate drives, pick one and it'll go.  If it's three physical partitions on the same drive, you can do what comes bellow.  If it's three logical partitions, it's not going to work.  You're going to have to delete those logical partitions, resize the actual partition to make some room for Ubuntu, then recreate the logical partitions.

When you boot the live CD, you should see all the partitions there in the installer.  If you only see one or two, then you have logical partitions and as I noted above that's an issue.  If you see one physical partition for each drive, you should have no issue.  I would resize one of them into the three paritions you need for Ubuntu and let it install on there.  Shouldn't have any issues breaking your Windows, but sometimes SHOULD and DO don't always intersect.  I'd make a backup so that if you do have to reinstall you don't get burned.  I've never had a problem of the three installs I've done, but you never can tell.  Best of luck!

---

### Post by Newbie29 on 2007-04-21
Ok then, thanks for your replies, now I have one more question, as I mentioned before, I'll be reinstalling Windows soon, what in your opininon would be better to use, CD-Rs or a DVD-RW, or an external hard disk.

I need to back up things like personal photographs, videos, the setup files for programs like Photoshop, Flash, Dreamweaver etc. and .........yeah I think thats it.....mostly that.

Oh, and what would you recommend as a good Anti-Virus program (for Windows of course :) , shouldn't have any problems with Linux, it being the superior operating system...XD   )


Thanks in advance.

---

### Post by Sef on 2007-04-21
> what in your opininon would be better to use, CD-Rs or a DVD-RW, or an external hard disk.


For back ups,  the external hard disk is best.  It can back up everything with little problem.

> at would you recommend as a good Anti-Virus program

I recommend [AVG]("http://free.grisoft.com/doc/1").  There's a no cost version which works great.

---

### Post by brennydoogles on 2007-04-21
> **Newbie29 said:**
> 
Oh, and what would you recommend as a good Anti-Virus program (for Windows of course :) , shouldn't have any problems with Linux, it being the superior operating system...XD   )


LOL. Avg is the best free antivirus, but if you want the best paid antivirus I have had the best luck overall with Prevx1. It is a virus scanner/firewall, and it checks your files against a database instead o relying only on virus definitions. That's my suggestion.

---

