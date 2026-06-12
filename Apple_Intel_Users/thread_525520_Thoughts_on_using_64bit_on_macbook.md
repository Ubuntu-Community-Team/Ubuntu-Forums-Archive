---
title: "Thoughts on using 64bit on macbook"
date: 2007-08-14
forum: Apple Intel Users
---

### Post by Zelut on 2007-08-14
I have long suggested that users stick with 32bit for compatibility reasons but recently I realized that if nobody ever uses 64bit it will never improve and not ever take off.  I'm considering re-installing with 64bit to help test and improve the 64bit platform but I wonder what other experiences users have with that.

Will wireless via ndiswrapper or madwifi work in 64bit?
Other known hardware issues?
Other known major packages not available for 64bit?

Let me know.. if there are major show stoppers I wont switch on my production machine, but maybe a testbed machine only for now.

---

### Post by cyberdork33 on 2007-08-14
> **Zelut said:**
> I have long suggested that users stick with 32bit for compatibility reasons but recently I realized that if nobody ever uses 64bit it will never improve and not ever take off.  I'm considering re-installing with 64bit to help test and improve the 64bit platform but I wonder what other experiences users have with that.

Will wireless via ndiswrapper or madwifi work in 64bit?
ndiswrapper will work if there are 64-bit windows drivers for your hardware.
> Other known hardware issues?
I would wait for someone with compatible hardware to answer this one.
> Other known major packages not available for 64bit?

Let me know.. if there are major show stoppers I wont switch on my production machine, but maybe a testbed machine only for now.
you can run 32-bit apps on 64-bit OS. Not as nicely, but it will work, you just have to have 32-bit copies of libraries available.

---

### Post by david_edmundson on 2007-08-14
I'm yet to get Madwifi to work with 64-bit. I was minutes away from writing a forum post about that. For me it's a stopping point to me using it as a primary OS.

As for applications - the killer stopping points are anything non-free, such as Skype, and some of the windows codecs mplayer uses. Having said that, flash works flawlessly.

---

### Post by trouble1313 on 2007-08-14
I have no issues with Madwifi. The only thing other than power consumption being not as good as osX (which has nothing to do with the kernel being 64 bits) is the lack of a 64 bit java web start capable JRE other than Blackdown which just doesn't work for the app I need to run.
-Trouble

---

### Post by misfitpierce on 2007-08-14
64 bit is taking off in a sense. I run a 64 bit partition and im going to say that 95% of all app's that have a 32 bit have a 64 bit install as well. On getdeb.net you can clic the name of program and it will show 32 and 64 bit install files. 64 bit is quite nice I might add.

---

### Post by Zelut on 2007-08-14
trouble1313 - thanks for that info.  Do you have the second gen? C2D?  I had to use ndiswrapper on my machine until the recent madwifi fix in gutsy (or cvs).  Just wondering if we're using the same hardware and if I'll have similar results.

---

### Post by Zelut on 2007-08-14
misfitpierce - do you notice a real performance difference?  Many I have talked to say its so minimal its not even worth it.  What do you think?  If my hardware were to work and th applications I use are 64bit built, would you suggest using it?

---

### Post by cyberdork33 on 2007-08-14
> **Zelut said:**
> misfitpierce - do you notice a real performance difference?  Many I have talked to say its so minimal its not even worth it.  What do you think?  If my hardware were to work and th applications I use are 64bit built, would you suggest using it?
It is minimal unless you are doing processor intensive tasks.

---

### Post by pveith on 2007-08-15
Yeah the actual gain in speed in processor-intensive tasks (mp3 encoding, video encoding) is paid for with higher memory useage. On servers 64-bit system do support a much bigger memory space natively, which is -IMHO- why 64Bit really took of there easily, but this is irrelevant for macbooks with a max of 4GB...

---

### Post by alephsmith on 2007-08-15
I was using 64bit on my Santa Rosa MBP and everything worked.

The only thing that too substantially more work than 32bit is having to fiddle around with nspluginwrapper. Installing the 32bit compatibility libraries and the associated hassles didn't seem to be worth it considering I saw no considerable benefits on the simple task I was performing.

---

### Post by cyberdork33 on 2007-08-15
> **pveith said:**
> Yeah the actual gain in speed in processor-intensive tasks (mp3 encoding, video encoding) is paid for with higher memory useage. On servers 64-bit system do support a much bigger memory space natively, which is -IMHO- why 64Bit really took of there easily, but this is irrelevant for macbooks with a max of 4GB...

Exactly... If you were building a server, I would recommend 64bit, but for a desktop system, stick with 32bit.

BTW, here is a great thread on the debate: [http://ubuntuforums.org/showthread.php?p=3191720#post3191720](http://ubuntuforums.org/showthread.php?p=3191720#post3191720)

---

