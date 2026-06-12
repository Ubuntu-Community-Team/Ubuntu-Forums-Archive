---
title: "Specific install requirements Mac G5 Dual core 2.5 Ghz Powerpc"
date: 2010-04-28
forum: Apple Hardware Users
---

### Post by 1984dc on 2010-04-28
Hello all.

I am going to install a Version of Ubuntu (the more modern the better(any advice?)) on to my Mac G5 Dual Core 2.5  Ghz PowerPC and i was wondering if anybody had done the same and had any installation advice specific to the G5 PowerPC architecture that i am going to build on. I am planning to Install ubuntu to an external hard drive and use that as a separate boot option using the open firmware codes provided  on this page
[http://www.macosxhints.com/article.php?story=20060301112336384](http://www.macosxhints.com/article.php?story=20060301112336384)
When i need to use ubuntu i will simply boot from Open firmware and add the code, I would also like to know if this is actually possible as i am unsure if the open firmware can only boot Os X and maybe it wont work with Linux.

I heard on a previous forum that some people needed to modify the linux kernel so that the fans/cooling system worked properly and did not work at full blast using karmic koala. i was wondering if anybody could shed any light on that as i would like to know if that is in fact true.

I would prefer to install Ubuntu rather than another linux distro as it seems to have the most community support and i am fairly new to linux (i have only been using it for a year on my netbook).

Many Many thanks in advance
Dc

Power Mac G5 dual-core at 2.5 GHz (OS X 10.4.11) 
Internal Hard drive: Serial ATA Maxtor 6B250S0

---

### Post by linuxopjemac on 2010-04-28
You might want to read about the windfarm kernel module. I think it's the one responsible for the G5 fans. They should be in Karmic Koala.

---

### Post by 1984dc on 2010-04-29
Thanks for that Thats a perfect response i wil look into modifying the kernel or find out which versions have not got it and maybe try them.

Once again many thanks

DC

---

### Post by zeroti on 2010-04-29
I have a powerbook G4 and I had a problem with fans going 100% all the time until I installed all of the karmic updates and rebooted. That seemed to solve the issue. I think it's even a little better in lucid.. :P

---

### Post by 1984dc on 2010-04-30
Thanks for that that is good to know i will undoubtedly install lucid lynx onto my g5. did yaboot just run out of the box for you?

---

### Post by 1984dc on 2010-10-25
Btw If anybody is reading this thread now, in the end i tried lots of different distros of ubuntu and none of them worked 
"out of the box". Some of them would boot but there was no gui just command line. I have since read that to set up x11 windows manager on a power pc mac is a serious task.

In the end i ended up installing Ydl (Yellow dog linux) 6.2 as it worked out the box =D>. The only thing that i am still trying to configure is the wifi connection but I can use ethernet for the time being.

---

