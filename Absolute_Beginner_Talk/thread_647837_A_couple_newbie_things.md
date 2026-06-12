---
title: "A couple newbie things"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by Zaopunk on 2007-12-22
Ok, so I have a couple of issues I am running into. 
I am trying to shed the evil empire from my computer, but I want to be sure everything works well before I make the plunge (Installing 7.1 Gutsy) . I am running into a few problems along the way as of yet.
First of all, I am running on a 2.6ghz 1.5g of ram, and running on 3mg DSL. I also did a full install on my old celeron 366 machine. Here are some problems I have.

1. Internet - The connection seems slow and irresponsive. In all actuality this is one of the few sites that actually works fairly well. Even the google taskbar that came with this release does not allow me to search, I simply time out.

2. Installation and upgrades - One of the only things that has kept me from just saying the heck with it and switching over is my MP3 player (Creative Zen Vision: M 30G) I was told to try Amarok by a friend, unfortunately when I go to upgrade, [from add/remove] it gives me the message that i386 is not supported or requires special hardware. So are you telling me that I can only use the software that came with the release. (as everything says this in the menu) or is it just a case of needing to find drivers.

3. Installation using the Live CD I still have not gotten to work, I used a copy given to me by the University Surplus store here in town and got it to work. Then tried the Live CD to no avail. Getting an error message of [The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed.]

Any and all help is very appreciated, thank you for your time, and hopefully I'll be free of the monopolizing memory horde that is on my other hard drive soon.

---

### Post by spiderbatdad on 2007-12-22
3. I  would suggest downloading your own iso and burning it at a slow speed. Then try that live cd. If you are offered options on creating the cd choose image not "with file."

2. There are numerous media players in the open source community. Some will make you jump for joy.

1.The internet issue is more than likely a quirk. Your Browsing experience should be normal or better, ultimately.

---

### Post by Zaopunk on 2007-12-23
Ok. So I re-downloaded a new copy, burned at 4x, and went through install. Unfortunately, when I rebooted I still had my old username and password and the same error messages. So I don't know if it installed OVER the old copy or if it installed somewhere else and won't let me log in.
Is there a way I can just format the HD to make it clean of the old copy of linux, so that I know the new install will be the only one?

---

### Post by Ripfox on 2007-12-23
When you get to the partitioning part, choose the option to use the whole hard drive.

---

### Post by Ertai87 on 2007-12-24
For the internet thing, I had the same problem.  Look in the output of sudo lspci -v and you should see the type of card (wireless or wired) that you're using.  Chances are the driver you're using isn't optimized for your hardware.  Find a better driver for your card and you should see a significant improvement.

---

### Post by Zaopunk on 2007-12-24
Thank you all for your help. See you in a bit.

---

### Post by Zaopunk on 2007-12-24
Ok. well I tried to install again, using the entire HD, put in my username and everything, then it starts installing...then the screen just disappears...I think I'll just save myself some hassle and order the cds. :(

---

