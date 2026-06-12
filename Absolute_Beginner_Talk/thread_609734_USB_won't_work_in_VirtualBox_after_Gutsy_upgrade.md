---
title: "USB won't work in VirtualBox after Gutsy upgrade"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-11-11
When I hit the Settings menu in VB, before starting the machine, this is what I see.

> Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND).The service might be not installed on the host computer.

After booting the machine, USB isn't available at all.  After the Gutsy upgrade, I had to reconfigure for the new kernel, but that was just 1-2 clicks and then the machine booted and everything seems to work find except this usb thing.  What do I need to reinstall?  Or should I just reinstall the entire VB program?  I hope I don't have to go that far.

---

### Post by quinnten83 on 2007-11-11
have you created the USBuser group again and added your account to it?
it on the virtualbox homepage how to do that.

---

### Post by kc5hwb on 2007-11-11
I didn't do that last time.   Didn't know it was needed this time since last time I was using it without any "usbusers group" or anything like that.  I am looking in the VB user's manual and it doesn't say anything about creating a group for USDusers.  It DOES talk about vboxusers group in Ubuntu, and I have verified that is there and working.

---

### Post by Green_Star on 2007-11-12
I am not trying to hijack this thread, I do have same kind of problem.

I am trying to connect my bluetooth usb device, i get the same error when ever i start VB.

Even after booting VB if i try the way like activating USB device by right clicking on the bottom USB icon, this is disconnecting bluetooth usb from ubuntu (i can see that bluetooth icon dissappered on ubuntu panel) and after 3-4seconds, that icon comes again on ubuntu panel and VB popsup the same error. I badly need that bluetooth working for my VB.

I have followed usbusers guide and changing the some file like .....permissions.sh and also edited fstab etc. but no luck so far. 

thanks in advance.

---

### Post by maybeway36 on 2007-11-12
Install Virtualbox from Innotek's website if you want USB.

---

### Post by Green_Star on 2007-11-12
do you mean by adding the virtualbox repos in to my repo manager? I did that, i know that if you install from ubuntu repos (open source version) then you can not get USB option. Now I can see the USB option but not able to connect it to my VM.

---

### Post by vercetti1765 on 2007-11-15
> **Green_Star said:**
> do you mean by adding the virtualbox repos in to my repo manager? I did that, i know that if you install from ubuntu repos (open source version) then you can not get USB option. Now I can see the USB option but not able to connect it to my VM.

I am getting this too. Like it is greyed out right. Except my usb worked a couple days ago.

---

### Post by kc5hwb on 2007-11-16
> **maybeway36 said:**
> Install Virtualbox from Innotek's website if you want USB.

That's what I did... but after using Synaptic to upgrade Fiesty to Gutsy, and reinstalling the new Kernel, it doesn't work. 

I may just blow-away and reinstall VB altogether.  No one seems to know how to fix this.

---

### Post by schorsch on 2007-11-16
[http://ubuntuforums.org/showthread.php?t=612985](http://ubuntuforums.org/showthread.php?t=612985)

---

