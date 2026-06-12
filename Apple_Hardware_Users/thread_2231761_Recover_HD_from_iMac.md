---
title: "Recover HD from iMac"
date: 2014-06-27
forum: Apple Hardware Users
---

### Post by mathew_davis on 2014-06-27
My in-laws imac has been crashing for a while now.  I told them to backup 30 times or more.  Anyway needless to say i think they understand now.  The HD has crashed and they can no longer boot into windows.  An apple repair shop said it's not possible to get the data back without paying 900 to send it to a special facility.  

So I booted up a new Ubuntu 14.04 live CD and started up gparted.  As it's scanning for drives it pops up a message reading "The journal is not empty.  Parted must replay the transactions before opening the file system.  This will modify the file system."  As I am trying to get their data back in tact I want to make sure that I am not causing irreparable damage to the drive.

So I did some reading and people have mentioned needing to turn off journaling in the mac os first as this isn't possible at this point what do I need to do?  Is it ok to replay the journal and get their unsaved data?  Or should I try removing the HD from the machine and put it into another system?  I would much prefer to keep the system in tact if possible.

Thanks in advance.  I am not super familiar with Mac although I am a long time CentOS and Fedora fan.  I have also used Ubuntu back in the 10.04 days.

Thanks,
-Matt

---

### Post by este.el.paz on 2014-06-29
m_d:

I think they should just pay the 900 . . . but you didn't say what "900" you are talking about . . . chickens, cents, Pounds Sterling, or US dollars???  OK, that was humor, but also you didn't say what "imac" you are dealing with . . . also, if they have OSX installed, indeed that file system is different than the linux system, so that won't really work . . . I don't believe.

In my '02ish G4 iMac I had a run of kernel panics a year or so back and I thought it was something "fatal" . . . but when it was running it was clean, so finally took it to a repair shop and they took a long while to trace the problem to broken RAM . . . it's hard to know if your local repair shop is "honest" or not, "900" to get data seems high.  Have you tried to boot the problem computer in "Target mode" using firewire?  You can look that up on Google or in Apple KB . . . but simply, it entails connecting another computer to your problem computer via FW, then boot the problem computer up while holding "command + t" keys . . . if the computer runs at all you should see the FW symbol on the screen, and the disk should show up on you other computer . . . you can then access the files on the problem computer . . . or "back up" to external HD . . . .  Should cost less than "900" . . . .

e.e.p.

---

### Post by mathew_davis on 2014-06-30
Thanks for the reply.  And just to clarify it's 900 Egg Whites.

It's a 2010 imac.  gparted properly identifies the HFS file system, so I was hoping the Ubuntu could properly playback the journal.

The Mac store said it's a dead HD and they can't recover.  I will see if I can get the fire thing hooked up.  I don't have a mac so it's a bit more tricky for me to test.  But I will try that before replaying the journal.

Thanks for the info.  I was really hoping that there was a way in gparted to just ignore the journal and read the drive as is.

---

### Post by este.el.paz on 2014-06-30
> **mathew_davis said:**
> Thanks for the reply.  And just to clarify it's 900 Egg Whites.

It's a 2010 imac.  gparted properly identifies the HFS file system, so I was hoping the Ubuntu could properly playback the journal.

The Mac store said it's a dead HD and they can't recover.  I will see if I can get the fire thing hooked up.  I don't have a mac so it's a bit more tricky for me to test.  But I will try that before replaying the journal.

Thanks for the info.  I was really hoping that there was a way in gparted to just ignore the journal and read the drive as is.

Ah, egg whites . . . so right, there is the labor to separate the whites from the yolks . . . I guess that is a lot . . . .  : - )  I have a '10 MBPro, it seems a little "unusual" for a HD to "die" that early . . . like I was saying, I have an '02-'01 iMac that had panics and it turned out to be RAM . . . .  If, in fact the HD is "dead" then the firewire/target mode option might be difficult, if not possible.  But, yes, GParted can show the partitions and the journaling of them, but, as far as I know, it can't change the journaling of OSX w/o it being "destructive" in some way . . . OSX doesn't like to be messed with by others.  But, if you can "boot" Ubuntu disk on the computer, you can look at the OSX files . . . and maybe for some of them you could move or copy them to another computer or Ext HD . . . but, the filesystem folders will usually have an "X" in one corner, so you can't open them or do anything with them.

Keep in mind that the Apple store is there to sell computers . . . I know it's a bit of pain to get into the iMac, but 900 EWs???? there might be another shop that could do it for less . . . .  Meanwhile try to hook another Mac to it via FW and see if you can move the data in the "dead" one to an ext HD.

e.e.p.

---

