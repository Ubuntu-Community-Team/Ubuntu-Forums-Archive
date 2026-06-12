---
title: "Use Wine to Drive Printer?"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-11-12
I'm using my newly installed Ubuntu system with pleasure, but my printer, a Dell AIO 922, is without a driver in Linux.  Can I use the Wine, or other OS emulator, to drive the printer?

Thank you,
Buck

---

### Post by verby on 2006-11-12
good question... i'd like to know if it's possible. i have other printer and no linux driver for it.
any ideas?

> **Buck2348 said:**
> I'm using my newly installed Ubuntu system with pleasure, but my printer, a Dell AIO 922, is without a driver in Linux.  Can I use the Wine, or other OS emulator, to drive the printer?

Thank you,
Buck

---

### Post by Handssolow on 2006-11-13
Me too. I've a BJ300 that I'm calling a BJ200 to get working in Edgy.

---

### Post by Sef on 2006-11-13
Your printer is based on Lexmark's x5270, so try the Lexmark Z55 driver.  It might work with your printer, but no guarantees.  It worked mostly with an [X5150]("http://linuxprinting.org/show_printer.cgi?recnum=Lexmark-x5150").

---

### Post by bollix47 on 2006-11-13
I used [this HowTo]("http://www.ubuntuforums.org/showthread.php?t=49714") to get my A920 printing and it does work, but only printing ... no scanner.

I'm pretty sure that I read somewhere in this forum that if a piece of hardware doesn't work in linux then it won't work in wine as wine is just a 'layer' running on top of linux.

---

### Post by Buck2348 on 2006-11-14
I tried the well-written How-to but no luck.  I've read somewhere that there is no driver for the Dell AIO 922/Lexmark 5270.  I would greatly appreciate hearing from anyone who has an idea how to make it work.

Thanks,
Buck

---

