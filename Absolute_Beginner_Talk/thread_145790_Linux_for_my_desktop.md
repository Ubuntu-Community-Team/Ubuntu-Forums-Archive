---
title: "Linux for my desktop?"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by gt24 on 2006-03-17
Linux currently wages war for dominence of my laptop.  On my desktop though, I don't even think too much of using Linux.  Here is the problems I ran into, all pretty annoying...

A) Pocket PC, Windows Mobile 2003 SE...  yeah, this didn't really work all that great with Linux.  In fact, when I did get it working, Evolution has some nice outstanding bugs that kill any opportunity of my device playing nice with Linux...  hmmm....

B) NTFS... my drives are all NTFS and Linux has a small partition to live in.  I want to access the files on the NTFS partitions so I go ahead and mount them (eventually, once I figure it out).  Gnome places lovely icons on my desktop of the mounted drives...  I want those icons eliminated, without eliminating any future mounted devices icons...

C) Jump drive... well, I hear that files may or may not copy over to the jump drive, this may or may not work... essentially, I just heard about every single "iffy" statement ever in relation to jump drives...

D) Hardware temperature monitoring... no clue how... never found out much about this... kinda more critical for the dekstop...

E) WINE... won't work... enough said...  this program is annoying as heck!

F) Stuck between two worlds...  I want to be able to cross between Windows and Linux... which may mean that I need a FAT32 partition...  and I also need to keep my information safe in case I get annoyed and reinstall the Linux OS.  How do I accomplish this... and what is up with /home and alike mount points in general?  Besides, how can I mount a partition on install without having it nuked by an installing OS?  (note that by installing OS I moreso mean (k)Ubuntu)

Any help appreciated.

---

### Post by bluevoodoo1 on 2006-03-17
D. Hardware Monitor:

Your motherboard must be able to support this. If you are unsure you should be able to see within your BIOS. If there's some sort of power management area where you can see fan/temp levels, then you're in luck. With GNOME get lm-sensors and sensors-applet (sensors-applet will show your levels on the gnome panel) with Synaptic or with the command line. 

```
sudo apt-get install lm-sensors libsensors-dev libsensors3 sensors-applet
```

(I believe those are all the files associated with lm-sensors)

If you're using KDE, ksensors is the package you'ld look for. 

E. Wine
What program(s) are you trying to get to work with wine? Here's a short link...
[http://www.psychocats.net/ubuntu/wine.php](http://www.psychocats.net/ubuntu/wine.php)

F: > what is up with /home and alike mount points in general?
technically, if you reinstall or upgrade the system, having / on a separate partition away from /home, your data on /home should remain intact. I haven't tried it yet, but that's the idea.

---

### Post by Sef on 2006-03-17
> technically, if you reinstall or upgrade the system, having / on a separate partition away from /home, your data on /home should remain intact. I haven't tried it yet, but that's the idea.

I have reinstalled Ubuntu and was able to keep my data by having a separate home partition.

---

### Post by bluevoodoo1 on 2006-03-17
[QUOTE=Sef]I have reinstalled Ubuntu and was able to keep my data by having a separate home partition.[/QUOTE]

Good to know that it will work.

---

