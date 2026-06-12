---
title: "Ubuntu install cd error"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by munkie2 on 2006-03-16
alright, first of all greetings! my first post(and i hope this is in the right section)

alright, I have both the i386 5.10 install disk and the amd64 disk

my cpu is a AMD Athlon XP 2600+

when I put the amd64 disk in it boots up fine(brings me to the kernel picking screen) and I pressed enter...then i get the message "Your system does not support 64 bits.  Please go to 32 bit" or something along those lines.

Then i tried the i386 cd.  It would not boot up at all(i didnt get to the kernel pick screen like the amd64 disk). Now i thought it might have just been a bad burn but i tried to burn it twice more and it still didnt work.  

Now i am stuck! Should i try to re download the i386(maybe the file was corrupted somehow)?

Thanks in advance for your help

---

### Post by Klaidas on 2006-03-16
At what speed did you burn them?
It's reccomended to use a very low speed.

---

### Post by m.musashi on 2006-03-16
I've installed ubuntu enough times to be able to help with this but I'm not sure I understand what is happening. First an Athlon processor should support 64 bit so I'm not sure where that error is coming from. But lets address the boot up piece first.

You mentioned that 64 brings you to the "kernel picking screen". I'm assuming that this means you got it fully installed and that the GRUB boot loader offers you a choice of kernels and your other OS (probably windows). If you are not dual booting you usally don't see the grub menu unless you press esc (I think) within a few seconds. It probably looks like ```
Ubuntu, kernel 2.6.10-386 (or 686 for 64 bit depending on the kernel that was loaded)
Ubuntu, Kernel 2.6.10-386 (recovery mode)
Ubuntu, memtest86+
Other operating systems:
Microsoft Windows XP Professional
```
At least that is similar to mine. Is this what you are referring to? It's odd for it to install and then say it won't work. Can you give a bit more info here?

On the 32 bit side, when you say it won't boot I'm assuming you mean it won't install (based on your description). I would say that the first thing to check is whether or not the CD is good. It's possible to have a bad burn or bad download. Give us a bit more info and we can try and pin down the problem.

---

### Post by m.musashi on 2006-03-16
Also, it might be good to decide which you want to install (32 or 64 bit) as working on both problems will be difficult. I'll probably get in trouble for saying this but most people seem to suggest the 32 bit as it's a bit more "complete")

---

### Post by munkie2 on 2006-03-16
i burnt each cd at 12X

and i meant by 'kernel picking screen' as the FIRST screen and prompt you see when you pop in the disk and wish to install(no grub or anything)...it gives a few options you can enter or you can just hit enter to use the default kernel(it always says to press F2 to see more kernel options)....i cant find a picture online but maybe my description can clear that up

---

### Post by m.musashi on 2006-03-16
Okay, that makes more sense. If you get the error on the 64 bit then it might be possible that you don't have a 64 bit CPU. I'm not sure why though as I though all athlon processors were 64 bit. I could be wrong.

The error on the 32 bit is probaly because of a bad burn or download. Did you check the md5 sum. If you are on windows you may need to search for and download a program to do this. I found one when I first started to play with Ubuntu but I don't remember where.

The other thing is to burn slow. There seems to be a lot of problems with burning fast 12x isn't THAT fast but I always burn at 4x. I assume you are also burning an ISO image rather than a data cd. Default windows programs don't do ISO as I recall. You will need to use Nero or similar. If you got the 64 bit version to boot though you probably are okay here. Try a slower burn or check the md5 sum.

---

### Post by munkie2 on 2006-03-16
alright, well im currently burning at 4x and ill try that out and then ill check the md5 sum if that doesnt work

thanks for the help!

---

### Post by m.musashi on 2006-03-16
[Here](http://www.openoffice.org/dev_docs/using_md5sums.html) is some info on checking the md5sum. It's in reference to open office but shouldn't matter.

---

### Post by munkie2 on 2006-03-16
alright! the md5 sum for the i386 was totally different than what it should be! time to re download >.<   thanks a lot!

---

### Post by patrick87 on 2006-03-16
[QUOTE=m.musashi]Okay, that makes more sense. If you get the error on the 64 bit then it might be possible that you don't have a 64 bit CPU. I'm not sure why though as I though all athlon processors were 64 bit. I could be wrong.
[/QUOTE]
AMD's Athlon XP series was not 64 bit edition. I have a Athlon XP 2000+ (currently not in use) . 

AMD's Athlon XP series were dropped and became basically the Sempron Series to my understanding.

because now if u buy a 2000+ or more processor, they arent XP's they are semprons . AMD's are usually 64 bit now.. most of the popular ones are, but older versions and chipsets are not. And when i say old, im only talking 3-5 years really. 

Its not hard to confuse that all AMD's are that way.

so yea... i jus had to explain that quote...that was u  understand y now..hope i helped sum.

---

### Post by munkie2 on 2006-03-16
[QUOTE=patrick87]AMD's Athlon XP series was not 64 bit edition. I have a Athlon XP 2000+ (currently not in use) . 

AMD's Athlon XP series were dropped and became basically the Sempron Series to my understanding.

because now if u buy a 2000+ or more processor, they arent XP's they are semprons . AMD's are usually 64 bit now.. most of the popular ones are, but older versions and chipsets are not. And when i say old, im only talking 3-5 years really. 

Its not hard to confuse that all AMD's are that way.

so yea... i jus had to explain that quote...that was u  understand y now..hope i helped sum.[/QUOTE]


ah, thank you! i looked at amds site and i couldnt find the XP's at all so i just figured they were 64 bit

---

### Post by m.musashi on 2006-03-16
Thanks for correcting my lack of knowledge. That error makes a lot more sense now.

---

