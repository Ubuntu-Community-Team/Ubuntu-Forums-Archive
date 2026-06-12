---
title: "New to Ubuntu... [Resolved]"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by Goblin King on 2006-12-14
Just inherited a dell 4100 with a wiped hard drive.  Decided to try Ubuntu, burned the ISO, dropped it in the cd drive, and no boot.  Do I need a boot disk first, or is there a way to use the Ubuntu disk to boot and load the o/s?  I have BIOS set to boot from cd first.

---

### Post by jimrz on 2006-12-14
did you burn the iso "as an image" or just burn the file to cd?

---

### Post by Goblin King on 2006-12-15
I followed the install directions.  I used Infra Recorder and selected 'Burn Image'.

---

### Post by aysiu on 2006-12-15
Just to be sure... when you click on the CD, do you see one big file or a bunch of files and folders?

---

### Post by Hacked.Alias on 2006-12-15
Go to your BIOS and select boot from disc.

---

### Post by aysiu on 2006-12-15
> **Hacked.Alias said:**
> Go to your BIOS and select boot from disc.
I think the Goblin King already did: [quote=Goblin King]I have BIOS set to boot from cd first.[/quote]

---

### Post by Goblin King on 2006-12-15
Boot from disk as in floppy? I have it set to boot from the cd first, then the floppy.


As for the disc, when I check it on my other PC, it says it's inaccessible.  Is this what the instructions mean about burning it more slowly?

---

### Post by Hacked.Alias on 2006-12-15
Yeah, sorry, I didnt read that. I dont think he burnt it right then. From what I read he burnt it as one would normally burn an ISO, burn image onto disc. If that's correct, I dont see what the problem could be.

No, boot from CD, you did it right. 

Try downloading a free trial of Nero and redownloading Ubuntu. The burn it as an ISO (stated above) in Nero. That should work.

---

### Post by aysiu on 2006-12-15
There could be a few problems here.

1. The ISO might have corrupted during download.
2. The ISO might have corrupted during burn.
3. Infra Recorder might have screwed it up somehow (I've never used that program before)
4. You have a hardware failure
5. Your BIOS *says* it's trying to boot from CD first, but it's ignoring CDs.

I think the first thing you should do is make sure your ISO didn't get corrupted during download. This tutorial takes you step by step on that:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Goblin King on 2006-12-15
I checked it with the md5 prog and it said it's okay.  The light flashes on the cd drive as it tries to boot, so I think it's working.

Like I said, when I try to look at the disc on my working pc, it says the disc is inaccessible.  I think the burn was bad.  Will try another disc and see what happens.

Thanx for the quick responses everyone.

---

### Post by aysiu on 2006-12-15
Try to burn at 4x if possible. Or 8x if you have to.

---

### Post by Goblin King on 2006-12-15
The lowest I can burn it is 12x.  I'm in the process now.  

/crosses fingers

*EDIT* Nope, same thing; unable to access.  Gonna download CDBurnerXP and try it.  If not, I've got a disc ordered....

---

### Post by flimflam on 2006-12-15
Good luck.  Yeah, I have had problems with cheaper discs in the past.  Nero usually does me justice.  Just make sure that you are burning a true image.  Also, make sure that the boot sequence is correct; make sure that you choose the right optical drive also for the boot.  It may seem trivial but I know we have all troubleshot pcs only to realize the easiest suggestion (try the power cord) was the answer.

I say all this because all my systems have multiple optical drives and HDDs.  I am kind of a hardware nut, and when I don't put the correct settings in the BIOS, the PC will try to boot from the wrong drive.

---

### Post by Goblin King on 2006-12-15
Yay! CDBurner did it for me.  It's loading in the other PC now.  Again, thanx to all for the quick and helpful responses.  If the rest of my Ubuntu experience is as pleasant, I know I'll enjoy it!:-D

---

