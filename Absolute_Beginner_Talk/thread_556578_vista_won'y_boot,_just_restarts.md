---
title: "vista won'y boot, just restarts"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by tommason on 2007-09-21
Hi,

I have had vista running on my comuter for a while now and i decided to install ubuntu. Now I have a little problem, ubuntu won't boot as it's giving me a
* /bin/sh can't access tty, job control turned off*

AND

vista just restarts as soon as i select it at the boot screen. 

I defragged the drive before my ubuntu install, bearing in mind i am a linux noob any one have any good ideas :)

yours 'on the border of being most frustrated' 

Tom

---

### Post by e_james on 2007-09-21
In my recent but very limited experience, Windows can be confused by the new partitions for ubuntu. (I don't have experience of Vista, only XP). In my case XP just hung immediately after the grub selection. The XP installer also got stuck at the point of analysing the hard drives. To solve my problem I had to make sure the Windows partition was first on the disc and then install ubuntu for a second time. It was probably an advantage that I was moving my existing XP setup to a new larger hard drive using a partimage backup. 

I have seen some comments that Vista has something new about its partitions and partition managers older than Vista may not do the job properly.

This link [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) might be of some help, especially the sections on GAG, WinGRUB and Super Grub Disk.

There are ways to reinstate the Windows boot loader but I can't quickly suggest any particular one. If you search these forums and other internet sources you should find suitable references.

At this point I believe that there is a simple solution but I don't know exactly what it might be. It is possible that a second attempt at installing ubuntu would fix both problems. I have no experience in using the Live CD installer; I have always used the the Alternate CD because I think it gives me more options in partition setup. It has no graphical interface, just text.

I do strongly suggest that you do not make any futher changes to your hard drive without thinking carefully. It would be easy to create additional problems without solving the existing ones.

It might be useful to point out that a linux live CD such as ubuntu allows you to back up and restore partitions between internal and external drives. You do need to find the correct route between mounted and unmounted partitions.

---

### Post by tommason on 2007-09-22
So how do I make sure that the windows installation is 'first on the disk'?; I defragged before I installed, which I thought was sufficient....

---

### Post by e_james on 2007-09-22
I've just seen your message but I have to go out now. I'll be back later with details.

---

### Post by tommason on 2007-09-22
much as i hate to do this, I'm giving up...what i first thought would be a days work to dual boot vista/ubuntu has now turned into 4 days of getting far too involved in the depths of computer trickery and has destroyed my vista install....  time to format and start again.
I'm going to wait until the next release of Ubuntu and try again..if this will solve any of the problems...
Thanks a lot for your time and help, I really appreciate it
Tom

---

### Post by e_james on 2007-09-22
I understand your position but I would like to suggest you give some thought to partitioning even if you only install Vista at this time. Rather than write out the details again I suggest you read my post in this thread 

[http://ubuntuforums.org/showthread.php?t=498319](http://ubuntuforums.org/showthread.php?t=498319)

If you are interested I will be happy to explain further.

Before you format the hard drive this link might be worth reading

[http://www.kellys-korner-xp.com/xp_haldll_missing.htm](http://www.kellys-korner-xp.com/xp_haldll_missing.htm)

I know it's not the same error but the procedure might still work for you. If you are planning to reformat anyway there seems to be nothing to lose.

When you are ready to think about linux partitions this thread is probably a good starting point

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

or maybe this link

[https://help.ubuntu.com/community/HowtoPartition?](https://help.ubuntu.com/community/HowtoPartition?)

---

### Post by tommason on 2007-09-22
AAAARGH now partition magic says my hard drive is one big BAD sector and won't format it!!!!!!!

---

### Post by e_james on 2007-09-22
It is really frustrating when repair utilities refuse to do repairs because the item to be repaired is faulty!!

There is at least one possible solution depending on your situation. 

Have you access to another PC running Windows XP (or maybe Vista)? 

Can you put your faulty drive in an external usb case? 

Have you a second drive which you can temporarily install as the first drive in your current PC with the faulty drive as a second drive? 

What happens when you boot the PC with the ubuntu live CD?

This link is also interesting  [http://forums.cnet.com/5208-12546_102-0.html?forumID=133&threadID=239417](http://forums.cnet.com/5208-12546_102-0.html?forumID=133&threadID=239417)

---

### Post by tommason on 2007-09-25
Cheers everyone for your help, apologies for my absence and non replies..have solved the Problem though :D 
This was my problem:
[I]
"I have deleted and formatted the vista partition using various programs (partition magic etc) but each time i attempt to boot from my vista DVD to reinstall (AND my girlfriend's XP CD) i still get the Grub 22 error even though i have set the BIOS to boot only from CD (Ubuntu live CD boots fine)

Want I want to do now is delete/replace the MBR to get rid of this. Are the xp and vista mbrs different?, I was thinking of removing the hard drive from my girlfriend's xp machine and sticking my drive in and using the xp partitioning program on the CD to format my drive"[/I]

solution:

Searching around on google led me to find a program called 'mbrfix.exe'
You just dump it into the root of c; open up command prompt; choose your drive and type:
mbrfix /drive 1 fixmbr /vista
and in about a second it is done! full of lovely new vista MBR goodness!! (well as good as vista goodness gets :P)

No starting in safe mode/no strange partitioning software

EU-bloody-REKA!

---

### Post by Maestro23 on 2007-09-25
Glad you got your system fixed.  Hope to see you back in Ubuntu down the road.  Don't forget to mark this thread SOLVED.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by e_james on 2007-09-25
Yes I'm happy to hear the good news. However,if you haven't already, please have a look at the link in my last post. It might help to explain what went wrong in the first place. It seems to confirm that a Vista created partition is significantly different from the XP version, which implies that Vista-compatible partitioning software may be desirable before installing linux.

---

