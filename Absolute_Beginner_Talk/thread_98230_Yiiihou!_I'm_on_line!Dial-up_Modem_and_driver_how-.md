---
title: "Yiiihou! I'm on line!Dial-up Modem and driver how-done-it"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by lila on 2005-12-02
Hello,
A big thanks to all of you who helped me get here, this is my first visit to the internet with my lovely new computer with Ubuntu Breezy Badger!  Took me a good couple of weeks to find a modem that would work, find and install a driver for it, and had to re-install Ubuntu once as well.  
For all of you experiencing similar oddysseys and don't know what they are doing (like me), here's how I got there (with lots of advice from people of these forums):

1) figure out what kind of Modem you have, hardware or software, or mixed.  
Open terminal (in Applications->accessories) and type wvdial /dev/null (or something like that, compare with thread "Modem doesn't work" by myself (lila)).  This will tell you if you have a hardware modem.  Hardware one is best, a software one seems to be highly complicated, so when I found I had one of those, I tried to find another one.  
2) if you have a hardware modem, skip the following: download scanModem (page address available in the same thread I think, else do search).  Use it (it helpfully comes with instructions).
3) it told me that my software modem was unlikely to get support (too modern).  So I searched and was about to buy a Serial port RS-232 (or was it -323?) modem, when my boyfriend found me a recycled ancient PCI 56k modem from a derelict computer at work, which, when I ran wvdial and scanModem again, turned out to be mixed hard/soft.  ScanModem told me that one was usable, so then I proceeded like this:
4)read all the useful information that comes up with, and I just ended up going to [www.linuxant.com/drivers](www.linuxant.com/drivers) and entering all the info
5) download the relevant package.  It comes in a free version which is slow (using that at the moment - hence I don't want to open multiple windows to find and give exact threads), and if that works, you can upgrade to a "full" fast version which involves "a small contribution" (to keeping the site working) which I think is fair enough, although I don't yet know how much "small" is...
6) install with their instructions - realising what took me a while: where they put ...modem...{version}_{arch}  you need to put your modem code (which you get from the title of your unzipped zip file) to replace the two {} bits.
7) go to System->Networking click on Modem and put your dial up info in.  
8) attach phone cable.  That one almost threw me....;) 
Hopefully, that should do it.  

Hope this is useful for other newbies.  I'll keep an eye on this thread for a bit, maybe others have additions/corrections/questions.

VERY happy,
Lila

---

### Post by Bartender on 2005-12-02
Hi, lila -
Thanks for taking the time to report back with some steps.  It's encouraging to this newbie to see others succeed in some of the areas that look a little shaky.

---

### Post by knobcottage on 2005-12-02
Nice one!  I have a smartlink 56k modem ( silicon laboritories ..I think) and the driver but no idea what to do to make them work.  Ubuntu is still the live version but I use SuSe too.  Tons of instructions in the help file that came with it but can't make head nor tail of them.  Any simple instructions for the illiterate?  
Got SuSe.  Got Modem.  Got driver.  Got no idea and I SO wnat to get online with some form of Linux via my modem!

---

### Post by L Campbell on 2005-12-02
Well done, Lila.

You have done what I thought I would be doing several weeks ago.

You've mastered what I'm beging to call ' Linux's dirty little secret', the fact that trying to get online with Dial-up is not always easy.

I thought I would be able to get all the issues resolved and then write a ' How To ', just like you have.

It won't be long, now and I'll be surfin' too.    :-)

---

### Post by lila on 2005-12-03
[QUOTE=knobcottage]Nice one!  I have a smartlink 56k modem ( silicon laboritories ..I think) and the driver but no idea what to do to make them work.  Ubuntu is still the live version but I use SuSe too.  Tons of instructions in the help file that came with it but can't make head nor tail of them.  Any simple instructions for the illiterate?  
Got SuSe.  Got Modem.  Got driver.  Got no idea and I SO wnat to get online with some form of Linux via my modem![/QUOTE]

If you mean the help files provided by scanModem, there are lots of them in a folder called Modem/ which, once you find it, I just read the lot and picked any bits i understood.  The ModemData.txt file is scary and tells you of lots of potential problems, but if you really don't get anywhere you could send that (whole) to the scanModem people (tells you how in 1stRead.txt), and apparently they'll try and sort it out for you (which I find pretty cool!).
I found what I needed in one of the other files: once you have unzipped the driver (which I did, after lots of tries with various versions of "gunzip" and "unzip" with all sorts of brackets in terminal, with or without sudo, all unsuccessful, by simply double clicking on it, which unzipped it....)
You go back to terminal and use their command you find in I think 1stRead, but possibly one of the other files, somthing like.... no, I can't remember, and I'm at work, not on my ubuntu computer, so I can't look it up either.  But it says "use this if apt-get or somthing like that hasn't done it for you already", and is fairly at the beginning, second paragraph I think, of one of those files (that's a visual rather than text memory for you...).  If you haven't got anywhere by tonight (my time tonight, GMT, didn't look where you are, it's half past ten in the morning at the moment for me), let me know and I'll post the exact command line.
Good luck, 
Lila

---

### Post by knobcottage on 2005-12-03
Cheers for the reply, but I'm still stuck.  There are comprehensive instructions with in a help file but I still can't make them work.

---

### Post by knobcottage on 2005-12-03
Cheers for the reply, but I'm still stuck.  There are comprehensive instructions with in a help file but I still can't make them work.

---

### Post by lila on 2005-12-04
[QUOTE=knobcottage]Cheers for the reply, but I'm still stuck.  There are comprehensive instructions with in a help file but I still can't make them work.[/QUOTE]

Hello, sorry for the late (1day! oops!) reply.  Here's the exact terminal line that did it for me (I'm assuming here that you downloaded a hcf modem driver from Linuxant):   
dpkg -i hcfpcimodem_{version}_{arch}.deb  
and instead of the {}s you put your version (or key I think it was called), so for me that looked like this:
dpkg -i hcfpcimodem_1.08full_k2.6.12_9_386_ubuntu_i386.deb
and I had to sudo it (sudo and then all the rest, it'll ask for password.  When you type the password, it doesn't actually show on screen, not even as ******, but when you hit enter, it's ok anyway.)

Anyway, hope this helps!
Lila

---

