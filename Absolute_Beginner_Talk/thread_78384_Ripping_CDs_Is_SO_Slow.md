---
title: "Ripping CDs Is SO Slow?"
date: 2005-10-18
forum: Absolute Beginner Talk
---

### Post by kimvall on 2005-10-18
Hello all, I've been trying to convert CDs to mp3, but I it so VERY slow. On my Windows machine I did so at 10-20x, but here I get an average speed of 0.5-1x. I MUST be doing something wrong, right?

What software do you all recommend?

Thanks in advamce.

---

### Post by jasmuz on 2005-10-18
Did you check if you have DMA for that CD drive enabled?

---

### Post by davmac on 2005-10-18
you can do this by opening up a terminal window and typing

"hdparm -v -i /dev/cdrom"

Somewhere in the first couple of lines you should see something like "using_dma = 1 (on)".

HTH,

Dave Mac

---

### Post by ChrisTheGeek on 2005-10-18
If it isn't on, use the following command to turn it on:

sudo hdparm -d1 /dev/cdrom  

You can look here for more information:

[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

---

### Post by Jenda on 2005-10-18
Yes, first of all ensure your DMA is on. If not, you can:
[QUOTE=Ubuntu FAQ Guide]11.&#8195;

How do I speed up CD/DVD-ROM access (enable DMA)?

       1.

          Assuming that /dev/cdrom is the location of CD/DVD-ROM
       2.

sudo hdparm -d1 /dev/cdrom 
sudo cp /etc/hdparm.conf /etc/hdparm.conf_backup 
sudo gedit /etc/hdparm.conf

       3.

          Append the following lines at the end of file

/dev/cdrom {
dma = on
}

       4.

          Save the edited file (sample/hdparm.conf_speedupcddvdrom)

[/QUOTE]
And now, if the problem persists, download&install GRip ```
sudo apt-get install grip
``` Run GRip and if it still rips slow, turn off paranoia, extra paranoia and/or scratch detection/correction in the Config > Rip tab. You just have to click the tabs in GRip.

---

### Post by muted on 2006-02-05
So... my DMA is on... Using grip... all paranoia and scratch repair and so on is off...

0.5 X ripping speed

help someone?!

---

