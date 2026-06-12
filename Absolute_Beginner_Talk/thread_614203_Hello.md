---
title: "Hello"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by KcAV on 2007-11-15
I have decided to try Ubuntu on the desktop. I thought I would start by asking for advice on the Beginners Forum concerning my approach and where I might look for information.

I plan to install Ubuntu on a notebook with a 64-bit processor.  I can make a bootable CD.  Where should I download the latest version of Ubuntu from?  What tutorial should I use to become familiar with the Ubuntu user interface?

The notebook connects to a LAN through ethernet cable.  Where can I learn about Ubuntu’s networking capabilities?  For instance, how to get it into a DHCP table.  

The notebook also gas wireless netwoek adapter and will need to be synchronized with a workstation on the LAN where its master files are stored, and with a mobile hand held device.  Does Ubuntu have these capabilities built-in?

When I am working at my desktop I use a 17” secondary monitor. Are there any known problems with Ubuntu’s ability to connect to a secondary monitor?

The notebook must connect with four USB peripheral devices:  (1) Polycom, Communicator C100S (2) Wacom drawing tablet (3) BlackBerry, Pearl 8100, and (4) LG MultiScribe DVD burner.  Where should I look for drivers, and how should I test a driver?

What speech recognition capabilities are built into Ubuntu?  What third party speech recognition software is available to run on Ubuntu?

These are matters I have on my mind as I begin to work with Ubuntu. I would appreciate any directions you want to provide to sources of information, or comments about Ubuntu in general. 

Thanks.
KC

---

### Post by Inxsible on 2007-11-15
you can download Ubuntu from [here]("http://www.ubuntu.com/getubuntu/download")

also have a look at this [link]("http://www.psychocats.net/ubuntu/installing") which helps you install Ubuntu if you want to dual boot

Ethernet is pretty much supported out of the box. Wireless depends on what wireless card you have. Most are easily configured.

Using secondary monitor depends on your graphics card. Nvidia are said to be better supported than ATI, but ATI support is growing too.

I am not sure about the Polycom, but people have been able to connect Wacom tablets, phones using bluetooth or USB, CD and DVD burners are supported out of the box. I am not sure if you have a lightscribe drive, because that is one thing that's not widely supported. Although thats changing.

---

### Post by KcAV on 2007-11-15
Download under way. It takes eatimate 58minutes. 

Catch you later.
KC

---

### Post by KcAV on 2007-11-15
I have LG, External Super Multi DVD Rewriter model GSA-E3OL. Nero Express software came bundled with the drive.  

I am very interested in integrating this device into my work flow. It has Light Scribe labeling capability.  I would also like to use this device to create  DVDs with menus, and do multi-session burning of data having different formats. 

How should I proceed to integrate this with Ubuntu?

---

### Post by KcAV on 2007-11-15
On the website where I am downloading Ubuntu, I found a Software Catalogue, but it did not contain any reference to speech recognition software; any suggestions where to look for speech recognition software?

---

### Post by DoctorMO on 2007-11-16
I have a blackberry pearl too and I'm working on making barry (the syncing and device management software for blackberries) easy to install and use; could you email me if you would like to do testing for us to get this hardware device working out the box?

The wacom tablet is another interesting one, you have to reconfigure xorg.conf to get pressure sensitivity and that isn't so easy; the drivers should be installed by default and the wacom tablet will act as a standard mouse (without pressure) out of the box.

---

### Post by KD6TZF on 2008-01-29
I have LG, External Super Multi DVD Rewriter model 65A-51690.  It worked under Ubuntu 6.06 Dapper Drake for a short time.  I may have done something to make it quit working - but not sure.  I have since upgraded to Ubuntu 7.10 Gutsy Gibbon and still have it plugged in to my computer, but unable to get it working.  The lights come on, on the front panel.  The drive bay opens and closes, but it's like the computer doesn't recognize that it is hooked up.

I go to "Places" and "Computer" and the browser window opens and shows me that the External CD-RW/DVD +/- RW Drive is listed.  When I click on it I get an error message that says  "Unable to mount media".  I have a known good CD in the drive that was produced by that drive before it quit working.  (I know it works because I can read the disc in another drive.)  Anybody got any suggestions?

I can use the terminal window, but I don't know what to do once there.  I used to enjoy DOS Command Line functions, but that has been many years ago.

Thanks,

---

