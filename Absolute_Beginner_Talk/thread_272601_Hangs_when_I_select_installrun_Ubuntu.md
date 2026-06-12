---
title: "Hangs when I select install/run Ubuntu"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by makko on 2006-10-06
Hi,

I have just burnt a cd to install (Version 6.1 i316 Desktop). I select run/install Ubuntu from the main menu I get the loading kernel progress metre. Thats fine skips onto the next screen. The next screen hangs when the progress bar is only a small bit gone along..what to do? I got the ISO from this site and burnt it with sonic record now..I am really looking forward to running Ubuntu and this is driving me around the bend..

Thanks,
Makko

---

### Post by ewl1217 on 2006-10-06
Reboot the computer with the Ubuntu disc in. Once you get to the menu, choose the option to check the CD for errors. Let us know the results of that.

---

### Post by blendmaster on 2006-10-06
The pc also might not have sufficient RAM. You may need to download the alternate cd. My two older ones (one only five years old, though that's pretty old) couldn't run the livecd.

---

### Post by makko on 2006-10-06
Ok,
This is the ISO I downloaded:
ubuntu-6.10-beta-desktop-i386.iso
I have tested the cd for errors and it has zero errors.
I have tried it on A P2 700Mhz and An Amd 700Mhz both have only 128Mb RAM..It must be the RAM?
I might try it on my laptop now which has 512Mb.

How much RAM is required and what is the difference between my ISO and the alternate one?
EDIT: I want to install the OS not just run it from CD..

Thanks,
Makko

---

### Post by lemonsCC on 2006-10-06
the alternate has text based install among a couple other features

---

### Post by gn2 on 2006-10-06
For the cd you've got you'll need a minimum of 256mb RAM.

6.10 isn't a stable release, it's still beta, and may cause more problems than 6.06 which is the stable release.

Need 256mb for all  but the server/alternate install methods.

Although it is possible to install 5.10 on 192mb RAM and update to 6.06 by downloading updates.

---

### Post by makko on 2006-10-06
That would all make sense to me..I just tried it on my latop (512MB RAM) and it worked perfect.. I also noticed (afterwards) that 6.1 was beta and 6.06 was stable damn it anyway.. I will get that later. with the alternate disc is it all the same after install.. I plan on getting more RAM anyway. I will probably get another 512MB or 1024MB...

---

### Post by gn2 on 2006-10-06
The alternate install is a whole different beast entirely...

Only installs what you tell it to, so I guess you need to know what you want?

Never used it myself, have been using standard 6.06 Ubuntu on a P3 500 192mb Portege 3440CT without any problems whatsoever.

---

### Post by makko on 2006-10-06
I think I will just get more RAM and install 6.06 fully, I plan on using it as a webserver. Does anyone know where I will find a guide on starting up a webserver with Ubuntu?

P.S. You guys are so helpful..

Thanks,
Makko

---

### Post by ewl1217 on 2006-10-06
If all you want to do is use it as a web server, then you should check out the server version of Ubuntu [(see here)]("http://www.ubuntu.com/server"). While it doesn't include a GUI (Graphical User Interface), it makes it very easy to get a web server up and running. Of course, if you aren't familiar with the command line, or don't have the time and/or desire to learn, then it may not be the best way to go. If you want, you can just do a normal install of the desktop version, and then install the required server components from there.

---

### Post by gn2 on 2006-10-06
This should get you going: [https://help.ubuntu.com/community/WebServerHosting?highlight=%28web%29%7C%28server%29](https://help.ubuntu.com/community/WebServerHosting?highlight=%28web%29%7C%28server%29)

---

### Post by makko on 2006-10-06
I have read some articles and the console version (server) seems very daunting so I will use the desktop version and install the server components. Where do I get all these extra downloads and other utilities??

---

### Post by gn2 on 2006-10-06
System>Administration>Synaptic Package manager.

You'll want to enable the Multiverse and Universe repositories first.

More info System>Help>System Documentation>Ubuntu Desktop Guide>2.6 Extra repositories.

Cool eh?

---

