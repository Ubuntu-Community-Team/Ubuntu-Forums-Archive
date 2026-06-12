---
title: "DSL modem(speedtouch)"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by Yazan on 2008-04-16
Hello everyone,
Before I start talking about my problem, I would like to advice anyone by not getting a DSL USB modem from speedtouch(thomson/alcatel) 330. Unless, you know what to do to make it work with Ubuntu.

Alright, before a couple of days, I decided to get back to trying connecting my internet. Firstly, I ran Ubuntu from the liveCD and tried to connect to my internet, though it wouldn't work.  After that, I tried two guides: [**This one**](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html) and the one created by ubuntu.com.  None worked.  So, anyways, I left it and was really annoyed why it wouldn't work. While I was chatting with some of my friends, they started talking about linux/ubuntu, and that made me have more hope on getting my internet to work and made me want to try again. 
People told me that nothing will stay saved if I didn't have Ubuntu installed.  So, that's how it went. I made a new partition for Ubuntu and installed it there, after it was successfully installed, and at last, I was happy :)
I then thought that I also might have luck in connecting my internet while running on Ubuntu. I called my ISP company and they told me that I should download the linux drivers.  So, I went to speedtouch's site and downloaded the driver for which will install the DSL drivers. After I downloaded speedtouch_1.3.1-2_i386 and rebooted in Ubuntu, I tried to install the package but for some reason, I got this error:
Error: Dependency is not satisfiable : hotplug
So, I asked on the IRC channel and no one had an idea. I decided to forget about it and to follow the guides. And that's what I did earlier today, I went over the two guides I mentioned above twice if not more and they still wouldn't work. I was shocked, I mean what did I do wrong?? I checked the files, checked the instruction but for some reason I did them all and no errors were given!
So, after all my hard work and patience(2weeks), I am now begging you to tell me some way to work a way around this. I NEED INTERNET CONNECTION ON UBUNTU. That request just won't be done.
Please make it possible, thanks.

---

### Post by spiderbatdad on 2008-04-16
The source package for hotplug is available here:[http://sourceforge.net/project/showfiles.php?group_id=17679&package_id=13684&release_id=227366](http://sourceforge.net/project/showfiles.php?group_id=17679&package_id=13684&release_id=227366)

Get the tar.gz. Right click on it and select extract here...Read the readme and install files.

---

### Post by SR_ELPIRATA on 2008-04-16
I have 2 speedtouch DSL modems and none gave me trouble with Ubuntu... but both of these have LAN ports which are recognized without troubles, all works fine here. I have the small 330 (I think is the 330, USB and LAN connections, which supposedly the manual says that doesnt do DHCP but IT DOES) and the 536 (wireless and also has 4 port switch).

Never tried using them with the USB... if I can use the LAN why use the USB?

One thing to note though, my Live CD did use the automatic internet configuration, but the installed didnt, so I had to change to manual configuration and after that no problems at all.

ELP

---

### Post by crjackson on 2008-04-16
Here, I found this solution in another [theread...]("http://ubuntuforums.org/showthread.php?t=575847&page=2")

> **giornata said:**
> Well, things aren't what they seemed! In my first post I said:

"However, 'ubudsl' ( [http://ubudsl.ubuntu.pl/index_en.html](http://ubudsl.ubuntu.pl/index_en.html) ) does work, although I should point out that this was not immediately after a clean install, but after I had tried the hand-cranking methods."

I've just done an install of the final ubuntu 7.10 (the previous was the release candidate). I then ran ubudsl and --- no internet connection. 

So:
[LIST=1]
[*]I uninstalled ubudsl;
[*]ran through the hand-cranking for PPP over ATM as described in  "https://help.ubuntu.com/community/UsbAdslModem/Speedtouch";
[*]installed and ran ubudsl.
[/LIST]
This did the trick, and I have a working internet connection.

---

### Post by Yazan on 2008-04-17
> **spiderbatdad said:**
> The source package for hotplug is available here:[http://sourceforge.net/project/showfiles.php?group_id=17679&package_id=13684&release_id=227366](http://sourceforge.net/project/showfiles.php?group_id=17679&package_id=13684&release_id=227366)

Get the tar.gz. Right click on it and select extract here...Read the readme and install files.
I need someone to explain to me each step, since I am a total beginner to Ubuntu and I have no idea what the instructions are talking about.
> 
 (1)  Make the root directory of that tree (with this file)
      be the working directory for your root shell.

 (2)  Install:

	# make install

 (3)  To collect ascii event logs for events that aren't handled
      by some /etc/hotplug/*.agent (optional):

	# touch /var/log/hotplug/events

      Or touch /var/log/hotplug/input.events to filter out just
      the unhandled "input" events.  (Similarly for other kinds
      of hotplug events.)

 (4)  Make sure modules are loaded, and device setup scripts are
      run, for devices that were present while the system was
      booting but which weren't handled by the initrd.  On RedHat:

	# chkconfig --add hotplug


The instruction above, didn't make any sense to me, I have no idea what they are asking me to do. Can please someone explain? Thanks.


> **crjackson said:**
> Here, I found this solution in another [theread...]("http://ubuntuforums.org/showthread.php?t=575847&page=2")

Sorry, but I use PPPoE and not PPP over ATM.

---

### Post by Yazan on 2008-04-17
I seriously need help with this please. I bumped it because it's going on the next pages and no one answered my questions yet. I've been trying for a month now. Thanks.

---

### Post by gandaran on 2008-04-17
why not save yourself from all these troubles, buy a modem/router (you can get one for the same price as the usb one) plug in the ethernet cable and use the pppoeconf tool in ubuntu to set-up the connection.

---

### Post by plucky on 2008-04-17
There are many threads on these forums for the Speedtouch 330 modem.

See this [thread](http://ubuntuforums.org/showthread.php?t=585647&highlight=speedtouch+330) for information and a **deb** package to install and use the Speedtouch 330 modem.Follow the link for instructions and to download the deb package.

Makes it really easy.

Good Luck

---

### Post by vinceUUUU on 2008-04-17
Hello

i believe that this website

[http://eciadsl.flashtux.org/modems.php?modem=48](http://eciadsl.flashtux.org/modems.php?modem=48)

has written a specific driver for your modem....your modem is listed in a large list as compatable.

follow the instructions to install and configure this driver and your modem should work in Linux.

Vince.

---

