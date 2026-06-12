---
title: "Problems with ATI drivers"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by PhoenixEdge on 2006-04-11
The machine that is having problems is an HP dv5020us laptop. It has an integrated ATI Express 200 (it's not that great, but I don't use this laptop for anything other than school and work). It has an AMD Turion 64 processor. 

I get a sinking feeling that Linux won't ever work properly on my laptop, because I can't find anywhere that says my graphics card is supported. My somewhat savvy Linux friend couldn't get the drivers working properly, either.

When I first installed Ubuntu, I couldn't even start X. But after fiddling around in the terminal and trying dozens of tricks that have been posted on this forum, I managed to get the X windows system to load. The problem is that the resolution won't go any higher than 1024x768 (which looks really bad, considering the native resolution of the monitor is 1280x800), and when I go into the device manager, all the ATI related stuff is labelled as "Unknown". 

I'm sorry if this question has been answered already in some form or another, but I have browsed these forums for hours and could not find any solutions to my problem.

For any possible solutions, please remember that I am an absolute beginner (this is my first time using Linux), so you will have to give me baby steps.

Thanks. ;)

---

### Post by Bishop Hill on 2006-04-11
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

This is what you're looking for. Beware though, it can screw up your system like it did to mine.

---

### Post by PhoenixEdge on 2006-04-11
Great, it looks like my card IS supported! :D 

[http://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.16.20.html#172394](http://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.16.20.html#172394)

In that link you gave me, am I supposed to follow method 1 or 2? And should I do the Breezy installation?

When you say it screwed up your system, do you mean that it damaged your hardware somehow? 
Should I completely reinstall Ubuntu and start from scratch when doing this? I don't have any important data or anything on the laptop at this point.

Thanks a lot for the help so far though.

---

### Post by romeozor on 2006-04-11
here's what i used (for my pc, 9600 XT) works like a charm
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28driver%29%7C%28ati%29]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28driver%29%7C%28ati%29")

---

### Post by PhoenixEdge on 2006-04-12
[QUOTE=romeozor]here's what i used (for my pc, 9600 XT) works like a charm
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28driver%29%7C%28ati%29]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28driver%29%7C%28ati%29")[/QUOTE]

But should that work for me?

---

### Post by PhoenixEdge on 2006-04-18
[QUOTE=romeozor]here's what i used (for my pc, 9600 XT) works like a charm
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28driver%29%7C%28ati%29]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28driver%29%7C%28ati%29")[/QUOTE]


Ok I followed the steps there, and now I can't even load X anymore. I have no idea how to do the second part. 

For this link 

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

I don't know what I'm supposed to do, especially considering the note for 64 bit users. I don't know how to download drivers and install them through the command line in Linux. Can someone help? I'm so lost. I've had this laptop for weeks now, and I still haven't been able to use it. I'm about to just give up and put Windows XP back on it.

---

### Post by MagicalElly on 2006-04-18
I'm having this exact same problem and registered solely because I need this question answered badly.  I have a HP 5040 and couldn't get into X until my friend helped me out. But then even he couldn't figure out how to get the ATI drivers to properly get recognized. Could we get some help here please?"

---

### Post by Vespa on 2006-04-19
I'm kind of having the same problem. I looked all over these boards but can't find a solution to the problem that the others are having in this topic. I have a DV5020 just like the topic creator and it has had nothing but problems. It first had these acpi issues or something (got help with that one thanks to a topic on these boards), then it couldn't even boot into the windows system... it keeps telling me that "X failed to start  Any ideas?  Help us!  Help us, please!

---

### Post by romeozor on 2006-04-19
try this as root:
```

dpkg-reconfigure xserver-xorg

```
probably works with sudo too

---

### Post by PhoenixEdge on 2006-04-19
[QUOTE=romeozor]try this as root:
```

dpkg-reconfigure xserver-xorg

```
probably works with sudo too[/QUOTE]

I've run that command at least twenty times now, and it doesn't do anything to fix X.

I tried everything I could from the stuff posted in this topic, but nothing is working to get X working again. Sigh.

---

