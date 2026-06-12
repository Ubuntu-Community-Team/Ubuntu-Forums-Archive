---
title: "Network Connection"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Arcturus on 2007-06-17
A friend told me his internet was detected and started working automatically, mine on the other hand didn't (of course...). Now, what do I have to do to get Ubuntu running with my network connection? My ISP is Bell Sympatico and I'm using 4200 Series modem. I'm running through USB.

I guess I have to download special drivers for Linux, or can I just create a network connection in Ubuntu and it will work?

-

Chat with my ISP support:

**[Support]** Okay. Can you brief me your issue?    
**[Me]** I'm dual-booting Windows XP with Ubuntu 7.04 and I want to be able to access the internet with Ubuntu. Can I do this?    
**[Support]** I am really sorry. We do not support the issue related to Ubuntu and this is out of our scope of support.    
**[Me**] I don't need your support setting it up, I only want to know if I am able to access the internet using Ubuntu.    
**[Support]** As I know we cannot access internet using Ubuntu

This is because they don't offer Linux based drivers, right? Either way, I should be able to still get connected?

---

### Post by Arcturus on 2007-06-17
Sorry to double post, but I am really in need of help with this.

---

### Post by Gimpy_Rob on 2007-06-17
Any chance you can run without the USB cord? If you are talking about the modem I think you are, there is an ethernet port on the modem as well.  I typically find USB annoying for network.

---

### Post by Arcturus on 2007-06-17
> **Gimpy_Rob said:**
> Any chance you can run without the USB cord? If you are talking about the modem I think you are, there is an ethernet port on the modem as well.  I typically find USB annoying for network.
I have an ethernet port, but I guess it isn't working. I will try to find the latest drivers for it and maybe I can get all this running, because I'm totally bummed right now... Went through all the trouble, just to have the "oh, you need Windows in order to access the internet dumbass!" line.

Thanks a lot for the response, I really wasn't expecting one. :)

---

### Post by meborc on 2007-06-17
copied this from another forum:> I run Kubuntu 6.6.1 and I was able to do it by following this directions:

Configuring PPPoE with the command line

To set up the modem, we will use a terminal. To open a terminal, use the menu bar : Applications > Accessories > Terminal.

You need the PPPoE package to be installed in order for the following command to work. This package is installed by default, but can be missing if the configuration has been changed. If the following command does not work, you will need to install this package (see the PPPoE package installation section).

In the terminal type:

sudo pppoeconf

A text-based menu program will guide you through the next steps, which are:

1.

Confirm that your Ethernet card is detected.
2.

Enter your username(provided by your ISP'Internet Service Provider').
3.

Enter your password(provided by your ISP).
4.

If you already have a PPPoE Connection configured, you will be asked if it may be modified.
5.

Popular options: you are asked if you want the 'noauth' and 'defaultroute' options and to remove 'nodetach' - choose "Yes".
6.

Use peer DNS - choose "Yes".
7.

Limited MSS problem - choose "Yes".
8.

When you are asked if you want to connect at start up, you will probably want to say yes.
9.

Finally you are asked if you want to establish the connection immediately.

Once you have finished these steps, your connection should be working.
Manual connection control

To start your ADSL connection on demand, in a terminal type:

pon dsl-provider

To stop your ADSL connection, in a terminal type:

poff dsl-provider

Problems

If your connection does not seem to work, try turning your previously configured ADSL connection on manually (see previous section). To see log, in terminal type:

plog

PPPoE package installation

To check if the PPPoE package is installed, in a terminal type:

dpkg -s pppoeconf

If it is installed you should see the output on the package where two lines show this:

Package: pppoeconf
Status: install ok installed

If the package is not installed, insert your Ubuntu CD and in a terminal type:

sudo apt-get install pppoeconf

If the package cannot be found, you may have to add your Ubuntu CD to the list of software repositories. To add your CD, make sure it is inserted in your CD drive and in a terminal type:

sudo apt-cdrom add

