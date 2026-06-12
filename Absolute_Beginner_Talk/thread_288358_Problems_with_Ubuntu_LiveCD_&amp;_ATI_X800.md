---
title: "Problems with Ubuntu LiveCD &amp; ATI X800"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Iray on 2006-10-29
Hi everyone,
I'm absolutely new to Linux and to this forum.
I have a serious problem when booting my Ubuntu 6.10 LiveCD, i have an ATI x800 graphics card and the booting stops without saying nothing.. simply my monitor (Samsung SyncMaster via DVI) receives the command to go in standby mode, thus becoming black.
At this [url ]("http://www.ubuntuforums.org/showthread.php?t=190133") I have found a problem similar to mine, but i cannot use the method explained because i only have the place to insert boot options, not the command line, so i cannot write "sudo nano...".
I want to use my livecd and if all goes well to install ubuntu, please help me to fix this problem!

Thank you in advance, Iray

---

### Post by ReaderRat on 2006-10-29
Pardon me, Wrong Disc...I'll check...

---

### Post by Iray on 2006-10-30
Sorry, I haven't understood your reply...

---

### Post by Sef on 2006-10-30
A few questions:

1) Did you download the disk or get it from shipit?

2) If you downloaded it, did you md5sum it?

3) Have you tried the disk in another computer?

4) What are your computer specs? (ram, MHz, etc.)

---

### Post by normanc on 2006-10-30
I recently installed ubuntu and I have an ATI X850 card. I was in the exact same boat as you, and the only way I could get x-windows to start was to type the three sudo commands that was referenced about halfway down the forum post you linked to and started "Actually, it's a lot easier than that". After I did that, it was fine and worked fine. Doing what the guy in the first post recommended (in the linked url) didn't work for me either, only the one further down as I stated.

If, as I understand it, you want to "try before you buy", going by my experience this won't be possible. You'd somehow need to alter the Live CD with the proper ATI flgrx driver already installed and configured to be the active driver on your system. Whether or not this is possible by using ISObuster (or similar) after you download the ISO to unpack the image, alter it, repack it I don't know, and it's well beyond my linux know how to even suggest where one would start on such an adventure.

Someone more knowledgable may be able to help you, but I fear that checking MD5 hashes, reburning disks at 2.4x speed, etc. won't help you get past that initial hurdle that ubuntu simply cannot run "out of the box" on modern ATI cards without downloading alternative drivers.

I even tried using the standard "vesa" option in x-configure and it balked at that even.

---

### Post by rlozano on 2006-10-30
iray, did you try booting with safe mode using the live CD? its the 2nd option in the selection

---

### Post by Iray on 2006-11-11
I tried md5 ... all ok.
I tried safe mode ... the problem is the same.

Good news!!
I have a AMD64 3500+ with 1Gb RAM and I had these problems with Ubuntu64 LiveCD.
I tried to download and run Ubuntu-non-64 LiveCD and IT ALL WENT WELL!!!
No booting problems, the video driver automatically selected is VESA and i can try the wonderful Ubuntu.
But I'm sure I have that processor! However I tried the Ubuntu64 CD on another AMD64PC and it worked fine.

Ok, ok it's not a problem to use only 32 bit... now I have another problem! I didn't wanted to go off-topic here, so I've opened a new thread [here]("http://www.ubuntuforums.org/showthread.php?p=1743494#post1743494").
If you can help me with the configuration of my ethernet ADSL modem... you're welcome! :D

---

