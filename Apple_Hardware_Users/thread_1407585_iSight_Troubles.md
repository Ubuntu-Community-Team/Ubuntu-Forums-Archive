---
title: "iSight Troubles"
date: 2010-02-15
forum: Apple Hardware Users
---

### Post by Zomaian on 2010-02-15
So I installed iSight by doing the following:

```
sudo aptitude install isight-firmware-tools

```Than I also did:
```

bob@LivingRoom:~$ sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport
[sudo] password for bob: 
** Message: Found Mac OS X.4 intel driver
** Message: Firmware extracted successfully in /lib/firmware/isight.fw
** Message: Apply patch 0 : Fix video control interface descriptor
** Message: Apply patch 1 : Fix video streaming interface descriptor
** Message: Apply patch 2 : Fix video streaming device qualifier
** Message: Firmware patched successfully

```I located the AppleUSBVideoSupport file and all the folders and files including isight.fw were in their place. I rebooted my computer and opened the Photo Booth program Cheese Webcam Booth and my camera worked!

Now I restarted by computer a while after that and suddenly iSight didn't work anymore. I did the steps over again that worked the first time but no luck. I did some research and on the Ubuntu site it said that I got to put the isight.fw it in the /lib/firmware/ and reboot my computer to make it work. I even made a little script that places the isight.fw to /lib/firmware/ when I start the computer by:

Made a file called "script-webcam"
```

#! /bin/sh

cp /home/imac/isight/isight.fw /lib/firmware/. 

```As you see I made a location called /home/imac/isight/ which contains the isight.fw and when the script is executed the copies the isight.fw file to /lib/firmware/. The script works and I added it to Startup Applications. I rebooted my computer but guess what? Cheese Webcam Booth still can't find my iSight.

How come that it found the iSight for the first time and now not any more? It has all the folders for isight-firmware-tools and everything seems to be good. Could anyone care to help?

Thanks a lot,
Bob.

---

### Post by Tycho59 on 2010-02-15
Something I've learned when installing software for certain things in Ubuntu (like the firmware for iSight) is that you actually need to completely shutdown the computer and then start it back up into Ubuntu in order for the software to take affect and be recognized every time there after.

Also, it is alot easier if you were to just drop the isight.fw file right into the /lib/firmware folder this way it is garunteed to work each and everytime.

---

### Post by Zomaian on 2010-02-15
> **Tycho59 said:**
> Something I've learned when installing software for certain things in Ubuntu (like the firmware for iSight) is that you actually need to completely shutdown the computer and then start it back up into Ubuntu in order for the software to take affect and be recognized every time there after.

Also, it is alot easier if you were to just drop the isight.fw file right into the /lib/firmware folder this way it is garunteed to work each and everytime.
I tried that and it just does not work

---

### Post by Zomaian on 2010-02-15
I did the following nothing works:

**Try 1:**


[LIST=1]
[*]Install isight-firmware-tools
[*]Locate AppleUSBVideoSupport
[*]Shutdown iMac - Bootup
[/LIST]
The isight-firmware-tools was installed correctly and there was a isight.fw file in /lib/firmware/

[B]Try 2:

[/B]
[LIST=1]
[*]Install isight-firmware-tools
[*]Locate AppleUSBVideoSupport
[*]sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport
[*]Shutdown iMac - Bootup
[/LIST]
Everything was in place once again but no luck

[B]Try 3:
[/B]
[LIST=1]
[*]sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport
[*]Shutdown iMac - Bootup
[/LIST]
No luck, the isight.fw was in /lib/firmware/ but iSight still didn't work.


I did these try's in several ways and orders, removed isight-firmware-tools, reboot, than install again no luck!

I tried it on Cheese, Gstreamer, Skype, Erika, and Camorama. Once again when I installed it for the first time it worked I installed it by doing this in the terminal:

