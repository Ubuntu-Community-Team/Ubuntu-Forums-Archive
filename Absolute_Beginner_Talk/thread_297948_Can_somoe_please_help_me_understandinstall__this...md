---
title: "Can somoe please help me understand/install  this?... linux-wlan-ng"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by sheeep on 2006-11-12
Okayy. I apologize for making so many topics on this, but the last one sort of got off-topic from the title, and might not attract the attention of those who can solve the problem.

To make a long story short, I'm trying to get my Microsoft MN-510 Wireless USB adapter to work with my laptop running ubuntu.

I installed the drivers off the Microsoft Adapter's cd using ndiswrapper, and the hardware is recognized as "present". When I go to configure the network, it doesn't recognize it as wireless.

iwconfig in the terminal returns:

> 
lo     no wireless extensions.

wlan0  no wireless extensions.

eht0   no wireless extensions.

sit0   no wireless extensions.


I've searched for the last week and have found a lot of threads on the adapter that end in dead ends. The only one I have found that has any good news is here:

[http://www.ubuntuforums.org/archive/index.php/t-106700.html](http://www.ubuntuforums.org/archive/index.php/t-106700.html)

Which states:

> I got the MN-510 to work on my parents' machine using linux-wlan-ng. The prism2_usb module loads automatically when you plug in the device, then you send a couple of commands to load the linux-wlan-ng drivers per the docs, then start the DHCP client.

The connection was a bit flaky at first until I followed someone's suggestion of sending the first linux-wlan-ng setup command twice in a row (I don't remember the whole string, you'll find it in the docs, but it's the one that includes prism2_usb DORESET=1). That seemed to prevent the connection from shutting down after a few hours.

I have not been able to get the connection to start properly on boot, despite trying all the suggestions in this forum and others (all involving /etc/hotplug). Once I figured out what commands worked, I put them in a script that I run manually with sudo after x starts. If Dad reboots the machine by accident (a weekly thing), he calls me and I tell him how to run it :)

When you are experimenting with the different setup commands to find what works, be sure to unplug the device and re-plug it each time or it won't "take"

Most of that is beyond my comprehension. 

I tried installing linx-wlan-ng from a file called linux-wlan-ng_0.2.0+0.2.1pre21-1.1ubuntu_i386.deb

After installing I sorta assumed this was the wrong linux-wlan-ng to install. I downloaded linux-wlan-ng-0.2.5.tar.gz and began to install that.

Untarred the file with tar -zxvf linux-wlan-ng-0.2.5.tar.gz

The readme file states to next enter 'config' which doesn't work. I got suggestions to try ./configure, make, sudo make install, none have worked.

I'm in the home folder directory doing this, should I be in another directory?

I'm honestly clueless at this point, any help in understanding the above quote is greatly appreciated.

---

### Post by jordanmthomas on 2006-11-12
Check your other thread

---