### Post by univremonster on 2007-03-04
Anyone who has significant programming talent would help the whole world out by going to
 [http://www.lexmark.com/lexmark/sequentialem/home/0,6959,204816596_659668505_0_en,00.html](http://www.lexmark.com/lexmark/sequentialem/home/0,6959,204816596_659668505_0_en,00.html) 

and writing a driver.  I have been all over the internet and think I can safely say that there are no drivers for Lexmark X5270.  One helpful hint I came across which may alleviate problems with other Lexmarks (and other brands really) is that if you use the drop-down for "Manufacturer" on Step 2 of installing a new printer, there is a section called Generic.  These Generic drivers are compatible with a wide variety of printers (though not the X5270 apparently).  More info at

[http://en.wikipedia.org/wiki/Printer_Command_Language](http://en.wikipedia.org/wiki/Printer_Command_Language)

---

### Post by univremonster on 2007-03-04
Oh, and as if to rub salt in your wounds, if you're trying to use a 64-bit processor (as I am) you can't even use the LDK Developer Kit.

---

### Post by dirken on 2007-05-25
I'm also having a dell aio 922 and i am a programmer. I don't feel like getting this thing working on my own cause yes i am a programmer but never programmed any driver in Linux. So if anyone feels like yeah, i wanna help sort things out and get that printer working, please let me know! Just reply to this message and we can start!

> **univremonster said:**
> Anyone who has significant programming talent would help the whole world out by going to
 [http://www.lexmark.com/lexmark/sequentialem/home/0,6959,204816596_659668505_0_en,00.html](http://www.lexmark.com/lexmark/sequentialem/home/0,6959,204816596_659668505_0_en,00.html) 

and writing a driver.  I have been all over the internet and think I can safely say that there are no drivers for Lexmark X5270.  One helpful hint I came across which may alleviate problems with other Lexmarks (and other brands really) is that if you use the drop-down for "Manufacturer" on Step 2 of installing a new printer, there is a section called Generic.  These Generic drivers are compatible with a wide variety of printers (though not the X5270 apparently).  More info at

[http://en.wikipedia.org/wiki/Printer_Command_Language](http://en.wikipedia.org/wiki/Printer_Command_Language)

---

### Post by Terl on 2007-05-25
I also have the 922 and have been playing with the drivers available in Lexmark.  I got it to at least start feeding paper then it stalled.  I found a spot that hinted that a z600 (it is more for the dell 910 but it was worth a shot) driver may help.  That is the one I got that at least fed paper.  The lexmark 5270 shows as a paperweight so I have little hope for the Dell.

So, my solution was to leave windows on the pc and print from ther.  :(  I don't use it a lot so it is easy enough.  I am going to give up and shop for a 100% linux compatible.  

Perhaps with Dell selling pc's with ubuntu they will help push for printer drivers.  :popcorn:

---

### Post by dirken on 2007-05-25
Can't find that dell z600 printer driver in Ubuntu, plz tell me how you got this one installed 'cause this may be a step closer to let it printing!

> **Terl said:**
> I also have the 922 and have been playing with the drivers available in Lexmark.  I got it to at least start feeding paper then it stalled.  I found a spot that hinted that a z600 (it is more for the dell 910 but it was worth a shot) driver may help.  That is the one I got that at least fed paper.  The lexmark 5270 shows as a paperweight so I have little hope for the Dell.

So, my solution was to leave windows on the pc and print from ther.  :(  I don't use it a lot so it is easy enough.  I am going to give up and shop for a 100% linux compatible.  

Perhaps with Dell selling pc's with ubuntu they will help push for printer drivers.  :popcorn:

---

### Post by Terl on 2007-05-25
This is where I started.  This guy has made the deb packages already.  I am not certain it will work.  I did get the printer to start but then it quit.  It may need more configuring.

[z600 and dell printer]("http://dgtlmoon.com/dell_720_printer_lexmark_z600_printer_on_debian_sarge")

He shows a Dell 720 but I thought I'd try.  I was following guides for a dell 910 but what the hey, go down swinging.  I am hoping I can at least get the printer portion working and do not care about the scanner part so I was trying all kinds of things :)  If all else fails I will just go to wal-mart and buy an HP Printer.

---

### Post by dirken on 2007-05-25
I'll let you know if it could get it working. I can now tell you already more. I tried some other lexmark drivers to searching for your z600 driver en i tried the lx5000 driver for the z82 printer of lexmark and he loads my paper but doesn't stall!!!!
That doesn't mean he's printing effectively. Here's what happens:
I give my printing job (a test page given through [http://localhost:631/printers](http://localhost:631/printers)
He loads the paper
Then it seems like he is stalling
but wait a minute and he is going on whit the job it seems but very very slow, you can here him move the paper forward one or twice every minute. Maybe you can try this out ones yourself and let me know whether you get this better working or not?

Greetz..
Dirken

> **Terl said:**
> This is where I started.  This guy has made the deb packages already.  I am not certain it will work.  I did get the printer to start but then it quit.  It may need more configuring.

[z600 and dell printer]("http://dgtlmoon.com/dell_720_printer_lexmark_z600_printer_on_debian_sarge")

He shows a Dell 720 but I thought I'd try.  I was following guides for a dell 910 but what the hey, go down swinging.  I am hoping I can at least get the printer portion working and do not care about the scanner part so I was trying all kinds of things :)  If all else fails I will just go to wal-mart and buy an HP Printer.

---

### Post by mlentink on 2007-05-25
> **Buck2348 said:**
> Can I use the Wine, or other OS emulator, to drive the printer?

Hmmm. Not without diffculty, I would say, if at all.
See also: [http://www.witch.westfalen.de/Wine-HOWTO/wineprintconfig.html]("http://www.witch.westfalen.de/Wine-HOWTO/wineprintconfig.html") or [Codeweavers]("http://www.codeweavers.com/support/docs/wine-user/config-printing").
Googling with  "printing with Wine" as search text gives quite a lfew results.

Success!

---

### Post by dirken on 2007-05-25
Hmm, can't get him even loading my paper with the z600 driver :s
too bad. But letting him loading the paper means that he actually get the printing job but then something goes wrong. So is there any way we can get to see an error message?
That would help me a lot further!

> **Terl said:**
> This is where I started.  This guy has made the deb packages already.  I am not certain it will work.  I did get the printer to start but then it quit.  It may need more configuring.

[z600 and dell printer]("http://dgtlmoon.com/dell_720_printer_lexmark_z600_printer_on_debian_sarge")

He shows a Dell 720 but I thought I'd try.  I was following guides for a dell 910 but what the hey, go down swinging.  I am hoping I can at least get the printer portion working and do not care about the scanner part so I was trying all kinds of things :)  If all else fails I will just go to wal-mart and buy an HP Printer.

---

### Post by Terl on 2007-05-25
> **dirken said:**
> Hmm, can't get him even loading my paper with the z600 driver :s
too bad. But letting him loading the paper means that he actually get the printing job but then something goes wrong. So is there any way we can get to see an error message?
That would help me a lot further!

I am at work now, but I am going to be trying more this evening and through the weekend.  I just know one of those drivers will work :)  I am also going to read up more about cups.  I was wondering about error messages also.  It would help us if we could find them.

I might even experiment with some of the foomatic stuff.  I figure the worst that can happen is a reinstall :D

---

### Post by dirken on 2007-05-25
That's right, not funny if you have to but also not the worst thing that can happen ;)
So for those error message you should have a look at [http://localhost:631](http://localhost:631) i guess, there you can find logs maybe in there. Couldn't test that with me 'cause my printer even won't load the paper anymore. Guess i'm closer to a reinstall then you :D But i'll get this fixed so I can try little harder.
I guess we keep posting here alle our thoughts on this topic and eventually also our progress :)

Greetz..
Dirken

> **Terl said:**
> I am at work now, but I am going to be trying more this evening and through the weekend.  I just know one of those drivers will work :)  I am also going to read up more about cups.  I was wondering about error messages also.  It would help us if we could find them.

I might even experiment with some of the foomatic stuff.  I figure the worst that can happen is a reinstall :D

---

### Post by MyR on 2007-07-14
at least the printer works using a virtual machine.

---

### Post by Mogurijin on 2007-08-17
> **MyR said:**
> at least the printer works using a virtual machine.

I was thinking about that route seeing as the only reason I really boot into Windows anymore is to print XD. But it would be nice to get a working driver. It seems quite a few people have a Dell AIO 922. Also, I do know that the comparable Lexmark drivers (I think it was x5270 but I can't remember) would work in Windows just fine (I had lost my driver intstall disk for a while ](*,)). To bad the x5270 doesn't work well in Linux either :(

---

### Post by MyR on 2007-08-19
i've discovered that wordpad has the worse print preview ever. i got a bsod the other day on my vm. that pretty much made my day.

---

### Post by armandh on 2007-08-19
no driver for a data products DDS-32. 
an old but very nice 32 page a minute printer. 
I have been limping along with win-2K beta drivers in xp.
but data products was sold to hatachi
support=0

---

### Post by wolfen69 on 2007-08-19
i have the same printer, and installed xp in virtualbox to get it to work. not the most ideal way to print, but at least i can still use it for a while before i get an HP.

---

### Post by asmoore82 on 2007-08-19
> **Buck2348 said:**
> I'm using my newly installed Ubuntu system with pleasure, but my printer, a Dell AIO 922, is without a driver in Linux.  Can I use the **Wine, or other OS emulator**, to drive the printer?

This is a very nonsensical turn of phrase.
the letters originally stood for
WINE = Wine Is Not an Emulator.

Wine is NOT an Emulator!! promise. :D

---

