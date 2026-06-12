---
title: "DVD Decryptor, DVD Shrink and Simple DivX"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-07-21
Upon putting in this thread title and searching for related threads, I found this HowT-o:
[http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/)

I assume this will work with Fiesty as well? It looks like it was written in 2005.

Also... what is the best thing to use for converting a DVD (.vob files after DVD Decryptor rips them to the HDD) into a DivX file?  I use SimpleDivx on XP, will it work in WINE with Ubuntu?  Or is there something better out there?

---

### Post by jimbob on 2007-07-21
I use k9copy to shrink DVD's and k3b to rip them to DVD.  Both are available using synaptic or apt-get in Ubuntu.

I don't know anything about Divx.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by kc5hwb on 2007-07-21
I have K3B already installed and I use it for burning, it will rip also?  I haven't used it but once or twice

---

### Post by jimbob on 2007-07-21
I guess I have to look up the definition of rip.  I don't do much of this at all so I tend to use the terms rip and copy interchangeably.   Sorry.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by kc5hwb on 2007-07-21
"RIp" generally means to read the files on a DVD, and rip them from the disc to either burn onto another DVD or place them on the Hard Drive.

---

### Post by reylafo on 2007-07-21
Both DVDDecrypter and DVDShrink work ok under WINE. But they work better together with "RIPit4ME", whose last version has "FixVTS' included.

---

### Post by kc5hwb on 2007-07-21
I assume "RIPit4ME" is available in Synaptic.

---

### Post by kinematic on 2007-07-21
The most simple tool for just ripping dvd's to your hdd is vobcopy.
The syntax is also very easy
```
vobcopy -i /media/cdrom0 -m
```
Where -i stands for input,/media/cdrom0 is where my dvd's are mounted and -m is mirror the content of the dvd to your hdd.
You can then use avidemux for converting to xvid.
It has some great filters and supports custom matrices.
If you want to do it more automated check out dvd::rip....this will rip and encode but i find avidemux produces a better end result.

---

### Post by kinematic on 2007-07-21
> **kc5hwb said:**
> I assume "RIPit4ME" is available in Synaptic.

Why would a Windows app be in the Ubuntu repository?

---

### Post by kc5hwb on 2007-07-21
> **kinematic said:**
> Why would a Windows app be in the Ubuntu repository?

LOL... never heard of this app so no idea who makes it.

---

### Post by reylafo on 2007-07-21
Ripit4me is some sort of interface for DvdDecrypter and DvdShrink  plus it creates a "psl"- protected sector list-which DvdDecrypter uses to break the protection to newer DVDs. The last version, 1710(was forcefully retired and banned) included "FixVTS", a tool to clean the file system of the copy so DvdShrink can analize it and do it's job.
I still use it simply because it works and they work under WINE-Ubuntu.
You can get the .exe here:[http://www.majorgeeks.com/download5408.html](http://www.majorgeeks.com/download5408.html)

Get it while you can. I have a guide to install. Can send it to you by e-mail, and a user guide ,but is only in spanish~español
[http://www.prtc.net/~laforey/](http://www.prtc.net/~laforey/)

---

### Post by kc5hwb on 2007-07-21
Cool, thanks for the info.  I just downloaded it and will try it with WINE

---

