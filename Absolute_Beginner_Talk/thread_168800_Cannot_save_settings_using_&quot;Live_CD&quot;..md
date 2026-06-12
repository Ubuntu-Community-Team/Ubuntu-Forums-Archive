---
title: "Cannot save settings using &quot;Live CD&quot;."
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by thornmastr on 2006-05-01
Greetings,

As is probably painfully obvious I am a total novice to Ubuntu and Linux. By way of background and training I am a Visual Basic 6.0 designer who has spent many many years confined, happily so, within a Microsoft environment. Unfortunately, MS and I are about to part company and after investigation Linux appears to be the way to go. An associate suggested I strongly pay attention to Ubuntu specifically because for Linux it is very user friendly, and I can use the live CD and not give up my Windows Security blanket. “Oh joy. Oh raptures” exults I and I am off and running. I burn the iso correctly, smack that saucer in the player and reboot my system and my mouth drops to knee level. This is absolutely fantastic. It installs with minimal intervention from me. I am thinking, this is really dazzling. So, installed and running I set out with on line manual to learn and play. Firefox is my browser of choice anyway so that is no problem, and installing Thunderbird is very easy.  I then used user/groups to define my own user name, password, admin rights etc. All relatively easy. I set up a play directory, created a couple of folders, use OpenOffice writer to build some little WP files, I found myself recalling things from a number of Unix texts I had years ago and things are really beginning to make sense. So, at that point I set up what I wanted on my login screen; used the save settings on the shut down window, and shut everything down. Sometime during the night I wondered,” Where did all my settings get saved.” And, since I am running a live CD and have not partitioned my HD, how is Ubuntu saving all my settings. Was it even saving them. How does Windows know what belongs to Linux. How does Linux know what belongs to Window.  This morning my first clue when I booted off the live CD, there were no options to use saved settings which makes me think there were no saved settings. It couldn't have saved them to the CD since I used a Read many write once CD. 

Specific questions. How do I use the live CD while not blowing out Windows. I am very reluctant to partition since I still have a number of work in progress development projects on my Windows system and do not want to loose them; yet I need to set up and use Ubuntu on the same system until I am certain it is time to blow away XP forever.

Suggestions, comments, and “Do it this way, stupid” instructions are all welcome.


Robert Berman

---

### Post by Sef on 2006-05-01
In general, you can't save setting on live cds.  

> How do I use the live CD while not blowing out Windows.

Just don't partion or do anything to the hard drive.  Using the internet, or writing an email won't affect your hard drive at all.  

> I am very reluctant to partition since I still have a number of work in progress development projects on my Windows system and do not want to loose them; yet I need to set up and use Ubuntu on the same system until I am certain it is time to blow away XP forever.

I would get another computer to put Ubuntu on.  Usually there won't be any problems, but at times XP can get trashed during an Ubuntu install.  And I hope you back up all your files anyway.

---

### Post by dasunst3r on 2006-05-01
The LiveCD doesn't save settings anywhere.  They are *lost* as soon as you turn off your computer.  I could imagine your frustration of finding that out.  Believe it or not, you can actually run a Linux installation inside Windows using VMware and play with Linux on your spare time!  Get the free VMware Server for that at [www.vmware.com](www.vmware.com)

Once you get up and running there, I would suggest searching for "Automatix" on this forum.

---

### Post by Randomskk on 2006-05-01
If you can partition or get a new hard disk, you could try dual booting.
You install Ubuntu on one hard disk, leave windows on the other and you get the choice at boottime which you want to load - linux or windows.

That way is great for using both and having them be full installs, but of course it needs some free hard disk space or a second hard drive.

---

### Post by muep on 2006-05-01
You could store your documents in an external Fat32-formatted USB thumb drive.

---

### Post by thornmastr on 2006-05-04
I  appreciate all the information and suggestions I received. The  one which seemed to be the most appropriate for my immediate situation was the suggestion to install VMWare server which I did and then installed Ubuntu within VMWare. Unfortunately, the response time and the quality of the display was far from ideal so the next morning, I saved my critical directories on Windows, and using the “Ubuntu + NTFS” as my guide, partitioned my machine for a dual boot. There were a few moments where I was a tad nervous and a bit perplexed but everything worked reasonably well and now Ubuntu and Windows share a hard drive and, as time permits, I am learning the intricacies of Ubuntu. I was able to easily connect to a network printer, and now I am trying to install Real Player which seems to be a bit of a challenge but the forums are very helpful. 

Again, thanks to everyone who has helped me with this endeavor.


Robert Berman

---

### Post by sailor2001 on 2006-05-04
google automatix and you can get your player+codecs etc.........Arnie made it real easy for all of us.

---

### Post by catlett on 2006-05-04
If you follow the links in my signature, you will find a website with ext2 drivers and a forum thread about ntfs in ubuntu. What it amounts to is you can install the ext2 drivers in windows and see and write to your ubuntu partition, as well as mount your windows ntfs partition in ubuntu and read and write to it.
The ext2 drivers work real well. Just read it through and sometimes on reboot you have set up again. The ntfs in linux is still in it's infancy and all the bugs aren't worked out but I haven't had any problems. Just be aware there could be problems.

PS with your background you don't need automatix. Go here [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) and if you have any install problems go here [http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by jackn on 2006-05-13
In Ubuntu 6.0.6 beta, it IS possible to save your settings while using a live CD.

Please look up:

[https://wiki.ubuntu.com/LiveCDPersistence](https://wiki.ubuntu.com/LiveCDPersistence)

Haim

---

