---
title: "Kubuntu, VMware, Bluetooth and Palm sync"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by beachedwhale on 2007-06-03
I just installed Kubuntu 7.04 VMware image (running in VMware Player 2.0) yesterday.  I'm quite impressed so far but I still have a ways to go to figure out if I can do nearly everything in Ubuntu  that I have been doing in XP.  One of those things (and perhaps the most difficult thing) is to sync my Palm TX, so I want to get this one solved early on.

My PC has a Bluetooth dongle and is currently set up for Bluetooth use via XP, also for Palm sync via Bluetooth using that horrid Palm Hotsync software (please tell me what's in Ubuntu is better!).  Is it possible for me to sync my Palm device in the Kubuntu VM image using Bluetooth (or USB cable if I absolutely have to)?  If so, where do I start?  If not, then is this something that'd work better if I did a real installation of Ubuntu?

All I know so far is that people on here seem to recommend JPilot and pilot-link; I haven't tried those yet.  When I start the VM, I get a popup that it detected the Kensington Bluetooth Adapter; I think this message is coming from VMware Player, not from Kubuntu.  I'm not sure if I should be trying to disable the Hotsync and Bluetooth software that's running in XP and to then set it up in the VM, or if I should leave the Bluetooth software on XP alone and somehow let VMware Player share that device somehow (as it appears to be trying to do).  The potential device contention issues puzzle me.

Any tips on where to begin?

Thanks!

---

### Post by lazyart on 2007-06-03
You'll have to enable USB in the virtual machine.  Once you've done that you'll probably find it easier to just sync by USB cradle/cable (otherwise you're adding a step-- install/configure bluetooth, then configure syncing software to use it).

I use Jpilot to sync my TX.  Set the serial port to "USB:" and it should fly through the process.  It's really, really simple.

---

### Post by beachedwhale on 2007-06-03
Figures my USB cable is now lost; I never use it so I didn't keep track of it.  So, I've been trying to get Bluetooth to work anyway.

Without doing anything, it seems that pressing the hotsync button on the Palm initiates a "Bluetooth Serial Chat" with Ubuntu, so VMware is automatically passing this device on to Ubuntu.  This connection that happens is using some service named kbtserialchat.  Now, I know that I need a "serial port" connection set up somehow in Bluetooth if I'm going to sync using jpilot, but is this "serial chat" something else?  The Palm sends unreadable characters repeatedly to the serial chat window, and of course replying in that serial chat window does no good because there's no such chat s/w on the Palm.

How do I install and configure a "Bluetooth Serial Port" service like I have in Windows?  In Windows, COM3 is mapped to this service.  I'm not sure if this thing passes through to VMware or if it's something I should disable in Windows first.

If I can get that set up, I see that jpilot has a Setting called "Serial Port" that is currently blank, with suggested values of /dev/ttyS0 and /dev/pilot.  I'm not sure if the Bluetooth serial port service would map to /dev/pilot or something else yet.

---

