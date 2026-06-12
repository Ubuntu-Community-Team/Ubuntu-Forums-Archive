---
title: "USB question using XP in VMware"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Eggnog on 2007-06-28
I've got XP running in a virtual machine under VMware.  It runs great.  I shortly noticed, though, that I had no USB controllers.  So, intrepid searcher that I am, I search the forums and solved my problem.  I had to add USB support when the VM was offline and then enable the devices in VM > Removable Media once the VM was online.  That part went well.

However, I have my cable modem physically connected to one of those USB ports.  Once I enabled them, the network connection under Linux disconnected.  I got a big message on the panel telling me all this.  Alarmed, I shut down the VM and closed VMware.  My network was still disconnected and even though I enabled it through the icon in the panel, it still wouldn't work.  I finally rebooted and returned to normal in the world of Ubuntu..

So what is going on?  Is it that Linux unmounts the USB devices when VM takes them over?  If so, how do I remount them once I'm done with the VM session without having to reboot?  I don't know where the devices are located or what they are called.  Or am I way off base and something else is going on?

---

### Post by netgineer on 2007-06-30
> **Eggnog said:**
> I've got XP running in a virtual machine under VMware.  It runs great.  I shortly noticed, though, that I had no USB controllers.  So, intrepid searcher that I am, I search the forums and solved my problem.  I had to add USB support when the VM was offline and then enable the devices in VM > Removable Media once the VM was online.  That part went well.

However, I have my cable modem physically connected to one of those USB ports.  Once I enabled them, the network connection under Linux disconnected.  I got a big message on the panel telling me all this.  Alarmed, I shut down the VM and closed VMware.  My network was still disconnected and even though I enabled it through the icon in the panel, it still wouldn't work.  I finally rebooted and returned to normal in the world of Ubuntu..

So what is going on?  Is it that Linux unmounts the USB devices when VM takes them over?  If so, how do I remount them once I'm done with the VM session without having to reboot?  I don't know where the devices are located or what they are called.  Or am I way off base and something else is going on?

In a nutshell, I have the same problem with USB devices w/Feisty and WMware Server 1.03. I can provide some illumination, though.

Short version: Yes, USB volumes are unmounted - ungracefully - if you mount them in a VM window. I always get an alert from the host OS when I mount my flashdrive from an XP instance in VMWare. There may be a solution to your modem problem, though.

Not so short version:

Sometimes my VMs - I'm running Suse 10.1 and XP in two VMs on Feisty w/VMWare Server 1.03  in a mixed Windows/Novell environment at work - won't recognize the USB device even if Feisty does. I can gracefully unmount the USB drive in Feisty, and attempt to connect the USB device in VMWare. Most of the time, the USB controller in VMWare says "Empty" anyway. I haven't yet found a specific reason or pattern to this.

It would seem that VMWare does not explicitly allow sharing of USB devices.

Possible solution:

Instead of taking physical ownership of the modem/NIC you have running in Ubuntu, go into your network settings for your VM - when it's powered off - and change the settings so that it shares your network connection via NAT, or bridged perhaps, depending on your setup. Don't let your VM try to take physical control, i.e. 'mount' your USB device. 

Remember that your VM is the guest OS and dependent upon the host OS'es ability to control the hardware properly. If your VM takes physical control of hardware, the host OS can't use it.

Hope this helps a little.

(tagline not made yet)

---

