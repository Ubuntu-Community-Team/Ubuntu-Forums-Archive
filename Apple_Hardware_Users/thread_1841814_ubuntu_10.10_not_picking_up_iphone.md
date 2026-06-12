---
title: "ubuntu 10.10 not picking up iphone"
date: 2011-09-10
forum: Apple Hardware Users
---

### Post by bobdobbs on 2011-09-10
Hi all.

I've got an iphone 16GB. It's the model that came out before the 3G.
It's running firmware version 3.0.

When I plug it into my desktop pc running ubuntu, ubuntu doesn't pick it up. I can't see it in bansee, and it wont charge when it's plugged in to the computer.
I've tested the cable. It works fine. 
(If I use an iphone wall charger with the same cable, the iphone charges.)

I upgraded from 10.04 to 10.10, because I thought that upgrading might help. It didn't.


If I start gtkpod from the commandline while the iphone plugged in, and hit 'load ipod', I see this in the terminal:

> (gtkpod:10872): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

How do I get ubuntu to recognize my iphone?

Thanks.

---

### Post by noahdiehl on 2011-09-10
I'm a total newb with Ubuntu... installed less then a week ago... I installed on an HP PC and mine was able to interact with my phone no problem (using 11.04).

Just to save you some of my iPhone headaches so far... all you seem to be able to do with the iPhone via Ubuntu is add/remove music, copy off pictures, and access the apps that share documents or what ever it is called... no backing up, no syncing contacts, no updating the iOS. I tried running iTunes through WINE and it looked all messed (the interface was just like all scrambled up and looked bizarre). I also trying running virtual machines software and installing Windows through that... it had issues with drivers and was pretty sluggish and would cause Ubuntu to be sluggish until I closed the VM and rebooted. In the end I split a 500GB hard drive and installed both Ubuntu and Windows and running a dual boot set up.

Anyways in regard to your actual issue I have full access to my iPhone with Ubuntu from the start... might you be having a USB port problem? Just to knock that off the list of possibilities... are you able to connect anything else to the USB port?... and thumb drive or external drive perhaps?

---

### Post by bobdobbs on 2011-09-10
Syncing music is enough.
Getting USB passthrough to a vm would be the next step.

Yes, I have tested the USB socket. It picks up a mouse and storage devices. So, in theory it should pick up the iphone.

---

### Post by bobdobbs on 2011-09-11
bump

---

### Post by bobdobbs on 2011-09-16
> **bobdobbs said:**
> bump

bump

---

### Post by bobdobbs on 2011-09-17
bump

---

### Post by iLeet on 2011-09-18
Try running Windows in Virtualbox or VMWare player?

my iPhone 4 worked fine in VMWare virtualizing Windows XP!

---

### Post by bobdobbs on 2011-09-18
> **iLeet said:**
> Try running Windows in Virtualbox or VMWare player?

my iPhone 4 worked fine in VMWare virtualizing Windows XP!

Cool.

Yeah - I'm running windows 7 in virtualbox. It doesn't pick up the device. The last time I had a setup like this working, the guest OS wouldn't pick up the phone unless the host OS did. Its pretty cool that you got it working though.

---

### Post by iLeet on 2011-09-18
> **bobdobbs said:**
> Cool.

Yeah - I'm running windows 7 in virtualbox. It doesn't pick up the device. The last time I had a setup like this working, the guest OS wouldn't pick up the phone unless the host OS did. Its pretty cool that you got it working though.

Give VMWare a try it should work. Does Ubuntu give you a mounting error when you plug it in?

---

### Post by bobdobbs on 2011-10-03
> **iLeet said:**
> Give VMWare a try it should work. Does Ubuntu give you a mounting error when you plug it in?

No, ubuntu doesn't give me an error when plugging it in.

I don't want to try vmware, because I don't think that the vm is the problem. At the moment, the problem is that ubuntu isn't picking up the iphone. I'd like to deal with that problem first.

---

### Post by bobdobbs on 2011-10-14
bump

---

### Post by bobdobbs on 2011-10-24
bump

---

### Post by bobdobbs on 2011-11-27
bump

---

### Post by bobdobbs on 2011-12-23
Bump

---

