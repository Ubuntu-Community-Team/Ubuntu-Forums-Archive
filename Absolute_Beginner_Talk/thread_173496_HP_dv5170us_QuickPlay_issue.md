---
title: "HP dv5170us QuickPlay issue"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by ebob on 2006-05-10
Hello,

I have recently purchased an HP dv5170us notebook.  What I would like to do is a triple boot system with Ubuntu, Windows XP, and QuickPlay (a Windows XP Embedded partition).  I have been able to install Ubuntu Dapper Beta 2 and have it mostly working.  However, when I try to use the QuickPlay function now, I get a blue screen.  The regular Windows XP boots up fine.  I would like to keep the QuickPlay functionality.  Does anyone have any ideas?

---

### Post by jyeh on 2006-07-17
I have a similar problem: I have a HP Pavilion dv2000t laptop which came with Microsoft Windows XP Home Edition.  The factory-default system configuration of my 60GB hard-drive is as follows:
[LIST=1]
[*]45.53 GB on first partition (/dev/sda1) is NTFS and contains normal XP Home Edition install.
[*]9.36 GB in second partition (/dev/sda2) is FAT32 and contains HP's recovery information (so they don't have to send you recovery DVDs)
[*]1.00 GB NTFS third-partition (/dev/sda3) which is a special embedded Windows XP partition that gets booted whenever you hit the "DVD" or Quickplay buttons above your keyboard.  Note that this is only for Quickplay v2.0 or greater; Quickplay v1.x used a ext2fs partition and ran Linux to allow for direct playing of DVDs.  I believe HP partnered with Cyberlink to develop Quickplay v2.x that is compatible with Windows so you could listen to music and look at pictures stored on your main Windows NTFS partition in addition playing DVDs in Quickplay (without having to boot to a full Windows session).
[/LIST]

I've played around with this quite a bit so I can tell you what I've done so far, but I'd warn you that not everything works right now.

What I've learned:
[LIST=1]
[*]You *can* resize the 1st NTFS partition safely using GParted or QtParted or the partition manager of your choice.  HOWEVER...
[*]...you cannot reassign partitions and still get Quickplay v2.x to work properly.  In particular, it seems that your Quickplay/embedded Windows NTFS partition has to be the third (/dev/sda3) partition.  I'm not sure where the mappings of what partition is "activated" and booted whenever the DVD/Quickplay button is pressed but without changing that, I don't think you can safely reassign or move-around partitions and still get Quickplay to work properly.  Currently, I'm not sure if you need the recovery FAT32 second partition at all, esp. since you can create recovery DVDs/CDs that do the same thing but having gone through a recovery, I think it's faster and safer to keep the recovery partition; a recovery will proceed without any "please insert next DVD" prompts if you run the recovery off the recovery partition, should you ever need to do a full recovery back to your factory-install state.  I also don't know if you need to necesarily have your primary Windows partiton as your first one.
[/LIST]

I was able to resize my primary Windows NTFS partition and using a second empty USB external drive, move my 2nd and 3rd partitions to immediately follow the end of the shrunken first partition without changing partition labels.  If you try to just copy/move things around using the empty space recovered after your shrunk your first partition, the partition labels may change and Quickplay direct won't work properly.  I was even able to create a 4th partition from the recovered space and install Ubuntu (or in my case, Edubuntu) and things SEEMED ok; my normal windows booted find, Ubuntu booted fine.  BUT when I shutdown and then tried to run Quickplay Direct, it started GRUB and showed me three options (in addition to my Ubuntu installation): Windows XP Home, HP Recovery, and Windows XP Embedded.  I assume the third option would have started Quickplay Direct but it just hung there.  I think you must preserve the Master Boot Record or somehow change the mapping of which partition is booted by the DVD/Quickplay button.  Since the latter option is unknown, I tried the former but I ran into another problem: using the Dapper Live CD, I was not able to choose to not install GRUB to the MBR and using the ncurses, text-base install CD it seemed to hang somewhere (or at least the display went black with only a single character-sized box in the middle of the screen).

Anyone have any ideas on how to get the Live installer to choose a different GRUB install location or (even better) to find the Quickplay button settings?

---

### Post by Venomone on 2006-09-23
i'm very glad this subject has come up. i should be getting my custom dv2000t in a week and would also like (e)ubuntu,winXP, and the Quickplay as a "triple" boot feature. i will be checking back here often, hopefully one of you MBR/GRUB guru's could help us out! [-o<

---

### Post by Yako on 2006-12-27
> **ebob said:**
> Hello,

I have recently purchased an HP dv5170us notebook.  What I would like to do is a triple boot system with Ubuntu, Windows XP, and QuickPlay (a Windows XP Embedded partition).  I have been able to install Ubuntu Dapper Beta 2 and have it mostly working.  However, when I try to use the QuickPlay function now, I get a blue screen.  The regular Windows XP boots up fine.  I would like to keep the QuickPlay functionality.  Does anyone have any ideas?

Hi, I had the same issue. Booting QuickPlay gave me a blue screen. But when I used Partition Table Doctor, it said the quickplay partition type was set to 'unknown', while it actually was NTFS. So I set the partition type to NTFS, and then it worked again. Maybe you should try it.

---

### Post by ebob on 2007-01-13
It looks like people eventually responded to my original post.  (They really need to find a way so people can keep better track of their posts around here.)  I have since given up on the idea of using the QuickPlay feature on the notebook.  I found that Ubuntu boots up more quickly than the QuickPlay anyway, thus making this "feature" a moot point.  I have since repartitioned and no longer have the Windows XP embedded partition.

---

### Post by Jonne on 2007-01-13
Well, I used to have Ubuntu + Quickplay on this laptop too, and it started bluesceening for no reason at all too.

I just blew it away (I turned it into more swap).

It's really not worth it, as Ubuntu plays DVD's fine, and quickplay isn't as instant-on as HP makes it out to be.

I wished the remote worked completely in Ubuntu, though. I can only use it to turn my laptop on, mute/change the volume, and pick the OS in grub.

Controlling media apps doesn't seem to work.

---