```

sudo aptitude install isight-firmware-tools
sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport

** Message: Found Mac OS X.4 intel driver
** Message: Firmware extracted successfully in /lib/firmware/isight.fw
** Message: Apply patch 0 : Fix video control interface descriptor
** Message: Apply patch 1 : Fix video streaming interface descriptor
** Message: Apply patch 2 : Fix video streaming device qualifier
** Message: Firmware patched successfully

```Rebooted the iMac, launched Cheese, took some pictures and vidoes and it all worked. Than I rebooted my iMac a while after that and iSight didn't work anymore.

Anyone good any other tips?

Edit: So I restarted my iMac and when loading GRUB I pressed ESC and F2 or F7 not sure either way I got this error:

```

[10.847812] ehci_hcd 0000:00:1d.7: fatal error
[10.851306] ehci_hcd 0000:00:1d.7: HD died; cleaning up
[10.851874] Failed to initialise isight firmware loader
[10.865039] hub 1-0:1.0: hub_port_status failed (err = -19)
[10.865101] hub 1-0:1.0: connect-debounce failed, port 7 disabled
[10.865165] hub 1-0:1.0: hub_port_status failed (err = -19)
[11.435122] uhci_hcd 0000:00:1d.1: host system error, PCI problems?
[11.485179] uhci_hcd 0000:00:1d.1: host controllers halted, very bad!
[11.485250] uhci_hcd 0000:00:1d.1: HD died, cleaning up
[11.788029] Failed to initialise isight firmware loader.

```Note: I wrote this on a piece of paper and copied it from the paper on here so their might be a spelling mistake here or there in the numbers. All I can say from this is that it fails to load the iSight firmware on the boot.

---

### Post by Zomaian on 2010-02-15
Sorry for another bumb but I fixed the problem and I would like to let you guys know how I fixed it for people that are having the same issue:

**Fix:**

**Step 1: **Uninstall isight-firmware-tools by either going in the Synaptic Package Manager or using the Terminal.
```

sudo apt-get remove isight-firmware-tools

```Now the problem is that it does not fully remove all drives and files so:

**Step 2: **Log into root powers by doing the following in the Terminal:
```

gksudo nautilus

```Go to Computer -> File System and Search for **isight**. After a view seconds/minutes you should still see some folders and files appear even after you removed isight-firmware-tools. Delete as many files and folders as you can, I was able to delete maybe 10 out of the 15 files/folders. 

**Step 3: **Completely **shutdown** your computer wait a view seconds start it up again. At the bootup when the white Ubuntu splash appears on the black background their might appear some text saying its fixing some drives etc. This is probably because you deleted/touched the drive folders to delete the isight junk.

**Step 4: **Install isight-firmware-tools in the Terminal by doing:
```

sudo apt-get install isight-firmware-tools

```Make sure to direct the to the AppleUSBVideoSupport I had it on my desktop so my patch was "/home/bob/Desktop/AppleUSBVideoSupport". If you still got your old Mac installation 10.4 or 10.5 you can fetch it with this patch "/System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport".

If you directed it to the wrong patch or it gives you an error make sure to do the following:
```

sudo apt-get remove isight-firmware-tools

```Than **completely** shutdown your computer and retry step 4.

**Step 5:** Once installed completely shutdown your computer, wait for a few seconds and start it up again. Than launch Cheese Webcam Booth and hopefully you will see your self!

**Other Things:**

When doing this I had my Ubuntu 9.10 installation Disc in so when booting the iMac backup I had to hold the Option key and select the Hard Drive. I highly doubt that this has any influence at all but just letting you know what I did ;).

Enjoy and thanks for all the help!

---

### Post by linuxopjemac on 2010-02-16
just read the wiki please, I think it says there that you have to purge  isight-firmware-tools, meaning not only removing the driver, but also all config files. That will do the job

---

### Post by Zomaian on 2010-02-16
> **linuxopjemac said:**
> just read the wiki please, I think it says there that you have to purge  isight-firmware-tools, meaning not only removing the driver, but also all config files. That will do the job

As I said I did that multiple times and if you read the post good you would have understood that when you purge/remove isight-firmware-tools it didn't delete all the isight files and folders on my File System so I had to delete them by hand.

