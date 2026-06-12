---
title: "Enable Slower Processor Speed on ti-Book?"
date: 2010-01-20
forum: Apple Hardware Users
---

### Post by noibs on 2010-01-20
I'm using 9.10 on an 867mhz ti-book.  Ubuntu is quicker than OSX and everything I care about works.  However, the G4 processor can't auto-cycle up and down as later G4's could.  It can operate at a reduced speed, though.  Doing so greatly reduces the heat output and fan noise.

Anyone know how to enable the slower processor speed in 9.10?

---

### Post by linuxopjemac on 2010-01-21
I have a panel added in the top of my Gnome desktop (cpufreq). "Add to panel" -> "CPU frequency scaling monitor". You can then set the frequency of your CPU. I hope it also works for PPC. I have no idea. It works for Intel Macs. In the past I had a PowerBook Titanium as well with Gentoo and I was able to scale the frequency. I don't remember how I did that. You can read the processor speed with

```
cat /proc/cpuinfo
```

you might also want to look at this post:

[http://mac.linux.be/content/cpu-frequency-scaling-opensuse-111-fix](http://mac.linux.be/content/cpu-frequency-scaling-opensuse-111-fix) I have to add that cpudyn is in the repository, so if you like to try the idea in the post you could just do a

```
sudo apt-get install cpydyn
```

If the panel trick doesn't work, and cpudyn is not the answer either, I will try to digg up that info I had in the past about freq scaling on PPC.

---

### Post by noibs on 2010-01-21
Thanks so much.  You were right in the beginning.  All I needed to do was add the CPU speed panel.  My two choices are 867mhz and 667mhz.  I'm now trying to find out if a slower speed than 667mhz is supported by the processor (on other forums).  If so, I'll edit the relevant file to enable the slower speed.

Also, link to the article was helpful in that I used that article and others I found to learn something that I didn't know.  Many thanks.

---

### Post by noibs on 2010-01-21
One more relevant update...

I found that by installing cpudyn, I could select an option in the CPU speed panel that enabled on-demand cycling between 867 and 667 mhz.  I can still select only 667 and only 867.  

To me that's noteworthy because Apple NEVER enabled on-demand cycling of the CPU frequency in this ti-Book in either OS9 or any version of OSX.

One other general comment from a still-Mac and sometimes Ubuntu user:  Karmic looks so nice.  Font smoothing is excellent and everything is clean, functional and attractive.  And, I'm shocked that there is as much PPC software available in the repositories.  I've been looking hard at the Dell Vostro V13 with Ubuntu (or the 2-core version and wiping the mandatory Windoze) and I think my current experience is pushing me even harder toward that purchase.

---

### Post by linuxopjemac on 2010-01-22
Excellent!!

---

