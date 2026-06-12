---
title: "USB Devices not showing up on VirtualBox Ubuntu Install"
date: 2009-09-07
forum: Apple Hardware Users
---

### Post by djross95 on 2009-09-07
Hi, I'm experimenting a bit with Ubuntu after not using Linux for the last couple of years.  I've installed 9.04 on an Apple iMac using the latest version of VirtualBox.  The install went pretty well, I've got sound and everything seems to be working fine.

Except for when I attach a USB key to copy files over, it does not mount on the Ubuntu desktop.  It shows up on the Apple desktop, and it appears "grayed out" on the USB device icon at the bottom of the Ubuntu window, but it can't be accessed.  I'm not sure what to do.  

I hope the above is clear, and thanks in advance for your help!    DR

---

### Post by djross95 on 2009-09-08
Hello?  Anyone out there? ........      :-)

---

### Post by kpholmes on 2009-09-10
i run ubuntu on a virtual box aswell and just to let you know that the guest os (ubuntu) is not going to recognize the hosts usb ports unfortunately. so in short terms, its not going to work. just like it doesnt recognize the true video card. until virtulization gets a little more developed then best bet is use a live cd when ever you need to use usb

---

### Post by djross95 on 2009-09-10
Thanks for your reply (though it's not good news!).  I'm trying to transfer music and photos from the Mac side to Ubuntu. The latter won't recognize HFS-formatted disks, of course, so I thought a USB key would do the trick.  Back to square one!

Any other ideas on how I might do this?    

Thanks again.       DR

---

### Post by KingLear0 on 2009-09-11
This may or may not apply but...

Which version of VirtualBox did you install?  The VirtualBox Open-Source Edition (OSE) does not support USB passthrough.  

I know that when I installed VirtualBox on my Jaunty machine, I had to  use the non-open source version in order to have the virtual machine read my USB devices directly.  


Alternately, you might be able to use Guest Additions add-on (if it exists for the Mac version of VirtualBox)  If Guest Additions can be installed, you can then access your MAC's files by setting them up as shared folders in the guest additions options for VirtualBox.

---

### Post by The Thug on 2009-09-11
You have to install the PUEL version of VB and not the OSE version.

OSE does not support USB, whereas the PUEL version does.

I'm in a similar predicament in that I had the PUEL version working perfectly but after upgrading through Synaptic, my USB ports are greyed out.

---

### Post by djross95 on 2009-09-11
I'm running VirtualBox v. 3.06 (with Guest Additions installed).  I got VBox from the VB website, I didn't know there were different versions, but checking again it looks like I have the PUEL version installed. 

I will try the Guest Additions workaround as suggested by KingLear0 and see if that works.

Thanks for the help and ideas!    DR

---

