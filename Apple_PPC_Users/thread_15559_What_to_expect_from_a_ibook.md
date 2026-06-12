---
title: "What to expect from a ibook"
date: 2005-02-15
forum: Apple PPC Users
---

### Post by larsg on 2005-02-15
hi

I'm thinking about buying a laptop, and I must say that those ibooks are tempting. I have been searching a bit round on the subject and have found that, there is some 'issues' with running linux on a ibook, but I haven't been able to get a clear picture of what to expect. Let's say I buy a brand new ibook g4:

1.2GHz PowerPC G4
512K L2 cache (at 1.2GHz)
12-inch TFT Display
1024x768 resolution
256MB DDR266 SDRAM
30GB Ultra ATA drive
DVD/CD-RW drive
ATI Mobility Radeon 9200
32MB DDR video memory
AirPort Extreme built-in

What should I expect to work with Ubuntu (both Warty and Hoary)? I can live without wireless network, but what about the following:

- Battery life
- Suspend/Sleep function
- TV-out
- External vga-monitor

These are very important to me, and I hope someone might be able to answer before I buy something that doesn't work.

Thanks in advance!

---

### Post by fu. on 2005-02-15
it all depends on what you want to do with it lars,

the ibooks are really good chunks of hardware for generic all-round computing but keep in mind that they represent the consumer line of apple's range...

if you just want a bit of office/net stuff and some gaming, then an ibook is a good bang for your buck...

now considering running linux on your ibook (and generally linux on Apple Hardware) i highly recommend taking a look @ this article:

[So you own a Mac, why run Linux?](http://www-106.ibm.com/developerworks/library/l-pmac.html) 

and do some seraching on the forums about your specific needs...

---

### Post by toojays on 2005-02-15
I have had an iBook G4 for about 8 months now. I use GNU/Linux exclusively on it, and switched from Gentoo to Ubuntu Hoary a couple of weeks ago.

I think the iBook is very good value, but I recommend maxing out the hard drive and getting bluetooth builtin.

As far as Linux support goes for the things you asked about:
Battery life - around 4 hours

Suspend - only works with kernel 2.6.9+benh-sleep-patch, support should be in mainline kernel in the next couple of months

External VGA monitor - Xinerama works fine, MergedFB has [bug 6223](https://bugzilla.ubuntu.com/show_bug.cgi?id=6223) against it.

TV-out - I've not tried this yet.

Note that Airport Extreme and the builtin modem will probably never support Linux.

---

### Post by DJ_Max on 2005-02-15
About the Airport Extreme, read the last post of this thread.
[http://ubuntuforums.org/showthread.php?t=862&highlight=Airport+Extreme](http://ubuntuforums.org/showthread.php?t=862&highlight=Airport+Extreme)

---

### Post by toojays on 2005-02-15
I just read that Broadcom thread. I don't know whether the original claim (that the chip can broadcast in military freqs) is true, but the argument is unsound anyway.

What it reduces to is "we can't give you software because you might do something illegal with it". It's a way of weaselling out of the debate, and people shouldn't settle for it.

---

### Post by DJ_Max on 2005-02-15
I see what you mean, but if there's anything I learned, companies aren't obligated to release the source of their software, and if there's a big enough demand, people can always do what the gatos project & GPLFlash did.

---

### Post by chascon on 2005-02-16
I'm not sure about this but I believe that "g" technology is derivitive of gpl software.  Thus, I have read that it might be posible to legally force "them" (such as broadcom) to release code because their drivers are extensions of the gpl software they are make to work with (G).  I imagine that in essense propietary makers are engineering software in hte same fashion one reverse engineers.

If propietary software owners want us to believe that reverse engeneering is illegal, then they shouldn't be allowed to engineer propietary software built on gpl code.  You can 't have it both ways marketdroids.

---

