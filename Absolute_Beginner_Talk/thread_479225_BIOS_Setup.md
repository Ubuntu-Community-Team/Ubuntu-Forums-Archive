---
title: "BIOS Setup"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by gdoermann on 2007-06-20
Ok, my problem is that I have an issue with my BIOS recognizing my CD/DVD player.  I just installed a new DVD Player in an old Sony Vaio I have and now it will not recognize it (or at least it has an exclamation point next to the drive) under the boot menu.  

Windows didn't have a problem recognizing the drive and installing it, but I would like to install Ubuntu on the laptop as well.  The laptop doesn't recognize USB keys either as bootable devices (at least as far as I can tell), so I am stuck trying to setup the BIOS... and I'm a bit of a BIOS n00b.  

Please help.

---

### Post by orb9220 on 2007-06-20
> Windows didn't have a problem recognizing the drive and installing it,

I'm sorry but the bios always loads before anything else including windows. So how is it your cdrom drive is not being seen?

You mean

1) when I enter into the bios the device does not show in advanced cmos settings?
2) Or I cannot boot from a cdrom device?

If the bios cannot see your cdrom then no way can windows see it as far as I know. Unless it is some special setup I have never heard of.

What you need to do first is to enter the bios when you first turn it on. By holding the del key,F1, or what ever key it says to enter setup.

You are now in the bios which is usally a blue dos type screen with menu's at the top. 

Look in general and advance settings which shows the devices listed for ide devices it should show

IDE 0 -  Master -  such and such size Hardrive
.             Slave-  may be cdrom drive or say none.
IDE1 -   Master-may be cdrom drive or say none.
              Slave- may be cdrom drive or say none.

Your cdrom should be listed there with your Hardrive.
Then in the menu's look for boot order or boot menu which allows you to select the order of devices to boot first

On a laptop all you would have to do for most is put in the cd and turn it on and hold the c key down and it would boot from cd.

Hope this helped some.

---

### Post by gdoermann on 2007-06-20
Your, right about the BIOS recognizing the devices first.

It is the second choice; the BIOS recognizes the device, but will not allow me to boot from it.  Under the boot menu it says "Optical Drive" with an exclamation point next to it.  I am assuming it means that it is not properly installed in the BIOS, though it recognizes it as a device.  I've just never had to deal with the BIOS setup before.

---

### Post by orb9220 on 2007-06-20
Is this a laptop? or system?

Is the cdrom drive ide or sata?

Will be signing off in 10mins from Portland,Or.  Will check back tomorrow to see if it has been solved for you.

---

### Post by gdoermann on 2007-06-20
Is this a laptop? or system?

It is a laptop

Is the cdrom drive ide or sata?
I'm not 100% sure.  It is a Quanta SBW-241 Laptop DVD/CDRW Combo Drive. (It's older, so I am pretty sure it is ide)

---

### Post by orb9220 on 2007-06-20
Did you try holding down the C key while booting the liveCD?

---

### Post by gdoermann on 2007-06-20
No, what does that do?

I don't understand why it would be a problem anyways, it is the same drive I had in before.

---

### Post by orb9220 on 2007-06-20
That is how to boot from cd on alot of latops.

---

### Post by gdoermann on 2007-06-21
Sorry it has taken so long, we just took off on vacation.  I tried to boot the disk using c, but it didn’t make a difference. 

Here is what I have gathered from the BIOS:

PhoenixBIOS
Version: R0103K7
Machine Number: PCG-FRV25 (UC)

I don't know if that helps, but I think I need to update the actual CMOS... but I have no clue how to do that.

---

### Post by gdoermann on 2007-06-21
I figured it out!  The optical drive had an exclamation point next to it.. apparently that means that it isn't activated.  I activated it... and now it boots from the CD/DVD rom!

---

### Post by CrispyFried on 2007-06-21
glad its working :)

but Ive never heard of having to activate a cdrom before.. usually its just "plug it in and go." how did you do it?

---

