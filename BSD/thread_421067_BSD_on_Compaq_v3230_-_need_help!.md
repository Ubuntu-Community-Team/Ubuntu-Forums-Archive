---
title: "BSD on Compaq v3230 - need help!"
date: 2007-04-24
forum: BSD
---

### Post by xx75 on 2007-04-24
Hi BSD-ers,

I have recently purchased a compaq presario v3230au notebook and am having trouble getting pc/free/desktop-bsd to install.

Problem = On the cd the BTX loader stops right after making an option in the boot menu, regardles of which option i select. It states "BTX has stopped" and then it just hangs. I have tried pcbsd, desktopbsd and freebsd and they all do the same thing.

Any suggestions?

Any help is appreciated.

Cheers
xx75

Specs - AMD Turion 64 X2 TL-50 1.6GHz
            80 GB sata hdd
            NVIDIA GeForce Go 6150
            2x512 MB DDR2 Ram 667Mhz
            Super Multi 8X DVD+/-RW 
            14.1" WXGA High Definition BrightView Widescreen display (1280 x 800 Res)
            Broadcom 802.11 a/b/g

---

### Post by mips on 2007-04-24
Go into the BIOS and try disabling "Virtual boot device" or "Virtual install disk" which could probably be found under advanced options.

[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=370245](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=370245)
[http://unix.derkeiler.com/Mailing-Lists/FreeBSD/questions/2003-06/2435.html](http://unix.derkeiler.com/Mailing-Lists/FreeBSD/questions/2003-06/2435.html)
[http://www.freebsd.org/cgi/getmsg.cgi?fetch=61247+63991+/usr/local/www/db/text/2003/freebsd-stable/20030525.freebsd-stable](http://www.freebsd.org/cgi/getmsg.cgi?fetch=61247+63991+/usr/local/www/db/text/2003/freebsd-stable/20030525.freebsd-stable)

---

### Post by xx75 on 2007-04-24
> Go into the BIOS and try disabling "Virtual boot device" or "Virtual install disk" which could probably be found under advanced options.

Thanks for the tips, mips :-P. Unfortunately I have no such options in my bios, in fact I have bugger all options. Boot device order, language, time & date, hdd test, media sound button(?). Disappointing really. Even updated the bios in hope that it may give me a few extra options.

xx75

BTW mips, are you a cricket fan? It should be a good game between the AUS and SA tomorrow.

---

### Post by mips on 2007-04-24
> **xx75 said:**
> Thanks for the tips, mips :-P. Unfortunately I have no such options in my bios, in fact I have bugger all options. Boot device order, language, time & date, hdd test, media sound button(?). Disappointing really. Even updated the bios in hope that it may give me a few extra options.

xx75

BTW mips, are you a cricket fan? It should be a good game between the AUS and SA tomorrow.

Then I dunno about the BTX thing, maybe try the BSDForums etc.

I'm not that big into cricket but I will most likey watch tomorrows game, I hope it is a good game. Some of the games to date have been disappointing to say the least, there has been such a big discrepancy in scores/skill. I watched the AUS game on Friday and the AUS just let rip, poor NZ :)

---

### Post by xx75 on 2007-04-24
> Then I dunno about the BTX thing, maybe try the BSDForums etc.

Yeah.... I know I should have tried there first but since I am familiar with the ubuntu forums I thought I'd try my luck. I have read along my tracks that the bsd forums are not so friendly, only one way to find out I guess.

>  I watched the AUS game on Friday and the AUS just let rip, poor NZ 

Unlike NZ to let their guard down on us, they usually make a good game of it. My guess is that SA are not going to be so easy. That effort last year where SA chased down AUS 434 runs still plays in my mind! :)

xx75

---

### Post by mips on 2007-04-24
> **xx75 said:**
>  That effort last year where SA chased down AUS 434 runs still plays in my mind! :)


lol, I was sitting in the pub watching that game. After  I saw the AUS score I though there is no way in hell, I might as well go home and sleep. When I woke up the next morning I heard we won and took your brief world record away from you guys.

---

