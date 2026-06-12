---
title: "XP/Ubuntu: One machine"
date: 2005-07-20
forum: Absolute Beginner Talk
---

### Post by Antinomy on 2005-07-20
Hey folks,

I need help with, or a resource for, running XP and Ubuntu on the same machine. I think this is called "dual boot" but I'm not even sure about that - a total n00b, which is why I'm here (and why the other instructions on this matter seemed to go over my head).

So, here's the specs: I have an AMD 64 with a 60 gig drive.  Two scenarios leap to mind: 

1) I imagine that I'd like to devote most of my file space to Ubuntu, and just enough to Windows that I can use it for emergency purposes.

2) Alternatively, I could see having 3 drives - one for each OS and a drive "in the middle" that they can both hit for data.

Thoughts? Anyone know a good walkthrough write-up for an absolute n00b? Anyone want to come to Queens and do it for me?  :) 

Truly,

Antinomy

---

### Post by aysiu on 2005-07-20
I'd recommend this link:

[http://linux.oneandoneis2.org/starting.htm](http://linux.oneandoneis2.org/starting.htm)

and this one:

[http://www.psychocats.net/essays/linuxguide.php](http://www.psychocats.net/essays/linuxguide.php)

And, yes, I would recommend having a middle (FAT32) partition to share files.

---

### Post by Antinomy on 2005-07-20
[QUOTE=aysiu]I'd recommend this link:

[http://linux.oneandoneis2.org/starting.htm](http://linux.oneandoneis2.org/starting.htm)

and this one:

[http://www.psychocats.net/essays/linuxguide.php](http://www.psychocats.net/essays/linuxguide.php)

And, yes, I would recommend having a middle (FAT32) partition to share files.[/QUOTE]
 Thanks, but these are a bit above and beyond my understanding - or at least my familiarity with the terminology. Actually, that only applies to the first; the second link won't open. 

I'm perfectly open to hearing the following from you: if I can't "get" the first file, I shouldn't be mucking around with a partition or a dual boot.

But if that's the case, maybe there's an ABCs of partitioning out there I can use?

Alternatively, maybe someone would like to breakdown the basics over IM?

Antinomy

---

### Post by aysiu on 2005-07-20
Second link should be working now. I just tried it.
No, you shouldn't give up on partitioning for dual boot if you don't "get" the first link. Have you considered using a Ubuntu (or Mepis or Knoppix) "live" CD?
Doing a complete install of Linux is quite a commitment.
Doing a dual-boot installation of Linux is a bit less of a commitment.
But doing a live CD is no commitment at all.
The live CD runs completely off the CD and RAM--doesn't affect your hard drive at all.

I'd advise using a live CD for a while just to get comfortable with Linux.
Otherwise, as long as you back up your data and have a Windows installer CD, there's no harm in playing around with partitioning--God knows I have. The worst that could happen is you totally screw up your system and have to reinstall...

---

### Post by ozzie123 on 2005-07-20
Actually, if you wanted to try KDE, you can have ntfs as your data partition since in my experience, KDE can read and write to ntfs partition (wonder GNOME can't...)

---

### Post by poofyhairguy on 2005-07-20
[QUOTE=Antinomy]Hey folks,

I need help with, or a resource for, running XP and Ubuntu on the same machine. I think this is called "dual boot" but I'm not even sure about that - a total n00b, which is why I'm here (and why the other instructions on this matter seemed to go over my head).

So, here's the specs: I have an AMD 64 with a 60 gig drive.  Two scenarios leap to mind: 

1) I imagine that I'd like to devote most of my file space to Ubuntu, and just enough to Windows that I can use it for emergency purposes.

2) Alternatively, I could see having 3 drives - one for each OS and a drive "in the middle" that they can both hit for data.

Thoughts? Anyone know a good walkthrough write-up for an absolute n00b? Anyone want to come to Queens and do it for me?  :) 

Truly,

Antinomy[/QUOTE]


Quick note: use the x86 version and not the x86_64 version.

---

### Post by Antinomy on 2005-07-20
[QUOTE=poofyhairguy]Quick note: use the x86 version and not the x86_64 version.[/QUOTE]
 Use the x86 installer? Don't I need to use the AMD 64 version?

---

### Post by UbuWu on 2005-07-20
[QUOTE=ozzie123]Actually, if you wanted to try KDE, you can have ntfs as your data partition since in my experience, KDE can read and write to ntfs partition (wonder GNOME can't...)[/QUOTE]

KDE doesn't do that. The desktop environment will not make a difference for what filesystems you can use. The best option for a shared data partition is a fat32 partition. Both Ubuntu and Windows will be able to read/write to it.

---

### Post by poofyhairguy on 2005-07-20
[QUOTE=Antinomy]Use the x86 installer? Don't I need to use the AMD 64 version?[/QUOTE]

The x86 version will work great on your hardware. Like a charm.

The 64 bit version will work to, but it lacks Macromedia flash, Java, and almost all the media codecs.

So its better to use the 32 bit version.

---

### Post by Antinomy on 2005-07-21
[QUOTE=poofyhairguy]The x86 version will work great on your hardware. Like a charm.

The 64 bit version will work to, but it lacks Macromedia flash, Java, and almost all the media codecs.

So its better to use the 32 bit version.[/QUOTE]
 Okay, sounds good.  Gonna try it today!

Wish me luck, ladies and gents...

Antinomy

---

