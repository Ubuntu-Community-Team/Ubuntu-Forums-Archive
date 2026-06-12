---
title: "iSight in Maverick?"
date: 2010-09-05
forum: Apple Hardware Users
---

### Post by hwong557 on 2010-09-05
Hi,

I just downloaded the new Maverick Beta and my iSight is no longer working. It was previously working in Lucid; I used isight-firmware-tools to get a firmware out and I had a script that copied to /lib/firmware on startup, but this doesn't seem to work anymore. I have a Macbook 4,1. Any ideas on how to fix this? Thanks!

---

### Post by davim on 2010-09-07
Same problem here...

---

### Post by VanHammersly on 2010-09-09
I'm having the same problem on MacBook Pro 1,1.

---

### Post by VanHammersly on 2010-09-09
I got my iSight to work.  

Here's the short answer: I installed it as the guides suggest, shut my laptop off, turned it back on, once on, I closed the lid to start sleep mode, and opened it back up a few minutes later.  Cheese recognized the isight.

Long version: I went through the usual moves of obtaining the Apple USBVideoSupport for Leopard, not Snow Leopard, installed isight-firmware-tools and pointed it to the appropriate directory.  I then shutoff the computer and turned it back on.  No luck.  I tried resetting.  No luck.  I even purged isight-firmware-tools and reinstalled.  Same.  Here' the catch.  I have not formatted and tested this.  After installing, shut down the computer and put it back on, I closed the lid and put the laptop in sleep mode.  When I reopened it isight worked.  

This sounds ridiculous and it probably is.  Maybe there is some other variable I am overlooking. However, that's the only difference I can trace.  Try the same and post results. Install as usual, shutdown and put it in sleep mode.  I'm very curious if it works for you or if my laptop is some strange anomaly.

---

### Post by hwong557 on 2010-09-12
Yeah, I tried that and it didn't work :( Interestingly, I tried to redo the whole process ( get a AppleUSBVideoSupport, install isight-firmware-tools, cp /lib/firmware/isight.fw to somewhere safe, and have a bootup script copy it back to /lib/firmware), and this time, Cheese just locked up and froze. After I tried to close my lid, my system locked up (probably a separate bug), and I tried Cheese again, and it opened with the usual "No device found". :(

---

### Post by davim on 2010-10-14
I've followed your steps and now instead of not recognizing my camera, cheese just stalls...

---

### Post by hwong557 on 2010-10-14
Hmmm... my isight actually works now. I just carefully redid the whole process and all is well.

---

### Post by opulentorca on 2010-10-14
I have a similar problem.

An "lsusb" in the terminal reveals the following:

Bus 005 Device 003: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 05ac:8240 Apple, Inc. IR Receiver [built-in]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 09da:001a A4 Tech Co., Ltd Wireless Mouse & RXM-15 Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05ac:021a Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 05ac:8300 Apple, Inc. Built-in iSight **(no firmware loaded)**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I don't understand why the firmware isn't loading given that the a "ls /lib/firmware/isight.fw" in the terminal
confirms that the file is where it is supposed to be. I also setup the script to copy file into the directory each time the os boots too. Ubuntu just won't take it.

Macbook 2,1 - Maverick

---

### Post by sean.simpson on 2010-10-15
I have the same exact issue.  The terminal will show that the iSight camera exists however, it wont load with any application.

---

### Post by jacek_ on 2010-10-16
I have Macbook3,1 and exactly the same problem. My webcam used to work on 9.10 (used [https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight](https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight) instructions), but does not work on 10.10.

I would appreciate a solution.

---

### Post by generic.tjohnson on 2010-10-16
I got my iSight web camera working on a Macbook 2,1 under Maverick by doing the following:

1. Install 10.04 on a virtual machine in VirtualBox.
2. Put the AppleUSBVideoSupport file on the virtual machine.
3. On the virtual machine, install isight-firmware-tools and point it to the AppleUSBVideoSupport file. Upon success, it will drop the file isight.fw in /lib/firmware.
4. Copy /lib/firmware/isight.fw on the virtual machine to /lib/firmware/ on your 10.10 host system.
5. Reboot, and open up Cheese to make sure the webcam is working.

Hope this helps someone out.

---

### Post by jacek_ on 2010-10-18
> **generic.tjohnson said:**
> I got my iSight web camera working on a Macbook 2,1 under Maverick by doing the following:

1. Install 10.04 on a virtual machine in VirtualBox.
2. Put the AppleUSBVideoSupport file on the virtual machine.
3. On the virtual machine, install isight-firmware-tools and point it to the AppleUSBVideoSupport file. Upon success, it will drop the file isight.fw in /lib/firmware.
4. Copy /lib/firmware/isight.fw on the virtual machine to /lib/firmware/ on your 10.10 host system.
5. Reboot, and open up Cheese to make sure the webcam is working.

