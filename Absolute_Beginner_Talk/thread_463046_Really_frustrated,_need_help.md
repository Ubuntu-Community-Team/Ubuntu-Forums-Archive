---
title: "Really frustrated, need help"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by sreed39 on 2007-06-03
So, after my XP Crashed a month ago, I had to get a new motherboard and new CPU (went with Pentium 4), after that I re-installed XP, only to find out that, since I had already had to re-install it a previous time, I could not re-install it without buying a new copy.

Friday night (it is now sunday morning), after doing some more looking into linux, I decided to give it a try. I downloaded the desktop i386 7.04. checksum was good, burned it to disk, there was a disk error (though it did apparently burn as the correct file structure was on the CD). So I downloaded a different version, same problem. In all I did 6 different downloads using different mirrors etc and could not get a download that would install.

For the 7th try, I used the alternate iso file. got through all of the installation in text mode seemingly fine. But, when I reboot in Ubuntu, I can never get past the command line. I found a forum last night that suggested the following commands "To get a useable desktop"

sudo apt-get update

sudo apt-get install xorg xterm gdm icewm menu firefox gksu synaptic

sudo dpkg-reconfigure x-server-xorg

sudo/etc/init.d/gdm start

The first three command lines went through and the fourth did not, it said unknown command... so still I am stuck at command line and cannot get into a desktop environment.

I am not a programmer and very new to Linux. I would prefer to stop paying Microsoft money. I really ***_WANT _***to switch to Linux, but if it is this difficult to use, I will probably be forced to go backwards to Windows 98. Any suggestions or help?

---

### Post by tchoklat on 2007-06-03
the last copmmand should read sudo /etc/init.d/gdm start
gap after sudo

---

### Post by oilchangeguy on 2007-06-03
where did you get the idea you have to buy a new copy of xp? all you need to do is follow the activation process, and call micosoft to reactivate it, if prompted.

---

### Post by cantormath on 2007-06-03
```
sudo apt-get update ubuntu-desktop
``` and reboot.
go here, same issue, different person:
[http://ubuntuforums.org/showthread.php?p=2757374#post2757374](http://ubuntuforums.org/showthread.php?p=2757374#post2757374)

I also personally recommend, just my recommendation, using Automatix2 to get your codecs, video, flash and java working in minutes instead of hours.  
There are other tools to do this, but I recommend automatix2, its at [http://getautomatix.com](http://getautomatix.com).  

If you havek, god forbid, an ATI video card, I recommend envy........if you dont like the way the video card is responding.....to install your drivers.

---

### Post by sreed39 on 2007-06-03
I did re-install and call microsoft, THEY told me that I would have to buy it again retail!

There was a space after sudo, btw

---

### Post by oilchangeguy on 2007-06-03
> **sreed39 said:**
> I did re-install and call microsoft, THEY told me that I would have to buy it again retail!

There was a space after sudo, btw

i find that hard to believe. unless you're not already using a legal copy.

---

### Post by bone43 on 2007-06-03
> **sreed39 said:**
> I did re-install and call microsoft, THEY told me that I would have to buy it again retail!

There was a space after sudo, btw

There are ways around the MS problem but why bother you are on the right track
freedom is a good thing!

---

### Post by sreed39 on 2007-06-03
ok...so after several restarts and several addendum installs I got the desktop up and running... thank you! Next problem, Ubuntu detects that I am connected to the internet, but I cannot actually access the internet. To get here, I had to restart and boot Windows again... any advice?

---

### Post by oilchangeguy on 2007-06-03
> **sreed39 said:**
> ok...so after several restarts and several addendum installs I got the desktop up and running... thank you! Next problem, Ubuntu detects that I am connected to the internet, but I cannot actually access the internet. To get here, I had to restart and boot Windows again... any advice?

ok, you mind clueing us in on how your computer connects to the internet?

---

### Post by sreed39 on 2007-06-03
reboot in Windows so that I can ask questions...

I have a  cable modem provided by local ISP... SMC EZ Card 10/100 PCI (SMC1211TX)

---

### Post by oilchangeguy on 2007-06-03
> **sreed39 said:**
> reboot in Windows so that I can ask questions...

I have a  cable modem provided by local ISP... SMC EZ Card 10/100 PCI (SMC1211TX)

ok, so how did you determine that ubuntu see's your internet connection, but won't connect?

---

### Post by sreed39 on 2007-06-03
when i log into Ubuntu, it shows "Detected Wired connection" When I launch Firefox, if cannot locate any websites. I cannot ping any websites from Ubuntu. I checked the config of the ethernet card and Ubuntu says it is okay another thread said to try

sudo /etc/init.d/networking restart

that did not work... another thread said to completely disconnect the power supply (not just shut down, but unlplug) and restart to ubuntu (the theory being according to that thread that Ubuntu wasn't seeing the driver because windows had it occupied) this did nothing either...

i went to network settings but it failed to load and I had to use "Force Quit" several times...

---

### Post by oilchangeguy on 2007-06-03
try this (don't know if it'll work) unplug/turn off the cable modem to let it reset. turn it back on, and see if that works. you may have to do this every time you switch from ubuntu to windows. as they probably use different ip addresses. if you go thru a router this will not be a problem.

---

### Post by sreed39 on 2007-06-03
tried everything I know of. Completely turned off computer, unplugged power source, disconnected DSL cable from computer, unplugged DSL Modem. Left them off for 15+ minutes. Logged into Ubuntu first. After getting to desktop plugged modem to power, put connection to Computer. Detected the connection, no access to internet still.

I was able to check all the settings and it appears to be configured properly. I just do NOT know what to do...

It is rather frustrating...

---

### Post by lemoniceblock on 2007-06-03
This might or might not help at all, but I remember when I installed Edgy onto my desktop, I had to go to /etc/network/interfaces and switch the order around so that the wired connection (mine was eth0) came after 'auto lo' but before 'auto wlan0' etc.  I'm not sure if putting eth1 after 'auto lo' matters or not.  Alternatively, if you don't think you'll be using wireless, etc you could put a '#' in front of every line in those entries that you won't need.  Then restart all your connections.

---

