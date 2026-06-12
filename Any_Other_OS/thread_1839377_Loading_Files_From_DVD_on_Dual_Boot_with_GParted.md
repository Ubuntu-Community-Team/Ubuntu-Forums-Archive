---
title: "Loading Files From DVD on Dual Boot with GParted"
date: 2011-09-05
forum: Any Other OS
---

### Post by supplysider on 2011-09-05
Newbie here. Trying to load files from DVD for HD to load XP on Dual boot system with GParted. HD just won't pick it up so I can load XP.  Picked up everything else though, including Ubuntu 11.04 for the Dual Boot. I'm left with either trying to copy files through the CLI from the DVD or Drag and Drop. Does anyone know the commands? And if anyone has a better idea, I'm all ears. Thanks.

---

### Post by mips on 2011-09-05
I have no idea what you are trying to say/do.

---

### Post by mips on 2011-09-05
Instead of PMing people rather post here so others can see what you mean.

My advice would however be to backup your data & mail followed by a format & reinstall. First however boot of the windows install cd and try and do a repair which might work.

---

### Post by supplysider on 2011-09-05
Clean format was the first thing I tried.  The SATA HD needs these files to properly function with XP.  Runs like a champ with Ubuntu.

---

### Post by supplysider on 2011-09-05
Clean format was the first thing I tried. The SATA HD needs these files to properly function with XP. Runs like a champ with Ubuntu.

---

### Post by mips on 2011-09-05
In that case you need the SATA drivers on a disk or usb stick the XP installer can access them from.

Second option is to slipstream the SATA drivers into your XP install media using something like nLite.

Third option is to use XP SP3 install media or sliptstream SP3 into your install media using nLite. I think SP3 has most of the SATA drivers but I could be wrong. Maybe just slipstream both SP3 & SATA drivers.

---

### Post by supplysider on 2011-09-05
That was my original response.  I had the drivers on a CD that were just no booting up.  It's the original Gateway CD that I have just come across.  I am not familiar with this nLite process.  I'm intirigued.  I'll Google it and see if I can find out more.  I do not want to trouble you for more information.  You have been very helpful Mips.  I would like to learn more about this process.  This could be the missing link.

---

### Post by mips on 2011-09-06
[http://www.nliteos.com/](http://www.nliteos.com/)
[http://en.wikipedia.org/wiki/NLite_and_vLite](http://en.wikipedia.org/wiki/NLite_and_vLite)

My suggestion would be to boot ubuntu and run the following command from a terminal **lspci -v**. Copy and paste the output to a file which you can save on a USB stick and then post the output here.

From the lspci -v command we can determine the exact SATA chipset used by your Gateway. We can then go to the actual chipset manufacturers web site and download the latest driver for it.

I would also suggest slipstreaming SP3 into the install media. Followed by removing all the unused stuff like additional languages you will never use, printer drivers, obscure network protocols like netware ipx/spx, banyan vines etc.

EDIT: You will need a working windows computer to use nLite. Should also work on windows running on virtualbox if you have no access to a windows install.

---

