---
title: "Mplayer Skipping"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2006-04-16
Hi everyone, 

I have Firefox 1.5 installed.  I had the same problem in 1.0.7 though.  When I view embedded video files, they skip.  The sound skips in and out and the film is choppy.  I checked the Mplayer setting, and the only thing I saw was the "double buffering" option, and it was enabled.

How can I fix this?

Thanks!

---

### Post by mishranurag on 2006-04-16
I have teh same issue. I have diabled ipv6 thing too :(
Anurag


[quote=brandoncolorado]Hi everyone, 

I have Firefox 1.5 installed.  I had the same problem in 1.0.7 though.  When I view embedded video files, they skip.  The sound skips in and out and the film is choppy.  I checked the Mplayer setting, and the only thing I saw was the "double buffering" option, and it was enabled.

How can I fix this?

Thanks![/quote]

---

### Post by brandoncolorado on 2006-04-17
*bump

---

### Post by GarethMB on 2006-04-17
I guess you can try turning DMA on. But it could just be down to your system specs too. Here is what the wiki says about DMA [https://wiki.ubuntu.com/DMA?highlight=%28DMA%29](https://wiki.ubuntu.com/DMA?highlight=%28DMA%29)

---

### Post by brandoncolorado on 2006-04-17
[QUOTE=GarethMB]I guess you can try turning DMA on. But it could just be down to your system specs too. Here is what the wiki says about DMA [https://wiki.ubuntu.com/DMA?highlight=%28DMA%29](https://wiki.ubuntu.com/DMA?highlight=%28DMA%29)[/QUOTE]

Thanks for the advice, but I believe that DMA is for optical drives.  This is only for embedded files in Firefox.  WMV mostly.  My system is sufficiently powerful, as the videos work in Windows, and I can play the most recent games because of a powerful video card.

---

### Post by GarethMB on 2006-04-17
[QUOTE=brandoncolorado]Thanks for the advice, but I believe that DMA is for optical drives.  This is only for embedded files in Firefox.  WMV mostly.  My system is sufficiently powerful, as the videos work in Windows, and I can play the most recent games because of a powerful video card.[/QUOTE]
My understanding of DMA is that it allows data to be transfered between RAM and hard drive without involving the CPU at all. Thus it is relevant to HDD as well.

But i could be mistaken, i only suggested it because for the sake of a single line in the terminal you'd be able to eliminate this as a possibility.

---

### Post by brandoncolorado on 2006-04-17
[QUOTE=GarethMB]My understanding of DMA is that it allows data to be transfered between RAM and hard drive without involving the CPU at all. Thus it is relevant to HDD as well.

But i could be mistaken, i only suggested it because for the sake of a single line in the terminal you'd be able to eliminate this as a possibility.[/QUOTE]


Oh sorry, didn't know that.  I tried to do this, followed the steps.  In the .conf file the DMA is on, but in the other it is listed as off, and won't turn on.

---

### Post by GarethMB on 2006-04-17
[QUOTE=brandoncolorado]Oh sorry, didn't know that.  I tried to do this, followed the steps.  In the .conf file the DMA is on, but in the other it is listed as off, and won't turn on.[/QUOTE]
What command did you use to try and enable it?

---

### Post by brandoncolorado on 2006-04-17
[QUOTE=GarethMB]What command did you use to try and enable it?[/QUOTE]

[QUOTE=GarethMB]My understanding of DMA is that it allows data to be transfered between RAM and hard drive without involving the CPU at all. Thus it is relevant to HDD as well.

But i could be mistaken, i only suggested it because for the sake of a single line in the terminal you'd be able to eliminate this as a possibility.[/QUOTE]

sudo hdparm -d1 /dev/hdc

---

### Post by GarethMB on 2006-04-17
That command *is* refferring to the CD-rom drive.

Try issuing the command for the relevant HDD partitions.
sudo hdparm /dev/hda
sudo hdparm /dev/hda2
sudo hdparm /dev/hda3

etc.

The output of these files will tell you whether DMA is enabled for these devices. If it is enabled then you can rule it out.

---

### Post by brandoncolorado on 2006-04-17
[QUOTE=GarethMB]That command *is* refferring to the CD-rom drive.

Try issuing the command for the relevant HDD partitions.
sudo hdparm /dev/hda
sudo hdparm /dev/hda2
sudo hdparm /dev/hda3

etc.

The output of these files will tell you whether DMA is enabled for these devices. If it is enabled then you can rule it out.[/QUOTE]

Enabled.

---

### Post by GarethMB on 2006-04-17
Ok. I take it that these videos play fine if they are downloaded to your hard drive first?

Ok, by messing around with the settings i was able to produce the same symptoms as you. I believe that using the ALSA sound setting produces jumping. Set audio output to ESD. Works for me :)

---

### Post by brandoncolorado on 2006-04-18
Now that you mentioned it, I have narrowed it down to only videos with sound.  I tried the ESA, MPEG, same problem.  I will try some others, hopefully I can find a solution.

---

### Post by Wolfi3 on 2006-04-20
=D> Switching to ESD solved this problem for me.  Cheers

---

