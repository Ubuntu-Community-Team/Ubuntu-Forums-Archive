---
title: "Getting airport card to work"
date: 2010-01-19
forum: Apple Hardware Users
---

### Post by rlinsurf on 2010-01-19
I'm onto my next step, which is getting my airport card recognized. I found the following site which gives instructions as to how to to do that:

[http://jomcode.com/fadhil/2008/broadcom-official-linux-driver-bcm4312/](http://jomcode.com/fadhil/2008/broadcom-official-linux-driver-bcm4312/)

He gives the following instruction I don't understand:

"Here’s the gist of what the instructions were:

Untar the file hybrid-portsrc-x86_32_5_10_27_6.tar.gz (hybrid-portsrc-x86_64_5_10_27_6.tar.gz if you’re running on a 64-bit kernel) in its own folder:

    tar -xvzf hybrid-portsrc-x86_32_5_10_27_6.tar.gz

You should now see this in your directory listing:

    hybrid-portsrc-x86_32_5_10_27_6.tar.gz
    lib
    Makefile
    src

Now build the Loadable Kernel Module (LKM) like so:

    make -C /lib/modules/`uname -r`/build M=`pwd`

**Of course, you need to make sure you have all the required kernel headers before building it.** Once that’s done, your directory listing should look like this:

    built-in.o
    hybrid-portsrc-x86_32_5_10_27_6.tar.gz
    lib
    Makefile
    modules.order
    Module.symvers
    src
    wl.ko
    wl.mod.c
    wl.mod.o
    wl.o"

The part in bold is what I don't understand. Can someone enlighten me?

---

### Post by linuxopjemac on 2010-01-19
do you have airport old fashioned ? Maybe stupid question, but i thought it was a simple kernel module. What happens if you:

```
sudo apt-get install b43-fwcutter
(when you are asked "Fetch and install firmware?" answer "Yes" (just press "Enter) )

sudo modprobe b43

sudo iwconfig

```

do you see some wireless stuff then ?

[reference]("http://https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

---

### Post by rlinsurf on 2010-01-19
This is a MacPro3,1 with the Airport built-in:

 Card Type:	AirPort Extreme  (0x14E4, 0x88 )
 Firmware Version:	Broadcom BCM43xx 1.0 (5.10.91.26)

Oh, also. How can I do the apt-get w/out an internet connection? (Wifi is the only connection for this machine)

---

### Post by linuxopjemac on 2010-01-19
I edited my post!!

---

### Post by linuxopjemac on 2010-01-19
You really have to hook it up by cable....

---

### Post by rlinsurf on 2010-01-19
> **linuxopjemac said:**
> You really have to hook it up by cable....

 Can't. It's about 150' away from the router :(

If I download bcm43xx-fwcutter_20060108.orig.tar.gz on my mac, and transfer it, can I install it from the tarball somehow?

---

### Post by rlinsurf on 2010-01-19
Ok. I guess I need to start here:

[https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")

Here's what it says:

"By default, Ubuntu does not come with the tools required. You need to install the package build-essential for making the package and checkinstall for putting it into your package manager. These can be found on the install CD."

Can you tell me how to install this from the CD? Then maybe I can get through the rest of the installs, since I've downloaded them all ;)

---

### Post by linuxopjemac on 2010-01-20
I wouldn't do it. Just go to a friend, family member or internet cafe and hook it up by cable. You only have to do this once if all is well. It's better for your package management as well to my opinion.

---

### Post by linuxopjemac on 2010-01-26
Can you explain us what you did to get it working ?

---

### Post by rlinsurf on 2010-01-26
Heh. Never did. I just went out and bought an extra long CAT 5, and plugged it in physically.

What a PITA :evil:

---

### Post by rlinsurf on 2010-01-26
Well, I got what I needed to do done, so now I'm after the airport card.

I tried following this tutorial: [http://jomcode.com/fadhil/2008/broadcom-official-linux-driver-bcm4312/](http://jomcode.com/fadhil/2008/broadcom-official-linux-driver-bcm4312/), but I'm stuck here:

```
root@ubuntu-desktop:~/Desktop/hybrid-portsrc-x86_32-v5.10.91.9.3# insmod wl.ko
insmod: error inserting 'wl.ko': -1 Unknown symbol in module

```

Any ideas?

---

### Post by rlinsurf on 2010-01-26
Answered my own question.

You must be hardwired first :(

Go to this link: [https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages]("http://https//wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages")

Find your mac model. In my case it was a MacPro3,1. I then followed the link there:

[https://help.ubuntu.com/community/MacPro#Wifi](https://help.ubuntu.com/community/MacPro#Wifi)

And skipped to the wireless section. I downloaded the Broadcom drivers, 

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

and read through and performed the commands in the readme:

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

Sure enough, my wifi network showed under Network Manger. I logged in, and boom, I was on.

HTH!

---

### Post by linuxopjemac on 2010-01-27
Good. Finally you start reading ... ;)

---

### Post by rlinsurf on 2010-01-27
:mrgreen:> **linuxopjemac said:**
> Good. Finally you start reading ... ;)

Hey! It wasn't for lack of reading. I had to get a 50' CAT5 while being snowed in. So I was trying to find some other way. It's ludicrous that I never did find a way to do it, and apparently, you were interested if it could be done, too.

So there <grin>

---

### Post by llamabr on 2010-01-27
What kind of machine is this?  Your airport card should just work.

---

### Post by rlinsurf on 2010-01-27
It's a MacPro3,1.

I know, I've read elsewhere that it should. All I know is it wasn't.

Is there something else I should have tried?

---

### Post by guybrush.d on 2010-01-29
Hi Rlinsurf,
some time ago i posted in this forum, an almost full tutorial on how set up an airport on
my ibook g3 clamshell, i had your same problem because i hadn't the cable try to search this forum
the tutorial explain how to install it with a git repository, after a restart it should work. I did it in an internet
point after 5 minutes i got internet with airport. :popcorn:

Hope this helped, Ciao

---

### Post by rlinsurf on 2010-01-29
Cool. I'll have to try that. :)

EDITED: Here 'tis:

[http://ubuntuforums.org/showthread.php?t=1008041&highlight=git+airport]("http://ubuntuforums.org/showthread.php?t=1008041&highlight=git+airport")

---