Hope this helps someone out.

Sounds reasonable. Could you upload isight.fw somewhere (ie. sendspace.com) and paste a link please? I would be grateful.

---

### Post by opulentorca on 2010-10-21
I am not entirely sure what happened but it seams the "lsusb" listing has changed. It now reads as follows:

Bus 005 Device 003: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 05ac:8240 Apple, Inc. IR Receiver [built-in]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 09da:001a A4 Tech Co., Ltd Wireless Mouse & RXM-15 Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05ac:021a Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 05ac:8501 Apple, Inc. Built-in iSight **[Micron]**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

gstreamer-properties continues to show static noise when testing the video. I have not tried the solution above using virtual box to get another version of the isight.fw but I figured I would mention the change to the usb listing in case someone can glean more information regarding a fix.

---

### Post by freshestwave on 2010-10-21
I am having the same problem.  It worked perfectly in lucid after I loaded the firmware and popped in the script.  Anyone knowledgeable have any ideas?

---

### Post by redmac68 on 2010-10-22
For me the solution to this problem was to install isight-firmware-tools-1.5.92 from here 
[https://launchpad.net/~mactel-support/+archive/ppa/+packages]("https://launchpad.net/~mactel-support/+archive/ppa/+packages"). 
sudo ift-extract --apple-driver AppleUSBVideoSupport
Then shutdown and restart. I have a macbook 2,1 running Ubuntu 10,10. :)

---

### Post by freshestwave on 2010-10-22
> **redmac68 said:**
> For me the solution to this problem was to install isight-firmware-tools-1.5.92 from here 
[https://launchpad.net/~mactel-support/+archive/ppa/+packages]("https://launchpad.net/~mactel-support/+archive/ppa/+packages"). 
sudo ift-extract --apple-driver AppleUSBVideoSupport
Then shutdown and restart. I have a macbook 2,1 running Ubuntu 10,10. :)

Worked like a charm :)  Thank you very much.

---

