---
title: "Modem Setup"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by someonedumb on 2006-09-22
Hi, I'm still unable to get my modem to work, here is what I've figured out so far.

I have the same behavior on 3 different dial up software packages, pppd, wvdial, and the GUI one. The modem initializes, dials the number, does the buzzing and beeping, turns off the sound(all exactly normal so far), but then the connection suddenly closes.

With wvdial it prints this:
Carrier detected, waiting for prompt.
Connected, but carrier signal lost! Retrying...

My computer is set to dual boot Ubuntu and Windows XP. The modem works *perfectly* in Windows XP, so I can rule out line noise or other hardware or ISP failures.

I've been leaning toward blaming the driver as the problem. It is a Lucent Winmodem, and I can't seem to find any evidence that it is supported with the kernel version Ubuntu uses (2.6.15-26 correct?)

Any ideas?

---

### Post by someonedumb on 2006-09-22
A simpler question that may render most of my above post irrelevant is this:

Should I expect to be able to get a lucent winmodem to work on ubuntu? Or would it be best to simply buy a real modem?

---

### Post by someonedumb on 2006-09-22
bump...

---

### Post by someonedumb on 2006-09-22
bump again... please help :P
(If there is some other information I need to supply before an answer can be made let me know)

---

### Post by podunk on 2006-09-22
[http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch04.html#id2531895](http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch04.html#id2531895)

also this has bunches of stuff:
[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

Just a comment - I wouldn't use a winmodem in Windows, much less try to use one in Linux. They slow your system way down.

Real modems are cheap! :-)

---

### Post by zxee on 2006-09-22
Winmodems can be made to work-when they're supported. From my experiance once the driver is successfully installed they work fine (given the above mentioned requirements).
Go to [http://www.linmodems.org/](http://www.linmodems.org/) download the scan modem tool and be prepared to do some configuration. Also check out the link in my signature.

---

### Post by someonedumb on 2006-09-22
Thanks for the replies, going through linmodems.org... wow its confusing. Definately the most poorly designed driver website I've ever visited. (Or maybe I'm just too used to the simplicity of windows drivers) But at least ScanModem tells me that my modem is supported, so I'm optimistic :)

---

### Post by someonedumb on 2006-09-22
Holy crap this is terrible!!!!! Ok so linmodems.org ended up not helping, the drivers I finally got from them wouldn't install because it said my kernel version was wrong (they wanted kernel 2.6.12 and I have kernel 2.6.15). So then I went to [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto) and found the section there on winmodems, it told me that the packages for the drivers were installed by default, and I found them, executed the commands to install them:
sudo sh -c "echo ltserial >> /etc/modules"
sudo sh -c "echo ltmodem >> /etc/modules"
and the commands executed and gave no errors, and I thought I finally had a working modem.

So I restarted and tried to dial up and its acting *exactly* the same as it did in my original description.

I dont get it, ScanModem says my modem is supported, and so does the website I refrenced, But the directions from both of those sources dont work... What should I do?

---

### Post by Mark_in_Hollywood on 2006-09-22
If you are using WvDial as the "backend", which means you get to the 'net by opening a terminal and typing "wvdial", you should read there FAQ, which is:

[http://open.nit.ca/wiki/index.php?page=WvDialFAQ](http://open.nit.ca/wiki/index.php?page=WvDialFAQ)

it does describe the problem of the line dying quickly. 

If you are using Gnome-PPP or KPPP, those are graphic versions of wvdial (they are "frontends").

Please don't be put off by the difficulty in getting dial-up to work. I've been going through it since I started with Ubuntu 9 months ago. If you like, you can search my posts by my user name.

I think most 'buntu-ers have broadband. At least those who can post.

---

### Post by someonedumb on 2006-09-22
Thanks for the reply. I use pppd most of the time, wvdial and the GUI dialer were attempts at finding other software when I was assuming the driver worked.

As a sidenote, broadband didn't work on ubuntu either :P I was on broadband when I dl'd the distro and installed it, but have been on dial up since that day.

---

### Post by someonedumb on 2006-09-22
I followed the instructions in the website you linked to, the "/var/log/messages" log file had this:

Sep 22 10:06:24 localhost pppd[4962]: pppd 2.4.4b1 started by root, uid 0
Sep 22 10:06:24 localhost kernel: [17179712.536000] PPP generic driver version 2.4.2
Sep 22 10:06:25 localhost chat[4963]: abort on (BUSY)
Sep 22 10:06:25 localhost chat[4963]: abort on (NO CARRIER)
Sep 22 10:06:25 localhost chat[4963]: abort on (VOICE)
Sep 22 10:06:25 localhost chat[4963]: abort on (NO DIALTONE)
Sep 22 10:06:25 localhost chat[4963]: abort on (NO DIAL TONE)
Sep 22 10:06:25 localhost chat[4963]: abort on (NO ANSWER)
Sep 22 10:06:25 localhost chat[4963]: abort on (DELAYED)
Sep 22 10:06:25 localhost chat[4963]: send (ATZ^M)
Sep 22 10:06:25 localhost chat[4963]: expect (OK)
Sep 22 10:06:25 localhost chat[4963]: ATZ^M^M
Sep 22 10:06:25 localhost chat[4963]: OK
Sep 22 10:06:25 localhost chat[4963]:  -- got it 
Sep 22 10:06:25 localhost chat[4963]: send (ATDT2492701^M)
Sep 22 10:06:26 localhost chat[4963]: expect (CONNECT)
Sep 22 10:06:26 localhost chat[4963]: ^M
Sep 22 10:07:11 localhost chat[4963]: alarm
Sep 22 10:07:11 localhost chat[4963]: Failed
Sep 22 10:07:12 localhost pppd[4962]: Exit.

But I'm afraid it isn't telling me alot.

---

### Post by someonedumb on 2006-09-22
Well this problem is starting to feel like I'm just beating my head against a brick wall... I haven't come up with anything new for hours now. Before I thought I narrowed the problem down to being a driver issue, but now I really have no idea if the problem lies in the driver, the /etc/ppp/options file, other configurations, pppd itself or something else I haven't thought of. All I know is that the ISP is good, the modem is good, and the username/password is good. (using them right now in Windows XP with no problem.)

Right now I would love to be able to at least narrow down the cause of the problem. I can post the ModemData.txt from scanModem if that would help anyone else. It said the modem was supported and pointed me to a link on linmodems.org that turned up useless.

---

### Post by someonedumb on 2006-09-22
I've been trying to figure out why I had no luck with the link that scanModem gave me, and I think I figured out what it expects of me.

[http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/)

Is the link that scanModem directed me to, originally I noticed that if I went up one level (to [http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/)) there was both a /martian/ and a /ubuntu/ directory, so I figured it was a small mistake on scanModem's part and just went to the /ubuntu/ directory and downloaded the .deb packages there.

However those packages did not work because they were for the 2.6.12 kernel and not my 2.6.15 kernel.

The reason I steered clear of the /martian/ directory was because at first glance I thought it contained drivers for other linux versions (the .rpm files convinced me it was for distros using the Red Hat package system)

After doing more reading I found out that the package style in /ubuntu/ is no longer supported and that I have to use the martian type drivers. So I looked in the original /martian/ directory more closely and found out it was all source code.

So now I guess if I want to use the proper modem driver I have to compile it myself from source. However (even though I do program in windows) the idea of compiling my own drivers from source is very scary... Which of the 10 files (of types .gz, .rpm, .spec, or bz2) do I download? I've never programmed drivers and also do not yet know how to combine the 17 .obj files (I assume one .obj file would be compiled from each .c file, and there are 17 c files in the source package I downloaded) together into a single driver.

As daunting as this task is, the most frustrating part is that I still do not know if the symptoms I'm having are symbolic of a driver problem, or a different type of problem.

---

### Post by someonedumb on 2006-09-22
Oh yeah, and in addition to that I do not yet have a compiler in Linux because for some silly reason it does not come with one installed by default.

I asked before why gcc was not included by default and I was told that it was not expected that normal users would use a compiler... which seems contradictory to me if normal users are expected to compile their drivers from source.

---

### Post by maaronB on 2006-09-22
A quick hackish solution might be to start logging in under the 2.6.12 kernel.

---

### Post by someonedumb on 2006-09-23
Considdering how sensitive modem drivers are to the exact version of the kernel... wouldn't switching the kernel version break pretty much every other driver?

---

### Post by maaronB on 2006-09-23
> **someonedumb said:**
> Considdering how sensitive modem drivers are to the exact version of the kernel... wouldn't switching the kernel version break pretty much every other driver?

Yeah, I just gave it a shot and my Video Card went all crazy. So I don't know what to tell you.  The fact is winmodems are a pain in the but to get working, and with the majority of Linux users having high speed conections there is not much reason for the major distro's and developers to fix them.  
I am sure there is a solution, but if you are not prepared to spend the next few months getting it to work, then you should probably think about your other options:

1. Buy a true Modem.
2. Try a couple of different Distros (I have heard Mepis is good at hardware recognition)
3. Give up on your Linux experiment for now and stick with Windows.(I hope you don't but sometimes it is the best option)

---

### Post by someonedumb on 2006-09-23
hehehe, option 3...
I did that a long, long time ago.
Over 5 years ago is my best guess... I spent about a month trying to get Linux working (mandrake). I learned as much as I could. Got the modem working in about a week (good old fasioned real ISA modem:P... this computer doesn't have any ISA slots even if I could find the old modem), spent a few days learning how to use Wine, then crashed the whole system by filling up the HD and had to spend over a week fixing it, and then tried to get my sound card working (SoundBlaster Live!) but eventually found out that no drivers of any form existed for my kernel version and took option 3. Haven't let linux anywhere near my computer since... untill a week ago when I finally decided to try again, but I'm determined to not give up this time.

If I have to buy a new modem then fine, but I'd rather exhaust software options first.

Right now I'm trying to figure out if I can download the "build-essential" package in windows and copy it to my Linux HD to install it.

---

### Post by _duncan_ on 2006-09-23
Hi. I was able to compile a modem driver from source for my smartlink modem by following this wiki. It wasn't written specifically for your modem, but some of the basics like installing build-essentials are covered.

[Howto Conexant and Smartlink modem]("http://www.ubuntuforums.org/showthread.php?t=190728&highlight=smartlink")

I had the same problem months ago. I was trying to get my PCTel dial-up modem to work but couldn't. So I did the next best thing: bought a smartlink modem for about 5 dollars and followed the wiki. After a few hours, I can already connect to the internet from Ubuntu.

---

### Post by zxee on 2006-09-24
Sorry you're having so many problems with getting that modem working in ubuntu. I've been away from my computer for a bit.
Sometimes the problems are in the options file or /etc/resolv.conf doesn't have the correct dns#'s in it.
Try using > pon provider from a terminal and then copy and paste the output the terminal outputs when the connection dies.
Note: replace 'provider' with whatever you have set your connection as. Having said that-have you run > sudo pppconfig from a terminal to set up your connection? i.e. that command will create the files you need to connect.

---

