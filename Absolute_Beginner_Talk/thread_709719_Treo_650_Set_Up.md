---
title: "Treo 650 Set Up"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by gr8dane on 2008-02-27
Hey all I have a problem.  I am running Kubuntu on my laptop, Celeron 2.6ghz 1gb ram and I want to sync my Treo with it.  I am having problems with kpilot and I am not getting any help on the Kubuntu forum.  Can someone point me in the right direction?  

Here is what I have done so far, installed kpilot and kitchensync, when I start kpilot or kontact then push the sync button, nothing happens.  Kpilot just says that it is waiting for me to connect the USB cable.  The cable is connected.  I know it is a good cable too.

Any help?

---

### Post by pieisgood4589 on 2008-02-27
Try this- do it STEP by STEP. It worked for me...

[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

Yup. That's what I did.

---

### Post by gr8dane on 2008-02-27
I saw this link and emailed it to myself at home during my lunch break.  :D  Did you type in visor or did you type in Treo?

---

### Post by Whiffle on 2008-02-27
Its "visor," even though its a treo.  Its just the name of hte module that talks to them.

---

### Post by gr8dane on 2008-02-28
I tried this in kpilot and it didn't work.  Using Kubuntu Gusty gksuo gedit don't work.  What are the equivalents to gksudo gedit?

---

### Post by gr8dane on 2008-02-29
Success!  Thank you all for the help and direction.  Here is what I did.  Instead of using Kpilot with kontact, I installed Evolution and set up gnome-pilot.  

Then I created /etc/udev/rules.d/10.costom.rules.  In that I typed

BUS=="usb", SYSFS{product}=="PalmOne Handheld*", KERNEL=="ttyUSB*", NAME{ignore_remove}=="treo", MODE=="666"

BUS="usb", SYSFS{product}="palmOne Handheld*", KERNEL="ttyUSB[13579]", SYMLINK="pilot.

Then totally by accident I found out that my Treo ID was 27059. I tried to sync with the default ID 1000 but gnome-pilot was kind enough to give me an error with the 27059 ID.  I changed that in my settings.  Then in gnome-pilot settings conduits I set each of the defaults to sync and TaDa my treo syncs with evolution!

Hope this helps someone else.

---