### Post by freshestwave on 2010-10-22
It also may be worth mentioning that although the help documentation for macbooks at
 [https://help.ubuntu.com/community/MacBook3-1/Lucid](https://help.ubuntu.com/community/MacBook3-1/Lucid)
states that it does not work with Snow Leopard installed, I had no problems retrieving the firmware from my Snow Leopard Mac partition.

---

### Post by opulentorca on 2010-10-23
Kudos and many thanks RedMac68! It has worked for me. Odd that gstreamer-properties still doesn't produce anything but static. Cheese and Skype now work though.

It is important to mention that the ift-extract -a AppleUSBVideoSupport has to be done by the root user as my regular account could not write to the /lib/firmware directory.

---

### Post by DeathStar427 on 2010-10-23
[http://x90265.homelinux.com/viewtopic.php?f=10&t=9&sid=e56d8b75b4ba01d4e1795fd51d644ace](http://x90265.homelinux.com/viewtopic.php?f=10&t=9&sid=e56d8b75b4ba01d4e1795fd51d644ace)

---

### Post by xedspace on 2010-10-23
> **redmac68 said:**
> For me the solution to this problem was to install isight-firmware-tools-1.5.92 from here 
[https://launchpad.net/~mactel-support/+archive/ppa/+packages]("https://launchpad.net/~mactel-support/+archive/ppa/+packages"). 
sudo ift-extract --apple-driver AppleUSBVideoSupport
Then shutdown and restart. I have a macbook 2,1 running Ubuntu 10,10. :)

This worked for me too. Seems to be the solution for Macbook 2,1

---

### Post by opulentorca on 2010-10-25
The isight functioned for a few days but has now stopped working. Cheese crashes and skype just displays a white screen. The green light that accompanies the camera on top of the screen no longer activates.

It works fine when I boot back into OS X.

 RedMac68 or any others who tried his suggested fix, have you experienced any problems since?

---

### Post by freshestwave on 2010-10-25
> **opulentorca said:**
> The isight functioned for a few days but has now stopped working. Cheese crashes and skype just displays a white screen. The green light that accompanies the camera on top of the screen no longer activates.

It works fine when I boot back into OS X.

 RedMac68 or any others who tried his suggested fix, have you experienced any problems since?

Mine is working fine still.  Did you create a script to replace the firmware back each time at startup?  If not follow the instructions here for creating the script:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight](https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight)

---

### Post by opulentorca on 2010-10-26
It seems that the isight works if I come from a cold boot straight into Linux. If one starts in Mac OS X and chooses to reboot and then go into Ubuntu it won't work.

Also it appears that beta of skype (~2.9) can't cope with the video for more than 30 seconds. The folks on the other end of my call say that the image freezes around the 30 second mark even though nothing appears wrong on my end with a self video preview that continues working fine.

---

### Post by trevolio on 2010-10-30
One way to make this work correctly is load OSx then reboot into ubuntu.... no idea why it works this way but it sure does, i think it loads the drivers and just leaves them running throughout the reboot.

---

### Post by dstien on 2010-11-02
I was having a problem with my isight.fw not loading.  I already had extracted it in previous verions of Ubuntu installs.  I could not figure out what was wrong, and why it wasn't loading.  When I did an 'lsusb' it recognized the isight, but in parenthesis mentioned the firmware was not loaded.  I decided to make the file executable as a program to see if that might be my problem... sure enough.  Now it works like a charm.

The way I did that was through the gui, since I'm not very proficient with the command line.  For any fellow noobs that are having problems and would like to try this, you can go to the terminal and type in "sudo nautilus" which opens nautilus window with raised permissions to change any file on the system, so be careful not to change any other files.  Then browse for /lib/firmware/isight.fw, and right click it>properties>choose the permissions tab>check the box for allow executing as a program.

---

### Post by Old Codger on 2010-11-04
> **dstien said:**
> I was having a problem with my isight.fw not loading.  I already had extracted it in previous verions of Ubuntu installs.  I could not figure out what was wrong, and why it wasn't loading.  When I did an 'lsusb' it recognized the isight, but in parenthesis mentioned the firmware was not loaded.  I decided to make the file executable as a program to see if that might be my problem... sure enough.  Now it works like a charm.

The way I did that was through the gui, since I'm not very proficient with the command line.  For any fellow noobs that are having problems and would like to try this, you can go to the terminal and type in "sudo nautilus" which opens nautilus window with raised permissions to change any file on the system, so be careful not to change any other files.  Then browse for /lib/firmware/isight.fw, and right click it>properties>choose the permissions tab>check the box for allow executing as a program.

So far, I've tried various fixes, including this one, but nothing seems to work. When I typed sudo nautilus into the terminal, I didn't get the nautilus window with raised permissions. Is there another way? It would be helpful if someone could provide either a complete, step-by-step command line progression or an idiot-proof GUI for noobs like I. :confused:

---

### Post by linuxopjemac on 2010-11-04
```
gksudo nautilus
```

---

### Post by dstien on 2010-11-04
Actually, I'm not sure that method I mentioned is actually what worked for me, either--because it's not working anymore.  At the time when I tried it, it was working, but now it's not.  I've been using Ubuntu on my Macbook (1,1) for a good three years now, and I've constantly had problems with my isight.  I can't figure it out.  I'm not a programmer, so I'm not really capable of creating a fix for this, but it's frustrating because sometimes it works and sometimes it doesn't.  Often it starts or stops working after updates, especially major updates where the kernel is changed.

Is there nobody out there who can explain a bit about why this firmware is or isn't recognized?  What else is at play here?  I'm not even looking for a solution as much as some kind of explanation.  What needs to happen in order for the system to recognize and load the firmware?

:confused:

---

### Post by Old Codger on 2010-11-04
> **linuxopjemac said:**
> ```
gksudo nautilus
```

That didn't work either. I got the desktop and nothing else.

---

### Post by dstien on 2010-11-04
Could it be that your account does not have administrative privileges?  Is your account the first one to be made on the system?  Subsequent accounts don't always have permission to administer the system. Check by going to System>Users and Groups>Advanced Settings (I'm using a spanish interface, so I'm not sure if that's exactly what it says, on the lower right).  You should be able to enter there and fine tune your permissions.  Otherwise you'll need an account with more permissions.

---

### Post by OTSB708 on 2010-11-04
> **DeathStar427 said:**
> [http://x90265.homelinux.com/viewtopic.php?f=10&t=9&sid=e56d8b75b4ba01d4e1795fd51d644ace](http://x90265.homelinux.com/viewtopic.php?f=10&t=9&sid=e56d8b75b4ba01d4e1795fd51d644ace)
Didn't work.

---

### Post by Old Codger on 2010-11-05
Hola! I was using administrative/root access when I tried it, but I'll check the settings to see if I can tweak them further.

---

### Post by Old Codger on 2010-11-08
> **freshestwave said:**
> Worked like a charm :)  Thank you very much.

After trying some of the other fixes listed here, this one also worked for me. Many thanks! :)

---

### Post by Stu09 on 2011-03-12
> **redmac68 said:**
> For me the solution to this problem was to install isight-firmware-tools-1.5.92 from here 
[https://launchpad.net/~mactel-support/+archive/ppa/+packages]("https://launchpad.net/~mactel-support/+archive/ppa/+packages"). 
sudo ift-extract --apple-driver AppleUSBVideoSupport
Then shutdown and restart. I have a macbook 2,1 running Ubuntu 10,10. :)

Worked for me :D

Thanks for that redmac68

---

