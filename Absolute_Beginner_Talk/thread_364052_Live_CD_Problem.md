---
title: "Live CD Problem"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by DarcKnyt on 2007-02-17
(I tried posting this earlier, but I guess it didn't get saved.  Sorry for the repost if it's here already and I just can't see it.)

Hello, all!

I'm the epitomal absolute beginner with Linux, and I've even got a problem with a Live CD.  I'm hoping some of you will help, if it's possible.

I downloaded the i386 ubuntu and kubuntu distros, but neither of them will work on my machine.  The initial installation gets to the point "Configuring some drivers", then the screen goes blank (sometimes there's a cursor blinking), and I have no idea what's supposed to happen.  My understanding was that the live CD would boot to Ubuntu, but that's not happening.

Believing I had downloaded the wrong version, I tried using the AMD version too (I have an Athlon64 3700+ 2.2GHz processor).  It actually gave me an error message (which I didn't write down -- I will next time I see it), but still wouldn't load.

If anyone has any idea what might be happening and what I can do, that'd be great.

Thanks all!
DK

---

### Post by solar george on 2007-02-17
First of all,

What is the full spec of your machine - from the sound of it there is some unsupported hardware interfering with the hardware detection.

---

### Post by DarcKnyt on 2007-02-17
Full spec ... hmm, let's see ...

It has an ATI Radeon video card, 1GB RAM, DVD RW/CDW combo drive, CD drive, multiple card reader drive, model HP a1230n.  I'm not sure what else to provide you, but if you let me know, I'll be happy to find it and give it to you.

Thanks for replying!
DK

---

### Post by solar george on 2007-02-17
What an idiot I am..............

> (I have an Athlon64 3700+ 2.2GHz processor)

You need the amd64 version - or is that what you ment when you said the AMD version.

If so find that error message.

---

### Post by solar george on 2007-02-17
I've just googled for your computer model and people appear to have had problems with it - try using the amd64 alternate install cd (text mode) to get a running base system.

---

### Post by 67GTA on 2007-02-17
You need the AMD 64 version. What did you use to burn the iso image? What speed did you burn it at?

---

### Post by DarcKnyt on 2007-02-18
> **solar george said:**
> What an idiot I am..............



You need the amd64 version - or is that what you ment when you said the AMD version.

If so find that error message.

You're no idiot ... and yes, that's what I meant when I said I had the AMD version.  :)

---

### Post by DarcKnyt on 2007-02-18
> **67GTA said:**
> You need the AMD 64 version. What did you use to burn the iso image? What speed did you burn it at?

Hi, and thanks for replying ...

I used Sonic Digital Media Version 7 (came on the PC).  It burned at whatever the default was for the software/burner ... I think it was 8X?  Maybe.  I didn't notice.  I had the install program check the disk, and Kubuntu version showed 5 checksum errors, so I didn't use it.  The Ubuntu version didn't say anything about errors.

The first time I did it, I didn't do it correctly; I copied the ISO file to a disc.  The second time I did it correctly, though, and when I execute start.exe from the disc under XP, it gives me the intro slideshow.

Thanks again, and let me know if you suspect problems due to the burning software.

DK

PS - sorry, forgot to mention that the AMD 64 version failed, too ... there was an error message, but I didn't write it down.  I'll try it again and post the error message.

---

### Post by DarcKnyt on 2007-02-18
> **solar george said:**
> I've just googled for your computer model and people appear to have had problems with it - try using the amd64 alternate install cd (text mode) to get a running base system.

Okay, I'll try it in text mode and see if that helps, but ... like I said, I have NO idea what I'm doing in Linux, so if there's a command line I need to issue, I need to know what that is.  Can you assist with that, or is that somewhere in the documentation?

Thanks again Solar George, I really appreciate it.
DK

---

### Post by rsambuca on 2007-02-18
I am not quite sure that the 64bit version is appropriate for you if you are a complete first time user of linux.  The 64bit version, while it is fine after you have it set up, can be rather "finicky" to get things like flash working.

Rather, it sounds like the installation is hanging due to hardware recognition issues.

Try using the Live CD you have (that had NO errors) and press F6 boot options and try adding some of these and booting.
Add the following before the "--" and leave a space before the dashes:

ide=nodma

If that doesn't work, try adding all of these in:

irqpoll pci=noacpi noapic nolapic acpi=off

---

### Post by DarcKnyt on 2007-02-18
> **rsambuca said:**
> I am not quite sure that the 64bit version is appropriate for you if you are a complete first time user of linux.  The 64bit version, while it is fine after you have it set up, can be rather "finicky" to get things like flash working.

Rather, it sounds like the installation is hanging due to hardware recognition issues.

Try using the Live CD you have (that had NO errors) and press F6 boot options and try adding some of these and booting.
Add the following before the "--" and leave a space before the dashes:

ide=nodma

If that doesn't work, try adding all of these in:

irqpoll pci=noacpi noapic nolapic acpi=off

Wow, thanks!  I'll give it a try.  Where are the "--" found?  All I see is the blank, black screen, and sometimes, there's a blinking cursor.  I never see a prompt of any kind.

Also, I just tried the AMD64 disc again, and it gave me the error.  I wrote down as much of it as possible; the computer doesn't seem to like the graphics, so the error was scrolling vertically very, VERY quickly, and appeared to overlap horizontally.  Sorry if this isn't enough information:

Error 16: segfault at 0000000000000000 rip 00002aaaaabf3c50 rsp 00

... and that's all I can see.

Hope this helps; let me know if not.
DK

---

### Post by DarcKnyt on 2007-02-18
rsambuca, thank you!  Your suggestions worked; the first one, in fact (it wasn't necessary to try any of the others).

I was able to load and run the Live CD environment, but I wasn't able to get my wireless card working.  I'm off to do a search in the forums about THAT next.

Thanks to everyone for helping!

---

### Post by rsambuca on 2007-02-18
Glad it worked for you.  Just note that the ide=nodma option turns off the Direct memory access to the ide drives.  You will want to turn it back on after you have booted into the live CD before installing, or the installation will be very slow.

To turn on the dma,```
sudo hdparm -d1 /dev/hda
```
You will have to do this for each ide drive.  ie /dev/hdb, /dev/hdc...

---

### Post by DarcKnyt on 2007-02-18
Thanks again!

---

