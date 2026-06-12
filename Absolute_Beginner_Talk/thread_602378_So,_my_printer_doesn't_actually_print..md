---
title: "So, my printer doesn't actually print."
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Metalslave on 2007-11-04
Yeah, a HP LaserJet 1018. I hooked it up via USB, Gutsy identified it right away, it's set to be the default printer, everything is fine, except it doesn't actually print anything.

The printer itself is fine. It works like it should on a Windows box. On my Linux box, sod all happens and no jobs are getting queued.

I am disappointed. I need this box to at least print. It is a basic thing in the world of computers and I totally expected Ubuntu to have this sorted by now.

---

### Post by Malta paul on 2007-11-04
Hi, I have the same printer as you and had the same problem. 
It does work good in Ubuntu as I found out. Check out [http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018)
If you still have a problem post again and I run you through the setup'
Good luck :)

---

### Post by Metalslave on 2007-11-04
I still have a problem.

---

### Post by SunnyRabbiera on 2007-11-04
usually HP printers work on linux as they share their drivers with us...
hopefully you can get this fixed

---

### Post by Malta paul on 2007-11-04
The most important thing is you must install some Firmware first, not just the driver: 

The firmware of the printer must be uploaded after turning it on. You can use a hotplug/udev script which comes with foo2zjs, or do it manually: "cat /usr/share/foo2zjs/firmware/sihp1018.dl >  /dev/usb/lp0".

For the driver which is required and Ubuntu will find. Is at:
[http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)

Keep trying, I can assure you the printer works well with Ubuntu. :)

---

### Post by SunnyRabbiera on 2007-11-04
uh huh as HP is very generous at least in that it offers both drivers and firmware to us...
getting it to work is another issue but at least its there

---

### Post by Metalslave on 2007-11-04
> **Malta paul said:**
> The most important thing is you must install some Firmware first, not just the driver: 

The firmware of the printer must be uploaded after turning it on. You can use a hotplug/udev script which comes with foo2zjs, or do it manually: "cat /usr/share/foo2zjs/firmware/sihp1018.dl >  /dev/usb/lp0".

For the driver which is required and Ubuntu will find. Is at:
[http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)

Keep trying, I can assure you the printer works well with Ubuntu. :)

I looked at the page you linked to and I have no idea what it means or what I'm supposed to do. I ran those code snippets in the terminal and it just threw up a bunch of errors.

---

### Post by SunnyRabbiera on 2007-11-04
you can try to find a deb for the driver/ firmware on google, I heard a few people doing that

---

### Post by Metalslave on 2007-11-05
> **SunnyRabbiera said:**
> you can try to find a deb for the driver/ firmware on google, I heard a few people doing that

What's a deb?

---

### Post by jaybombalous on 2007-11-05
its an install package, means it has everything thing u need in one package that will install automatically and configure itself.

U could have just used google. '*.deb' [http://en.wikipedia.org/wiki/Deb_(file_format)](http://en.wikipedia.org/wiki/Deb_(file_format))

---

### Post by Malta paul on 2007-11-05
Hi, I see you still have a problem, let me see if I can run through the setting procedure for you.

Connect and S/W on your printer.

Go to Terminal and copy in the following,- One line at a time then after each entry press enter.

wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)

tar zxf foo2zjs.tar.gz

cd foo2zjs 

sudo make uninstall

make

./getweb 1018

sudo make install

sudo make install-hotplug

sudo make cups

Switch Off your printer, then on again. Reboot you computer.

Go to System>Administration>Printing
Check printer settings show your printer idle, If not go to 'Policies' and tick enabled,

That is it, Good luck :)

---

### Post by Rollinpizza on 2007-11-05
Hi, I have the same problems but the scenario is a little different because my printer is connected to PC that has windows installed. That means, my printer is shared and I need samba to use it. Ubuntu detects it perfectly but when I want to print, the printer doesn't print. I've installed foo2zjs from openprinting but it hasn't solved my problem. Anybody has the same problem than me and has found a solution?

Thanks in advance. ^^

---