---

### Post by Tycho59 on 2010-02-17
There are 2 different remove commands that can be used if you're trying to start over with the firmware install.

I'm guessing that you tried:

     sudo apt-get --purge isight-firmware-tools

Try using this line of code for removing all of the isight firmware files for a fresh start on installing the isight firmware:

     sudo apt-get --purge remove isight-firmware-tools


Another user in this forum suggested this second code to me while i was working with the coding that's suggested in the how-to guide that's on the site.

Hope this new line of code works for you.

---

### Post by linuxopjemac on 2010-02-17
Zomaian: I didn't mean it negatively! ;)

---

### Post by linuxopjemac on 2010-02-17
I edited the wiki page. Thanks Tycho59 for the suggestion.

[https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight](https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight)

---

### Post by Zomaian on 2010-02-17
> **Tycho59 said:**
> There are 2 different remove commands that can be used if you're trying to start over with the firmware install.

I'm guessing that you tried:

     sudo apt-get --purge isight-firmware-tools

Try using this line of code for removing all of the isight firmware files for a fresh start on installing the isight firmware:

     sudo apt-get --purge remove isight-firmware-tools


Another user in this forum suggested this second code to me while i was working with the coding that's suggested in the how-to guide that's on the site.

Hope this new line of code works for you.
I guess that would have worked, never got the change to try it!

> **linuxopjemac said:**
> Zomaian: I didn't mean it negatively! ;)
It's fine, my bad for being so negative :P.

---

### Post by bkadoctaj on 2010-03-21
> **Zomaian said:**
> Sorry for another bumb but I fixed the problem and I would like to let you guys know how I fixed it for people that are having the same issue:

**Fix:**

**Step 1: **Uninstall isight-firmware-tools by either going in the Synaptic Package Manager or using the Terminal.
```

sudo apt-get remove isight-firmware-tools

```Now the problem is that it does not fully remove all drives and files so:

**Step 2: **Log into root powers by doing the following in the Terminal:
```

gksudo nautilus

```Go to Computer -> File System and Search for **isight**. After a view seconds/minutes you should still see some folders and files appear even after you removed isight-firmware-tools. Delete as many files and folders as you can, I was able to delete maybe 10 out of the 15 files/folders. 

**Step 3: **Completely **shutdown** your computer wait a view seconds start it up again. At the bootup when the white Ubuntu splash appears on the black background their might appear some text saying its fixing some drives etc. This is probably because you deleted/touched the drive folders to delete the isight junk.

**Step 4: **Install isight-firmware-tools in the Terminal by doing:
```

sudo apt-get install isight-firmware-tools

```Make sure to direct the to the AppleUSBVideoSupport I had it on my desktop so my patch was "/home/bob/Desktop/AppleUSBVideoSupport". If you still got your old Mac installation 10.4 or 10.5 you can fetch it with this patch "/System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport".

If you directed it to the wrong patch or it gives you an error make sure to do the following:
```

sudo apt-get remove isight-firmware-tools

```Than **completely** shutdown your computer and retry step 4.

**Step 5:** Once installed completely shutdown your computer, wait for a few seconds and start it up again. Than launch Cheese Webcam Booth and hopefully you will see your self!

**Other Things:**

When doing this I had my Ubuntu 9.10 installation Disc in so when booting the iMac backup I had to hold the Option key and select the Hard Drive. I highly doubt that this has any influence at all but just letting you know what I did ;).

Enjoy and thanks for all the help!

Followed these directions on MacBook4,1 with Ubuntu Lucid Alpha 3 (64-bit) and it worked perfectly!  :)  Thank you.

---

### Post by hellrazor35 on 2010-03-22
Succesfully installed firmware,,,,,Thanks for all the help.
iSight works perfect in cheese and gstreamer.
However cannot get to function in browser based programs i.e Tinychat and Stickam. I'm guessing it's a flash issue. Any suggestions???

---

