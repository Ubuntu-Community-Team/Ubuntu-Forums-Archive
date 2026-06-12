---
title: "Question about Ubuntu home server"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by BlizzofOZ on 2008-03-10
I have some basic questions about using/running a Ubuntu home server:

1)  Can I run this server and have Win XP Pro computers be able to access the server?

2)  If #2 is yes, can I use Win applications, such as WinAmp, PowerDVD, etc, which will run from the Win XP machine to access files (mp3s, dvd movies, etc) on the server?
    Ex:  I want to run PowerDVD to play a movie on the Win XP machine from the Ubuntu server.

Thanks for answering these basic questions...

---

### Post by bodhi.zazen on 2008-03-10
1. Yes.

2. Yes.

Take a look at Samba or NFS.

---

### Post by BlizzofOZ on 2008-03-10
Thanks for the quick reply...

What is the difference between 7.10 and 6.06 LTS?  Which one would suite my needs?

---

### Post by bodhi.zazen on 2008-03-10
Ubuntu is numbered by year.month

so 6.04 was released in april of 2006, so 7.10 is "newer"

The LTS versions are supported for longer then the non-LTS releases.

IMO, if you are running just a headless file server, go for the LTS release. FYI 8.04 will also be a LTS and there are plans to allow direct upgrade 6.04 -> 8.04.

Last, the server install boots to a command prompt, no GUI 

o.O

---

### Post by BlizzofOZ on 2008-03-10
Thanks again... I appreciate you answering as I'm sure this has been asked many times!

---

### Post by BlizzofOZ on 2008-03-10
Another question:

If ran a a backup on my Win XP system, would I be able to save the backup file to the Ubuntu server?  And would that backup app be able to see and use that file?

I know this sounds just like what I'm asking above, but just covering my bases.

---

### Post by bodhi.zazen on 2008-03-10
Not sure about that one, I advise you test any back-up scheme before you assume it is working.

---

### Post by mrsteveman1 on 2008-03-10
I'm going to save you a lot of time here and suggest you stay away from NFS if you need to use Windows machines on the network. Microsoft at one point had a services for Unix package available (for xp pro only, had to be hacked for home) which let you use NFS shares, but it wasn't all that easy to use and not reliable, so stick with SMB and Samba. The Vista version of this NFS client requires some kind of user mapping server, but I haven't played with it long enough to figure it out, i just stick with SMB since it works well.

Because of the way SMB works in windows, anything you can do to a drive you can do to an SMB share over the network. I use my ubuntu server as a backup target for my itunes library (using an rsync script), and as a backend store for media files like video etc, it all works perfectly, and even fairly high res video plays over the network just fine.

If your only intent with this machine is to setup a file server, the server edition should work fine unless you are REALLY uncomfortable with the command line, but a lot of server tasks will need the CLI anyway even if you do have GUI installed.

---

### Post by BlizzofOZ on 2008-03-11
mrsteveman1,

I haven't done any research yet between Samba and NFs, but I'll keep that in mind.

I'm a mainframe programmer, working on HP 3000's and do command line functions ALL the time... so, it is just a matter of learning the commands and what they do.

---

### Post by louieb on 2008-03-11
> **BlizzofOZ said:**
> ...If ran a a backup on my Win XP system, would I be able to save the backup file to the Ubuntu server?  And would that backup app be able to see and use that file?...

Should not be a problem. A Samba share  is a lot like sharing files and folders in a Windows workgroup.  

18 years IBM mainframe programmer here. A lazy one at that.  for a home network : if it has 512MB ram or better : I'd go ahead a  put the 7.10 desktop on it. You can still install and use any software you could put on the server version. Even use the CLI to to set everything up. But some things have a GUI setup and it just makes it easier. Good Luck.

From what I've read NFS is for *nix to *nix sharing only. Don't think there is an NFS client for windows.

---

### Post by BlizzofOZ on 2008-03-11
Yep, I'm a dinosuar too... done work on IBM too.  Mainly COBOL... teaching myself Java.

Yeah, have an older P4 2gz (I believe) with 1gb of ram.

I thought the server version didn't have a GUI.  Or is that something you can install later?

Curious also on how OS upgrades work?  bodhi alluded that 6.04 will be upgradable to 8.04... will 7.10 also be?  And how does that work?  Download iso and upgrade... connect to internet and download upgrade file(s)?

---

### Post by bodhi.zazen on 2008-03-11
+1 samba. There is a nfs client for windows , I have set it up, worked well, took about as long as samba + a little reading.

Here is are some links :

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

[http://ubuntuforums.org/showthread.php?t=310168](http://ubuntuforums.org/showthread.php?t=310168)

---

### Post by louieb on 2008-03-11
> **BlizzofOZ said:**
> ...I thought the server version didn't have a GUI.  Or is that something you can install later?...

the server doesn't come with a GUI. Can add one after the install.  or do a desktop install and add the server stuff to it.  

> **BlizzofOZ said:**
>  Curious also on how OS upgrades work?...
I don't know for sure. 8.04 is the second LTS release so this will be the 1st time there had been a LTS to LTS upgrade path.  My guess is that it will work the same way as up grading from 7.04 to 7.10. That is the update notifier will inform you that there is a new release. Do you want to upgrade? Click yes and away you go.  

> **bodhi.zazen said:**
> ...There is a nfs client for windows... 
:popcorn:Just what I need... another way to waste my my time playing with Linux. 
> "I am not the only person who uses his computer mainly for the purpose of diddling with his computer."
-- Dave Barry 1994

---

### Post by guilly on 2008-03-11
+2 for SAMBA, Mainframe programmer as well. But i'm no Dinosors just yet...

---

### Post by Oldsoldier2003 on 2008-03-11
> **louieb said:**
> the server doesn't come with a GUI. Can add one after the install.  or do a desktop install and add the server stuff to it.  


I don't know for sure. 8.04 is the second LTS release so this will be the 1st time there had been a LTS to LTS upgrade path.  My guess is that it will work the same way as up grading from 7.04 to 7.10. That is the update notifier will inform you that there is a new release. Do you want to upgrade? Click yes and away you go.  


:popcorn:Just what I need... another way to waste my my time playing with Linux.

its been said a few times that they plan a direct upgrade path for 6.06 LTS to 8.04  LTS and theres no rush since server is supported till 2011 lol!

---

