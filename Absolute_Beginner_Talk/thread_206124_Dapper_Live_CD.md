---
title: "Dapper Live CD"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by Pavilion on 2006-06-29
I read many times that it takes 256MHz to run Dapper Live CD.  Well I popped the CD into a 500MGHz machine 200MB Ram.  Yes, the CD is slow to load, but once it's up the performance is not that bad.  I believe the slow performance is more a function of  CPU speed not the ram, of course more ram is good.  Also, when it gave an option to strike an [F] Key the message stated 128MB Ram is all that's required.:cool:

---

### Post by aysiu on 2006-06-29
It's probably a combination of CPU and RAM, but RAM is a huge thing.

---

### Post by muep on 2006-06-29
I've used it on a 600 MHz machine with 128 MB. It's very slow and load times are long.... On a 350 MHz box with 512 MB It's actually not like a livecd, but more like an installed one. Still load times, but not nearly as much waiting. Also after loading things, it feels snappier.

---

### Post by Jucato on 2006-06-29
Like what aysiu said, both CPU and RAM are factors to consider, but RAM is the most important one. The Live CD uses RAM both as a temporary "hard drive" and as a memory resource. If I'm not mistaken, it first allocates the temporary filesystem and uses the leftovers for memory usage.

---

### Post by Pavilion on 2006-06-29
[QUOTE=muep]I've used it on a 600 MHz machine with 128 MB. It's very slow and load times are long.... On a 350 MHz box with 512 MB It's actually not like a livecd, but more like an installed one. Still load times, but not nearly as much waiting. Also after loading things, it feels snappier.[/QUOTE]

It seems right that a machine would actually be snappier with more ram because more information is carried within random access memory.  Your experience with the 350MHz with 512MB machine seems to verify this.:smile:

---

### Post by confused57 on 2006-06-29
Ram is probably the most important component for using the LiveCD, possibly the CPU & ram for a hd installation...starting Firefox results in almost 90% CPU usage with my 500 Mhz computer, 256 Mb ram.

---

### Post by enyaw on 2006-06-29
[QUOTE=confused57]Ram is probably the most important component for using the LiveCD, possibly the CPU & ram for a hd installation...starting Firefox results in almost 90% CPU usage with my 500 Mhz computer, 256 Mb ram.[/QUOTE]

I'm surprized at the 90% CPU usage for Firefox, and I thought Firefox was lean and mean.  On my 500MHz/200MB machine it does come up slow and now I know the reason:(

---

### Post by Jucato on 2006-06-29
AFAIK, when a program starts up, it usually takes a big amount of CPU resource. But this goes down once the program is fully loaded into memory. I'm not absolutely sure, though. That's just what I heard.

---

### Post by cjssmo on 2006-06-30
Try dawn small linux it works well on older machines, you can set it up to run from RAM.  It's only 50mb and it is fast.  Check it out it might be what you need.  I thought it was a joke but boy was i suprised

---

### Post by enyaw on 2006-06-30
[QUOTE=cjssmo]Try dawn small linux it works well on older machines, you can set it up to run from RAM.  It's only 50mb and it is fast.  Check it out it might be what you need.  I thought it was a joke but boy was i suprised[/QUOTE]

I still have my fist computer [in the basement]. Original... Packard Bell.  5.0 MS Dos. 125MB hard drive. 10/20MHz.  2MB Ram.

Years ago I increased the ram to 16MB and loaded it with 3.1 Windows.  It was tricky But I actually connected to the internet with its 14.4 modem.  Many of the web sites  would not let me on because of the slow speed.  Anyway, if I can figure out how to burn an DSL ISO image to a 1.44MB floppy I'll try DSL.  If it works I'll post.

Thanks for the idea:grin:

---

### Post by mority on 2006-08-16
I just booted the Dapper installation CD on a AthlonXP 2000+ (1666 MHz) with 256 MByte RAM and it's a really pain to install because it is so slow.

Of course I understand that 256 MByte of RAM is very sparse for running a live CD, but I think there should be an easy way to fall back to a text mode or framebuffer driven installer in Edgy Eft.

If booting the live CD will remain the only way to install, Ubuntu will exclude unexperienced users (which are not able to install from the server CD and install desktop system manually) with slower machines. And excluding people from using free software without any grave reasons is not good the karma...

---