If all else fails, you can download the pppoeconf package from [WWW] [http://packages.ubuntu.com/](http://packages.ubuntu.com/). Of course you will need a working Internet connection, and then to transfer the package via a CDR or USB stick for example. Double click on the package in GNOME to install it.
Boot issues

If you find that you have to run pppoeconf each time you boot, you can try two things:

*

Edit /etc/network/interfaces as described [WWW] here, so that that 'pppoe maintained' lines are before 'auto dsl-provider':

# added by pppoeconf
auto eth0
iface eth0 inet manual
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

*

Failing that, edit /etc/rc.local, and before the last line ("exit 0"), add:

ifconfig eth0 up
pon dsl-provider

Error logs

If you are having problems with your connection, you may find valuable information in the system message logs. You may acces system logs either in a terminal, or with a graphical interface.

*

To use the grapical log viewer, in the menu bar, go to : System > Administration > System Log. You will find the system messages in /var/log/messages.
*

To use the terminal, type:

sudo dmesg

original thread - [http://www.linuxforums.org/forum/ubuntu-help/84942-newbee-needs-help.html](http://www.linuxforums.org/forum/ubuntu-help/84942-newbee-needs-help.html)

---

### Post by Gimpy_Rob on 2007-06-17
Well, the thing that's nice about the network port is that it takes load off of CPU, and is so close to the base system (on motherboard chipset often) that it will almost never fail, even when your USB host might die.  So, I do suggest finding the CAT5 (networking) cable that came with router, and running it instead of the USB wire.  Windows will have NO trouble with this at all, and linux will be happy.  If you need help, ask here or even get ISP to help you run without USB.

If you must go USB, I'll see what I can find for ways of making that work.  Please describe modem more... Is it the motorolla surfboard 4200?

---

### Post by Arcturus on 2007-06-17
> **Gimpy_Rob said:**
> Well, the thing that's nice about the network port is that it takes load off of CPU, and is so close to the base system (on motherboard chipset often) that it will almost never fail, even when your USB host might die.  So, I do suggest finding the CAT5 (networking) cable that came with router, and running it instead of the USB wire.  Windows will have NO trouble with this at all, and linux will be happy.  If you need help, ask here or even get ISP to help you run without USB.

If you must go USB, I'll see what I can find for ways of making that work.
I remember with my first attempt trying to install Ubuntu, it didn't work out, so I rebooted into Windows and the attempt had deleted my USB drivers, so I called my ISP and they tried to set me up using the ethernet, but since it wasn't in my device manager, she said I didn't have an ethernet port, which I do... I guess it just isn't working or something. I will try to find those drivers online right now, I haven't updated them in a bit actually.

In the mean time, if that fails, would you be so kind to check out what you can do with the USB? Nothing can ever go right for me, so I'm assuming the ethernet port won't work or something, etc.

---

### Post by meborc on 2007-06-17
have you tried "sudo pppoeconf" as suggested in the thread i copied? they got it working (dell sympatico) 

read the full thread from the link i posted 2 posts back

good luck :)

---

### Post by Arcturus on 2007-06-17
> **meborc said:**
> have you tried "sudo pppoeconf" as suggested in the thread i copied? they got it working (dell sympatico) 

read the full thread from the link i posted 2 posts back

good luck :)
Sorry, you posted nearly a the same time. ;)

Will check it out now. The thing is though, yeah, my ethernet port isn't working.

---

### Post by Arcturus on 2007-06-17
> **Gimpy_Rob said:**
> If you must go USB, I'll see what I can find for ways of making that work.  Please describe modem more... Is it the motorolla surfboard 4200?
I'm fairly certain it's a Speedstream 4200.

Sorry for the late reply, I hadn't noticed you edited your post until now.

---

### Post by FloSynergy on 2007-06-17
Hey there,

similar issues,

in my case, i just installed ubuntu 6.06 for AMD64x2...
but unfortunately, the ethernet/LAN connection is simply not recognized - anyone have an idea on this one?

thanks, 

flo

---

