---
title: "[SOLVED] Some guidance with D-Link DWL-G630"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by AndrewEsther on 2008-04-09
I know this has been talked about before because I've been reading and googling as much as I can. However, I think I know what I need to do, I just don't know how to go about doing it.

I have a D-Link DWL-G630 v. A1 card.. I don't know what chipset it is (atheros?), but I'm assuming it uses the RT61 driver available from Ralink. It could also possibly use the windows driver available through ndiswrapper. I'll probably just try one method and if that doesn't work hope and pray that the other one does.

Anyway, this is what lspci -v gives me:

02:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)
        Subsystem: D-Link System Inc Unknown device 3b08
        Flags: 66MHz, medium devsel, IRQ 11
        Memory at 24000000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Memory at 24010000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>

I have no idea what any of that jargen means.

Any help here?

---

### Post by prshah on 2008-04-09
> **AndrewEsther said:**
> 
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)
        Subsystem: D-Link System Inc Unknown device 3b08


Marvell chipset is the same as used in the newer netgear wg311v3 cards. That means that you need to use ndiswrapper. A quick-and-dirty summary of commands which assumes that you will have no problems at all follows:

```
sudo apt-get install ndiswrapper
``` installs ndiswrapper, if not already installed.

```
sudo ndiswrapper -i whatever.inf
``` Gets info about your windows drivers through it's INF file; to be used with ndiswrapper.

```
sudo ndiswrapper -m
``` adds info about ndiswrapper (and therefore your wireless card) as a loadable module

```
sudo modprobe ndiswrapper
``` loads your wireless cards windows drivers, bundled into a ndiswrapper "cocoon" for linux to use it.

```
sudo ndiswrapper -l
``` displays information on whether or not the driver has been successfully "integrated"

```
iwconfig
``` searches for and displays information about your wireless card.


If nothing goes wrong, you should have working wireless. If something goes wrong, give the results here and many will be willing to help.

---

### Post by AndrewEsther on 2008-04-09
$ sudo apt-get install ndiswrapper gives me

E: Couldn't find package ndiswrapper.


do I not have the right repositories selected??


<EDIT>
I got it... it's listed under ndiswrapper-common

at least I hope I got the right one lol
</EDIT>

<EDIT>
nope, that wasn't it.... I'm just downloading the .tar.gz and compiling it myself...
</EDIT>

---

### Post by AndrewEsther on 2008-04-09
so after fiddling with this and finally getting ndiswrapper installed (I think I got everything there, at least)

I get the first error when I try to do $ sudo ndiswrapper -i whatever.inf

I get this:
installing whatever ...
couldn't open whatever.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.


the second error I run into, probably as a result of the first error:

$ sudo ndiswrapper -l
whatever : invalid driver!

and iwconfig gives me:

lo          no wireless extensions.
eth0      no wireless extensions.


blargh!

---

### Post by j2fraser on 2008-04-09
I believe you have to replace "whatever.inf" with the filename of the windows driver for the DWL-G630. Check the installation CD it came with, or your windows partition (if you have one) for the file. I believe the driver is called "TNET1130.INF" (see [http://ubuntuforums.org/archive/index.php/t-4200.html]("http://ubuntuforums.org/archive/index.php/t-4200.html"))

Hope that helps. Good luck!

---

### Post by nickpaton on 2008-04-09
Have a look at [this]("http://ubuntuforums.org/showthread.php?t=612458") post.

If the download doesn't work, substitute the following straight off the Asus site:

```
wget http://dlsvr01.asus.com/pub/ASUS/wireless/WL-138g/Driver.zip
```

Note that WL-138G uses the same Marvell W8300 rev 7 drivers

Unzipping and going to the new Driver > WinXP folder you will find mrv8ka51.inf and .sys files you need.

HTH

---

### Post by AndrewEsther on 2008-04-10
still nothing... I get:

couldn't open MRV8KA51.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.


same thing as earlier... 

J2 - I figured that out after the first 2 attempts lol as foolish as I was for thinking that whatever.inf was an actual system file haha but I tried it for the MRV8KA51.inf file and the WG311v3.inf file, because I read two posts and each had a different driver to track down and use.

crapolla.

---

### Post by AndrewEsther on 2008-04-10
Ah-HA! I got it :-) for some reason, using the "installed windows drivers" interface and clicking the "install new driver" button, and then selecting the .inf file that way worked when the code didn't...? hmm... whatever, it's working now. although I haven't sucessfully connected to my network yet because it froze while changing my ip to static, but it was lighting and blinking and that's a vast improvement over 10 hours ago :-)

as always, thanks for the help!

---

### Post by nickpaton on 2008-04-10
I think what's happening is that you are not moving to the folder where MRV8KA51.inf and .sys are located.

Easiest way.  Find the folder where MRV8KA51.inf & .sys are located.  
In mine it is in home/nick/driver/xp/mrv8k51.inf and ///xp/mrv8k51.sys.

Now that's all a bit of a mouthful, so do a copy of .inf and .sys files from there straight into you home/yourname folder (i.e for me it would be home/nick folder).

This is where the Terminal by default looks for files, and saves you having to point ndiswrapper at the ///xp/ folder.

I assume you've installed the ndiswrapper programs  - if not in a Terminal run:

```
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
```

you now need to load ndiswrapper pointing it at the MRV8KA51.inf and .sys files.  
Since they are in your home/yourname folder, in the Terminal run:

```
sudo ndiswrapper -i mrv8ka51.inf
```

This should now find the .inf file.   

If it throws up an error try:
```
sudo ndiswrapper -i /home/yourname/mrv8ka51.inf
```

(ie for me it would be sudo ndiswrapper -i /home/nick/mrv8ka51.inf )

If it still throws up an error please would you post the location of the two files.

Now continue as per [http://ubuntuforums.org/showthread.php?t=612458]("http://ubuntuforums.org/showthread.php?t=612458")

Lets see if it is present

```
ndiswrapper -l
mrv83xx : driver installed
        device (xxxxxxx) present
```

(where xxxx are your installed driver details)

Save our settings
```
sudo ndiswrapper -m
```

Start the device
```
sudo modprobe ndiswrapper
```

Let us know how you get on.

Good luck!

---

### Post by nickpaton on 2008-04-10
Excellent news - well done!

Re the static IP - how have you specified the static IP address?

Some other hints assuming you have a simple modem to router to ububox setup:

Address: ububox ip address.

Subnet mask: usually 255.255.255.0.

Gateway Address: your router IP address.

---