### Post by Malta paul on 2007-11-06
Hi,Rollinpizza.
If you are duel booting Windows/Ubuntu your printer will run in Windows using an MS or a HP Windows driver then when you are in Ubuntu, Ubuntu will use the Foo2zjs driver. 
The HP Laserjet 1018 printer when used with Linux requires you to install some _Firmwar_e with your operating system. Ubuntu will detect your printer and install the correct driver but won't install the Firmware itself. Take a look at the links in my previous posts, and this link my also help (I hope!)
[http://foo2zjs.rkkda.com/INSTALL](http://foo2zjs.rkkda.com/INSTALL)
Have fun:)

---

### Post by Metalslave on 2007-11-06
I am giving up on this and going back to XP. I will keep Ubuntu around on a partition like a digital curiosity, the bearded lady of my local freakshow, if you will.

---

### Post by stchman on 2007-11-06
> **Metalslave said:**
> Yeah, a HP LaserJet 1018. I hooked it up via USB, Gutsy identified it right away, it's set to be the default printer, everything is fine, except it doesn't actually print anything.

The printer itself is fine. It works like it should on a Windows box. On my Linux box, sod all happens and no jobs are getting queued.

I am disappointed. I need this box to at least print. It is a basic thing in the world of computers and I totally expected Ubuntu to have this sorted by now.

You unfortunately have a printer that is in the LaserJet 1000 family.  I have a LaserJet 1000 and it is a you know what to get it to print.  These printer use the Zenographics ZJStream wire protocol.  I eventually bought a Postscript HP printer that works perfectly under Linux.

Refer to the following webpage:
[http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)

In the future refer to [www.linuxprinting.org](www.linuxprinting.org) for compatible printer.

---

### Post by Rollinpizza on 2007-11-06
> Hi,Rollinpizza.
If you are duel booting Windows/Ubuntu your printer will run in Windows using an MS or a HP Windows driver then when you are in Ubuntu, Ubuntu will use the Foo2zjs driver.
The HP Laserjet 1018 printer when used with Linux requires you to install some Firmware with your operating system. Ubuntu will detect your printer and install the correct driver but won't install the Firmware itself. Take a look at the links in my previous posts, and this link my also help (I hope!)
[http://foo2zjs.rkkda.com/INSTALL](http://foo2zjs.rkkda.com/INSTALL)
Have fun

Well, I've uninstalled foo2zjs driver and then I've installed it again following the steps of your previous post and the link: [http://foo2zjs.rkkda.com/INSTALL](http://foo2zjs.rkkda.com/INSTALL) . After, I've added the printer with CUPS manager. Everything is ok (printer status: Idle) but when I click Print Test Page button, the printer status is processing and afterwards, quickly, changes to held status. Definitely, it doesn't print yet :( .
Googling, I've found out it needs to send the firmware to the printer in mac os x and another systems. But how do I do if my printer is shared in a network? Is it necessary in ubuntu gutsy?

---

### Post by LowSky on 2007-11-06
my 1018 works fine in gutsy? I did have issues in Fiesty but non since upgrading

---

### Post by offroad64 on 2007-11-06
I had a situation very close to this with my HP printer. I have a dual boot computer Gutsy 32bit and Gutsy 64bit. I was able to print out of the 32bit distro but got the same symtoms out of 64bit that you discribe. It was driving me up the wall. The fix turned out to be a faulty cable. I don't know how or why but when the cable was replaced I could print with no problems.:confused:

---

### Post by Rollinpizza on 2007-11-06
If only was a faulty cable... but it isn't my case because with windows XP it works. :(
In Feisty, the shared printer worked like a charm with foo2zjs. I don't understand why it doesn't work in gutsy... I'm very frustrated and upset.... :cry:

---

### Post by offroad64 on 2007-11-06
That's what I thought. My printer worked fine in windoze XP and Vista as I said it also worked fine in Fiesty 32bit and Gutsy 32 just not in Gutsy 64. For me it was a cable issue not firmware or drivers.](*,)

---

### Post by Rollinpizza on 2007-11-08
I've realized that in CUPS manager, in the printers section, where it puts the printer name (in my case: LaserJet_1018 ), just next, there is the following: "/usr/lib/cups/backend/smb failed"
I think this is my true problem because all the rest works fine. But I don't know how to solve it...

EDIT:

Well, I've found out it's samba bug that affects ubuntu. We will have to wait until they correct it. The bug importance is high, so I don't believe that they are long much to release an update. (I hope so)

---

