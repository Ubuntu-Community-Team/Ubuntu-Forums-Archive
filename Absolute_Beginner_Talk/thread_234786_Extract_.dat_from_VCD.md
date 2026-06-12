---
title: "Extract .dat from VCD"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by JcZndeR on 2006-08-12
I need to get a file with the extension .dat from a VCD, and since copying them doesn't work I am stuck.  I realize that there are many threads about this but stupid me I couldn't get them to work.  I tried CDFS but I couldn't get that to work as you can see from this, [http://ubuntuforums.org/showthread.php?t=233392](http://ubuntuforums.org/showthread.php?t=233392).  I also read [http://www.mplayerhq.hu/DOCS/HTML/en/vcd.html](http://www.mplayerhq.hu/DOCS/HTML/en/vcd.html) and many others but still failed.  I am trying to get it from a dvd drive at /media/dvdrecorder and the file is at ./mpegav/avseq01.dat.  I normally can figure it out for myself but I am having trouble with this for some reason, if someone can give me a more step by step instruction or tell me howto use the syntax because it is seriously giving me trouble, I would be most greatful.  :D   I couldn't figure out how to use the vcdimager and stuff like that.  I am not really happy with the ubuntu mutimedia area but I can't really complain.  (Sound is STILL broken and video playback of local files are tinted blue.)
Thanks!!

Edit:  Oh yeah..  And also I seem to get the input/output error alot.  And btw, it works perfectly on windows so it isn't a disk problem.  This is really sad cuz i can't even get it to play.

---

### Post by Gringo11 on 2006-08-25
Try
vcdxrip --cdrom-device=/dev/cdrom --rip
That should rip the *.dat file into your home-directory.

---

### Post by JcZndeR on 2006-09-04
> **Gringo11 said:**
> Try
vcdxrip --cdrom-device=/dev/cdrom --rip
That should rip the *.dat file into your home-directory.

lol
havent been on in a while
i am not working on that anymore
but i will try
thx

---

### Post by bernardfrancois on 2007-07-03
Thanks, it worked for the VCD I needed to rip here.
I now have an mpeg file. I wonder if there was any recompression causing quality loss or not, otherwise I would have liked to have it in avi (xvid) format for more efficient storage.

---

### Post by libos on 2007-08-11
I manage to use vcdimager and mpgtx to extract the dat files from VCD.

[http://bsling.blogspot.com/2007/08/ripping-dat-files-from-vcd-to-mpeg-in.html](http://bsling.blogspot.com/2007/08/ripping-dat-files-from-vcd-to-mpeg-in.html)

---

### Post by tahaselim on 2007-08-25
> **bernardfrancois said:**
> Thanks, it worked for the VCD I needed to rip here.
I now have an mpeg file. I wonder if there was any recompression causing quality loss or not, otherwise I would have liked to have it in avi (xvid) format for more efficient storage.

This worked for me too, Thanks!

But I think there was quality loss, though not much.

Taha Selim

---

