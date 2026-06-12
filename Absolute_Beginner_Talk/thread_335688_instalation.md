---
title: "instalation"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by Blackbirdman on 2007-01-10
Not even a new recruit yet as I can't seem to load Ubuntu 6.06 from the disc.
I used Partion Commander to create a linux partion, that at least is fine. 

However, when I select the linux option with the OS disc in the CD drive it doesn't kick in. Any ideas?

Help please

---

### Post by nonpareilpearl on 2007-01-10
What did you use to burn the CD? Make sure that if you were using something like CD Burner XP Pro (free, Windows burning program that is nice) that you selected that you were burning an IMAGE (img) file. If you don't then the computer won't recognize it as a boot file. If you are unsure how to do this I would recommend downloading imgburner (a very small program, as it only has one purpose):
[http://www.imgburn.com/](http://www.imgburn.com/)

There is also Infra Recorder, which is listed on the Ubuntu download site (under "CD burning instructions"):
[http://infrarecorder.sourceforge.net/](http://infrarecorder.sourceforge.net/)

---

### Post by meng on 2007-01-10
Likely problems:
1. Corrupted download file: do md5sum check on the iso
2. Burned the CD wrongly (i.e. copied the iso file rather than extracting the filesystem from the iso): check your CD to see if there is a filesystem on it, if not burn another one FROM the iso
3. Bad burn: reburn at lower speed

[www.psychocats.net/ubuntu/iso](www.psychocats.net/ubuntu/iso)

---

### Post by nonpareilpearl on 2007-01-10
Good point I didn't really think of those :) I just assumed that it was the img thing because in all my zeal to get Ubuntu I didn't select "burn IMAGE" and my computer didn't recognize it as anything more complex than a txt file :-X but don't tell anyone ;)

---

### Post by Blackbirdman on 2007-01-10
Hi Nonpareilpearl,
the disc is direct from Ubuntu by post.
Sorry not to answer quicker I only just found the thread setting.

---

### Post by meng on 2007-01-10
Okay, thanks for clarifying.
Now, back to your original message, what is it that doesn't "kick in"? Please explain in more detail exactly what happens from the time you boot.

---

### Post by Blackbirdman on 2007-01-10
I have an Ubuntu istalation disc (by post), my reading of it is that it is a live instalation disc which should load as the computer starts.

I set up, using Partition Commander a linux partition, which worked, with the idea that when I opt for and open that partition the Ubuntu istalation will boot up and install on this prepared partition. No joy.

---

### Post by Blackbirdman on 2007-01-10
All that happens is I am told that the new Linux drive has no operating system, which I knew really.

Is there another boot disc I should have?

---

### Post by meng on 2007-01-10
I'm sorry, I'm going to repeat myself because I still don't understand how far you're getting. Forget about what you did with Partition Commander, that doesn't interest me right now. Please explain - in excruciating detail if necessary - exactly what happens from the moment you try to boot from the Live CD.
EDIT: didn't see your last post - sorry.
Just checking - is the BIOS configured to boot from the CD before the hard drive?

---

### Post by Blackbirdman on 2007-01-10
Hi Meng,

I would guess the sequence is Disquette, Operating system, CD drive.

---

### Post by meng on 2007-01-10
1. Don't guess! It's hard to help if we have to guess! Enter your BIOS and check it!
2. If when you do that, the CD-ROM is not first, then make it first!

---

### Post by TooRight on 2007-01-10
You'll have to change the boot sequence to boot from cd first, then reboot your comp with the ubuntu cd in the drive

---

### Post by Blackbirdman on 2007-01-10
Thanks Tooright/Meng,
I will try to refigure the boot proceedure, what you say sounds very likely.

All for now.

---

