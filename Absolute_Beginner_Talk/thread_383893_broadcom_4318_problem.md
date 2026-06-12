---
title: "broadcom 4318 problem"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by mmmhobnobs on 2007-03-13
hey I've only just got into linux, sorted my dual booting and partitions and basically getting to grips with things.  The only major drawback I have so far is that my network card appeared to be recognised, whereas I could not access the internet (I tried setting up my network settings to know avail)...and to cut a long story short I've been looking around the internet trying to sort this out.

Okay I've got a hp laptop/notebook/whatever name you want to give it with a broadcom bcm4318 wireless card and a amd turion 64 - I'm running 64 bit edgy (I think? 6.10).

After reading up I read that I would have to use ndiswrapper and a windows driver for my wireless card to be recognised and useful, and found this tutorial which I followed:
[http://www.ubuntuforums.org/showthread.php?t=285809&highlight=ndiswrapper+initialize+failed]("http://www.ubuntuforums.org/showthread.php?t=285809&highlight=ndiswrapper+initialize+failed")

I found what I believed to be the x64 driver for windows for my card and installed it all accordingly, and blacklisted the other card as mentioned in the above link.  Thing is, now my wireless card doesn't appear at all - something must have gone wrong.

I was wondering if anyone could help?  upon doing the whole dmesg thing I discovered the error of "Windows driver couldn't initialize the device" with regard to my wireless card.

I've tried searching forums and the internet, but it's all **very** confusing for a noob, hence me joining this forum=)

---

### Post by mikesignguy on 2007-03-14
yes  very confusing and difficult.....i couldn't make mine work using ndiswrapper  ...so  i bought a netgear pmcia  card ... plugged it in and it worked (not really but it took about 20 min to get it working)


so  my advice ..  try..   if you   don't succeed goto to the computer store

---

### Post by mmmhobnobs on 2007-03-15
ugh well I'm on a laptop for a start, and I a bit poor atm so it's not really an option.

I'm getting help on the subject in another thread however, which seems to be going well:)

---

### Post by kelbizzle on 2007-03-15
theres a post from a guy named compwiz18 on here. It's the same howto I follow every time and now he even has a script that does the leg work for you. But it's works every time and it's as simple as running a script. Then installing the nm-applet from the repositories.

---

### Post by DarkN00b on 2007-03-15
> **mmmhobnobs said:**
> hey I've only just got into linux, sorted my dual booting and partitions and basically getting to grips with things.  The only major drawback I have so far is that my network card appeared to be recognised, whereas I could not access the internet (I tried setting up my network settings to know avail)...and to cut a long story short I've been looking around the internet trying to sort this out.

Okay I've got a hp laptop/notebook/whatever name you want to give it with a broadcom bcm4318 wireless card and a amd turion 64 - I'm running 64 bit edgy (I think? 6.10).

After reading up I read that I would have to use ndiswrapper and a windows driver for my wireless card to be recognised and useful, and found this tutorial which I followed:
[http://www.ubuntuforums.org/showthread.php?t=285809&highlight=ndiswrapper+initialize+failed]("http://www.ubuntuforums.org/showthread.php?t=285809&highlight=ndiswrapper+initialize+failed")

I found what I believed to be the x64 driver for windows for my card and installed it all accordingly, and blacklisted the other card as mentioned in the above link.  Thing is, now my wireless card doesn't appear at all - something must have gone wrong.

I was wondering if anyone could help?  upon doing the whole dmesg thing I discovered the error of "Windows driver couldn't initialize the device" with regard to my wireless card.

I've tried searching forums and the internet, but it's all **very** confusing for a noob, hence me joining this forum=)

This happens because Ubuntu includes the card drivers so it can recognize the hardware, but it does not include the firmware to actually make the card work.  Have a look [here]("http://ubuntuforums.org/showthread.php?p=1071920&mode=linear") to fix your problem. I don't know if this will work on the 64 bit varsion of Ubuntu, but I don't see why it wouldn't.

---

### Post by kelbizzle on 2007-03-15
don't forget to get a connection manager that way you won't have to connect via command line. Compwiz18 has instrustions on all those also.

---

