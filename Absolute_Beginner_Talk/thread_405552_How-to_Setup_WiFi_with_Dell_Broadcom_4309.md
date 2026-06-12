---
title: "How-to Setup WiFi with Dell Broadcom 4309"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by smackywentz on 2007-04-09
Okay I had two days worth of trouble getting this setup and when I finally got it it turned out to be very easy. I am using the Beta release of Feisty Fawn and I have a Dell Inspiron 2200 with an internal wifi card. That card is a Broadcom Corporation BCM4309 802.11a/b/g.

To check and see if you have this network card go to Applications > Accessories > Terminal. 

Then simply type **lspci**.

Near the bottom of all that information you should get something similar to the following:
[B]
02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)[/B]

The following is how to get wireless working.

Note: This works for all broadcom wireless cards **except** BCM4318. As far as I know...

Okay first thing you need to do is open your Synaptic Package Manager. [There are other ways to install this, but they never worked for me...

Go to System > Administration > Synaptic Package Manager.

Then in the upper right hand corner of the Synaptic Package Manager window click search.
In the search field, search for "**ndis**."

Here you will need to mark all of the following for installation:
[LIST]
[*]ndisc6
[*]ndiswrapper-common
[*]ndiswrapper-source
[*]ndiswrapper-utils-1.9 *1.9 can be substituted for whatever version shows up in your Synaptic Package Manager*
[/LIST]
*Note: Do not install "[I]ndisgtk*", this created many problems for me and is unnecessary. It also has a tendency to crash.[/I]

Now click **Apply**.

Once these have installed we now have to get our necessary driver. If you have read other forums on this problem you have probably downloaded your driver, well it turns out with Feisty there is no need to do this. 

All we need to do is open our terminal window. To do so go to Applications > Accessories > Terminal.

Here we have a few simple lines of code to put in, don't worry this will work.

First run the following command:
**sudo apt-get install bcm43xx-fwcutter**

Now when that command has run, it should have extracted itself. Near the bottom of the code you should see a few lines saying extracted...

If not do the following:
**sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o**

Then:
**sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` ~/Desktop/wl_apsta.o**

Now that the firmware has been extracted do this:

Run:
**sudo apt-get install network-manager-gnome**

And then:
**modprobe bcm43xx**

Almost done!
Go to System > Administration > Network

Make sure your wireless is enabled and in **Roaming Mode**

Congratulations! Everything works and you are done.

*Note: This was a very specific "how-to," if you have any questions please e-mail me at [email]smackywentz@yahoo.com[/email] .*

---

### Post by stingbot on 2007-04-21
Man, thank you so much.  I have a Broadcom 4309 rev 02 on feisty fawn (the newly released version, not beta), and this set of instructions is the only thing that's worked for me.  Nice to not need ndiswrapper.

I found the .sys file i needed for bcm43xx-fwcutter from the ndiswrapper wiki:
[http://ndiswrapper.wiki.sourceforge.net](http://ndiswrapper.wiki.sourceforge.net)

Also, I don't know if it was necessary but I used synaptic to remove the network-manager-gnome (and network-manager) before I installed bcm43xx-fwcutter.  After I completed the bcm43xx steps, I re-installed the network manager.  

At that point, the manager detected (or equivalently through iwlist <interface> scan) the available wireless networks.  I wasn't able to connect to anything until after I rebooted.

---

### Post by cam_tram on 2007-04-21
Installing ndiswrapper is unnecessary, the driver you're using is native.  Nice howto though.

---

### Post by gustrix on 2007-04-25
Thanks man. Your method worked like a charm for me. 
Have a Dell D800 with BCM4309 based wireless card. Had it running with Ndiswrapper on Edgy but after I did a clean install of Feisty that just wouldn't work. 
Had messed around so much so I did a new clean install today, followed your method and now I'm up and running.
I could mention that I had to do a networking restart to get it going.
sudo /etc/init.d/networking restart

---

### Post by Globox on 2007-06-30
This worked perfectly, thank you!

---

### Post by gb5757870 on 2007-07-20
I was so hoping this would work but when I installed fwcutter, got this garbled response:

Sorry, the input file is either wrong or not supported by bcm43xx-fwcutter.
This file has an unknown MD5sum 0c5ffe204a083fcdf623aa47acfefcbd.
dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by saadakhtar on 2007-07-20
you can try installing the linux native driver for your broadcom card.

look for my post on [this page]("http://ubuntuforums.org/showthread.php?t=349824&page=3"). this has always worked for me so, hope it works for you.

---

### Post by gb5757870 on 2007-07-21
thanks mate. I continued hunting around to see what the story was with the firmware and found a help link somewhere that directed to me another page which from where the firmware could be updated. So just installed the package and hey presto, works a treat.  I did have to reboot but that's all.

cheers

---

### Post by areseapea on 2007-09-17
Why isn't this more widely advertised?  I had the same problem with the Dell TrueMobile 1305 (which is a BroadCom bcm4306 card) and having failed with bcm43xx-fwcutter (Sorry, the input file is either wrong or not supported by bcm43xx-fwcutter) this worked perfectly, straight away!  Installed the package and up it came!

A lot easier than fwcutter or anything else!  A true "It just works" Ubuntu trick!

---

### Post by saadakhtar on 2007-10-06
the easiest and best possible way to get your broadcom chipset card to work is use the linux native broadcom driver.
its called "wlan-ng"
you can search for wlan-ng using synaptic and install it and thats it your card should work.

---

### Post by viperrepiv on 2007-11-05
I look forward to trying this when i get home tonight.  I was banging my head against a wall when i was trying to set this up last night.  After much messing around, i got the thing to scan, but the wifi could not connect to anything.  So first things first, I think i'm going to try that firmware download that gb57 recommended.  Then, I'll try going through the long process if that doesn't work.  Crossing my fingers!

---

### Post by ctodd111 on 2007-11-25
Thank you Thank you Thank you Thank you Thank you Thank you Thank you Thank you Thank you Thank you Thank you Thank you Thank you Thank you Thank you Thank you Thank you Thank you Thank you Thank you  Well, you get the idea...

After spending two entire days (one day until 4:30 am) trying to get my BC 4309 working in Fedora 7 I am ecstatic to have the wireless working in Ubuntu thanks to your instructions.  I am sooooo happy.....

---

