---
title: "Edgy won't boot reliably."
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Foxblood on 2007-03-22
Greetings, I have a problem with my Edgy install. This install is about 6 weeks old and about 3 weeks ago when I booted Edgy, it stopped just after the progress bar started. I had to disconnect the power to enable reboot. At the time I thought it was an anomaly. However, the problem has not only persisted but is getting worse. A week ago 2 of 3 boots were succesful, now I'm lucky if 1 out of 3 succeeds. Because it's graphical, I don't know what's causing the problem. 
Any help would be greatly appreciated.

---

### Post by wpshooter on 2007-03-22
Did it seem to run basically error free for those first 3 weeks ?

Could be any of **MANY** things.

Perhaps you have an intermittent hardware problem.

How old is the system and it's various components.  Are the components quality components ?

Have you moved the computer lately ?

Have you tried reseating the video card ?

Have you downloaded the manufacturer diagnostic software for your hard drive and tested the integrity of the drive ?

---

### Post by iconfly on 2007-03-22
Hi,  I'm just a beginner like yourself.  It does sound like a hardware recognition problem.  Have you added anything recently?

Try opening a terminal and typing   dmesg   into it.

This might give you a clue to what is goin on.


Good luck!

---

### Post by rbprogrammer on 2007-03-22
first off, i'm not sure what is wrong with your system.  but the error sounds like one that i had awhile ago.  where it just hangs up during boot.  to fix my problem i had to run the command:
```

sudo tune2fs -c **1** /dev/hda1

```
this makes it so that at every boot it checks the filesystem. i have no idea why this worked for me, but you may want to try it.  should it work, it will take a bit longer to boot.  but for me it would definitely boot.

that is assuming the linux files are on the first partition of your first IDE hard drive

---

### Post by Foxblood on 2007-03-22
> **wpshooter said:**
> Did it seem to run basically error free for those first 3 weeks ?

Could be any of **MANY** things.

Perhaps you have an intermittent hardware problem.

How old is the system and it's various components.  Are the components quality components ?

Have you moved the computer lately ?

Have you tried reseating the video card ?

Have you downloaded the manufacturer diagnostic software for your hard drive and tested the integrity of the drive ?

What's the diagnostic software you mentioned?
Oh, and there's been nothing added, nothing taken away. System is old but has always been reliable. I can't really speak about the quality of the components. Mostly familiar names. But I feel they've proved their mettle by surviving 4 1/2 years of intensive use.

---

### Post by Foxblood on 2007-03-22
> **iconfly said:**
> Hi,  I'm just a beginner like yourself.  It does sound like a hardware recognition problem.  Have you added anything recently?

Try opening a terminal and typing   dmesg   into it.

This might give you a clue to what is goin on.


Good luck!
 Did that and got a lot of information that I don't know how to interpret. All seems well. No blatantly obvious problems. I was going to cut and paste the results but it's a long file. But surely if I can do this, then the system has booted correctly? It's when it doesn't boot correctly that concerns me and when that happens I've got nothing to work with.
Is there any particular part of these results that I should be paying attention to?

---

### Post by Foxblood on 2007-03-22
> **rbprogrammer said:**
> first off, i'm not sure what is wrong with your system.  but the error sounds like one that i had awhile ago.  where it just hangs up during boot.  to fix my problem i had to run the command:
```

sudo tune2fs -c **1** /dev/hda1

```
this makes it so that at every boot it checks the filesystem. i have no idea why this worked for me, but you may want to try it.  should it work, it will take a bit longer to boot.  but for me it would definitely boot.

that is assuming the linux files are on the first partition of your first IDE hard drive

Couldn't find valid filesystem superblock.

How can I check that I'm checking the right partition?

I don't care if it takes a little longer to boot. As long as it boots.

---

