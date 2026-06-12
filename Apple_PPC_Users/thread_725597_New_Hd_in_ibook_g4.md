---
title: "New Hd in ibook g4"
date: 2008-03-15
forum: Apple PPC Users
---

### Post by spkays on 2008-03-15
I just purchased a new samsung 80 gb hd for my ppc ibook g4. I put it in my ibook and ran the feisty fawn live cd and have run into many errors. Many applets won't run. I'm guessing I need to format the hd but I have no idea how. I've searched all day for help. Every once in a while the live cd won't load and i'll get the "/bin/sh: can't access tty: job control turned off" line. I had feisty working before this new hard drive. 
 
Thank you,
Sean

---

### Post by stream303 on 2008-03-16
Since the new drive is empty, have you tried installing Feisty onto the new drive, rather than run from the live-cd?  You may also want to give the "alternate" cd install a try.

---

### Post by spkays on 2008-03-16
Thanks for the advice. I'm downloading the alternate cd now. Another thread suggested typing the kernal name plus hda=noautotune. This successfully loaded the live cd. Now all of my applet not working messages don't appear, which is great. I'm going to try to install now.

---

### Post by spkays on 2008-03-16
The installation failed. This happened previously. It gets to 5% and the message says, "Creating ext3 file system for / in partition #3 of IDE1 master..."

Then this appears, "The attempt to mount a file system with type ext3 in IDE1 master, partition #3(hda3) at / failed."

I'm not sure what's going on.

---

### Post by stream303 on 2008-03-16
I've heard that when changing major components in your mac, you should zap the pram, nvram, and possibly do a power pmu/smu reset.

I've never swapped out any hardware on my machines, so I can't tell if it won't bring your machine back to life if it fails.

However, here's some info about it if you want to try it.

[http://docs.info.apple.com/article.html?artnum=2238](http://docs.info.apple.com/article.html?artnum=2238)

---

### Post by spkays on 2008-03-16
Thanks for the advice. I tried those things and it doesn't appear to help. I'm wondering if I can make the ibook become a slave to my MacBook. How would I do that if there is no OS on the ibook? I have the feisty live cd and the alternate cd is downloading right now. 
Here's some of the errors I'm getting:
ide-pmac lost interrupt, dma status: 8080
Buffer I/O error on device hda, logical block 0
hda: drive not ready for command.

Also, I can only boot successfully when I load "live hda=noautotune"

Thanks again,
Sean

---

### Post by spkays on 2008-03-23
I kept searching for answers. I decided to take the HD out and put it in an enclosure, attached it to my macbook and used Disk Utility.  I partitioned the HD and put it back in the ibook g4. I tried to load edubuntu live cd with no success. I then tried dapper. My applet issues continued but I had a successful install. When I rebooted my applet issues continued. After reading some other posts, I think my ibook g4 is too weak for ubuntu, which is weird, since I had feisty running perfectly before I changed HDs. I may have messed up the ram when I took it out.
I'm trying opensuse 10.3 now and if that doesn't work I'll try xubuntu 6.04.

---

### Post by Kasa on 2008-03-23
Its not that its weak, Ubuntu can run on much lower systems then xp or mac.
I am having similar problems with my HD, if anything dont give up on it, sometimes its something small that your missing. xD

---

### Post by spkays on 2008-03-23
Opensuse seems to be working great. It detects all of my ram, so my issues from before weren't a ram problem. I think it was a bad connection somewhere that I happened to fix when I reinstalled my HD.

---

### Post by ipstone on 2008-05-15
Hi, 

Does suspend to RAM works in opensuse 10.3 with your ibook G4?
I am thinking of switching to linux on my ibook G4 as well

thanks

---

