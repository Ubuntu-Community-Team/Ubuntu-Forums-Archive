---
title: "MFC-210C How to make a printer driver?"
date: 2005-04-01
forum: Apple PPC Users
---

### Post by tater on 2005-04-01
Can anyone here tell me how to make my own printer driver for this printer, the Brother MFC-210C?  I have the linux printer driver for it in i386, and also for OSX, and there are drivers for it in every flavor of Windows.

I've never made a printer driver before, so I don't even know how difficult it would be.  Or where to begin.  It would seem to me that somehow it should be possible to look into the OSX driver and find pieces that would be usable, after all, it's UNIX-based, isn't it?  Is there some sort of utility anywhere that would let Ubuntu or Kubuntu use OSX printer drivers?

Or, does anyone know of some powerpc printer-driver guru that could and would help?

Thanks in advance,
tater

---

### Post by tater on 2005-04-02
No one has replied to my plea for help, and I think I now know why.  I've been reading everything I can get my eyeballs on about linux printing.  What I need is a ppd file for the MFC-210C.

However, peeling the onion a bit, I now know that the reason there is no ppd for this printer is because Brother is not releasing its specs to developers.  That's why they are providing their own printer drivers for i386 linux, and OSX, and flavors of Windows, just the binary files.

So, I have an idea, please let me know if this is way off-base.  What if, on my Windows XP machine, I make a minimal text file, and print it through the printer driver, but to a file instead of sending it to the printer?  Won't that file contain the printer's embedded control codes for basic text printing?

And then, couldn't there be a way to harvest those control codes and use them to create a ppd for this printer, or modify an existing ppd?  Like, open the file in a binary/hex editor and see if I can identify the printer's control codes?

I probably need to try this thread over at linuxprinting.org, but I wanted to first run it by everyone here to see if any of you know if this has been tried before, or if you think it could work.

Of course, if anyone here has gotten the MFC-210C to print (from an Ubuntu mac), please tell me how you did it.  I really, really want to stick with Ubuntu and not be forced to go back to OSX just because of my stupid printer.

Thanks,
tater

---

