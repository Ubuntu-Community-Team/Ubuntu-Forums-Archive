---
title: "Hi, new Rookie in town..."
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by DizMan on 2006-06-21
Hi there.

First my appologee if this is the wrong forum to post my strory and questions. This post is about my (lack of) Linux experience - and after i've yacked on about that for 136 lines then all my questions start popping up.

**My story - a 3rd time Linux Newbee ](*,) **

Yo, i'm the new rookie in town. In fact i'm not even yet an Ubuntu user. I've currently downloaded 536 MB of the DVD.iso, so there's still a couple of hours of waitin, coffee sipping and the like before the fat lady sings.

In Danish we have the saying that the 3rd time is the time of luck. Well, I guess this is now. These are my Linux attempts:

1) I lost my virginity to Red Hat Linux many years ago. I installed a-heck-of-a-bunch of floppies. The install went ok, but I never got connected to the internet as my built-in modem on my Pentium-90 was a win-modem. Without the net my Linux affair only lasted a good week or so

2) A year ago or so I got Suse Linux 9,2. Quick install without any problems. I even got my internet to work. Wow! But my sound card didn't work and the graphics were not that good too due to low resolution. What to do. I did what most sensible grown up men do with thier computer problems: I called a teenager. He used all day and all night and wow: Suddenly everything was just as I wanted. Then after his 23th bottle of coke he wanted to fine tune something about the graphics. Everything f** up and the screen just flickered green and black when booting up in Linux

3) This is now. I'm running a pretty well running Win XP Prof on a P4-3,2 Ghz with 1 GB row and about 50 GB freespace dedicated to my final encounter with Linux. This time I mean business. In my nightly fantasies I dream that I can do on Linux what ever I'm dooing on Windows now. This is my goal - i'm excited if I'll succeed or not. I'm a medium heavy user running internet, e-mail, office programs, media apps, system utilities and the like so it should be possible. Professionally I'm a software developer on the Z-OS (OS/390), so I think I should be able to learn this as well!

If you are not still sound asleep then i'd like to ask some questions:

My questions :confused: 

* Is there any problems with Win XP co-existing with Ubuntu?
* My internet is provided via a wireless zyxel router and a Asus mainboard with integrated wireless LAN. I'm using WEP encryption. Any chance i can get my Linux to reach the Internet without a lot of hazzle
* A religious question: What's the best desktop? KDE or GNOME?
* I'm currently running NTFS on 2 HDs diveded into 2 partitions each. I'm thinking of using 1 partition with 50 GB space to Ubuntu. Is that enough?
* Is it possible for me to read NTFS from Linux and vice versa - or do I have to create a Fat 32 partition to exchange files between the 2 os'es.


Thanks in advance. I'm looking forward to be an UbuntUser 

/Lars

---

### Post by flapane on 2006-06-21
1) no
2) sure
3) I'd tell you kde, but it's really a religious one, so it hasn't answer
4) do as you prefer
5) both read and write, but write on ntfs from linux is deprecated

---

### Post by rowanparker on 2006-06-21
50gig is plenty for Ubuntu.
It would work fine with 5gig!

Rowan.

---

### Post by %hMa@?b&lt;C on 2006-06-21
no
yes
IceWM>Gnome>KDE :D 
yes
yes

---

### Post by Drakkor on 2006-06-21
Welcome to the forum, I installed Ubuntu 60.06 on a 60Gb drive and have already used 7%,lol !! I think you're gonna love Ubuntu, I also have tried various flavors of linux, Suse,Mandrake,Knoppix,DSL,but think Ubuntu has them all beat.
Good Luck !!

---

### Post by steve.horsley on 2006-06-21
1: Ubuntu replaces the windows bootloader with GRUB, which should offer a chioce of windows or Ubuntu. Should be no problem.

2: As long as the wireless hardware is recognised this should be easy. 

3: 
a) Gnome is great and those KDE fools will burn in hell.

b) KDE is great and those Gnome fools will burn in hell.

c) Don't you start! Try 'em both. But I would suggest Gnome first because it is the official Ubuntu desktop and I gather Kubuntu is slightly behind on GUI admin tools. I think I remember reading that Kubuntu didn't yet have a GUI wireless config tool. And most Ubuntu users use Gnome so most replies to posts for help will be suggesting the Gnome tools. Not that I'm putting KDE down. They are different in feel, and you really should at least try both.

4: 50 Gig is ample. Can I suggest chopping it into 2 - 10G for the root system (/) and 40G for /home? That way you can reformat and reinstall the system without trashing your personsal data. Like keeping a D: for user data.

Don't forget to create a swap partition (1G is fine) if you are partitioning yourself. If you want to let the installer do the thinking, just delete the unused partition leaving 50G unused, and tell the installer to use the free space - it will then create its own partitions.

5: Linux can read but not write NTFS. You can get windows drivers that can read Linux ext2/3 filesystems. Personally, I use a FAT shared partition because I didn't know about the windows drivers, and I use reiserfs not ext3 anyway.

---

### Post by mfrazzz on 2006-06-21
Another option for you (and what I'm currently doing) is if you aren't sure you are ready to completely switch and don't want to lose your XP install, you can run (K/X)Ubuntu in a vmware window directly under XP.  No partitioning of your drive is necessary (vmware will just allocate the space up to the size you specify on your existing partitions).  For me this allows me to play with Xubuntu (my current choice, but I have Gnome and KDE loaded up to switch between) and still continue to work with XP when I need it and I don't have to reboot.  My plan is that as I get more comfortable with Ubuntu, then I'll reverse this and run XP as a vmware session under Ubuntu and just have it for the few things that I have to have XP (We have stuff at work that will only run under IE right now).

Good luck!  I have to say I've had similar past stories with Linux.  I've always left it after a few weeks due to it not being a complete replacement for Windows, but now with Ubuntu, I'm actually thinking I may finally be able to switch and make Windows a secondary OS.

---

### Post by neoflight on 2006-06-21
a very nice intro and a nice post...

install GNOME.... ubuntu will work for you....do not get frustrated when things seem not working... minor tweaks required to get the system working as you expected... do  come back and discuss things and enjoy ur ubuntu pickle...

---

### Post by Iowan on 2006-06-21
Not to throw sand in your soup, but be mentally prepared for a few bumps in the road.  I haven't tried Dapper (yet), but there are usually a few things that require tweaking (I'm still having problems making .wmv files play).  Your success depends on being willing to tackle problems, try things... and probably break something along the way.  The good news is - this forum seems to be one of the bright stars in Ubuntu's sky. There's *probably* someone who has had similar problems and overcome them.  Good luck with the adventure...

---

