---
title: "Boot Menu - doesn't respond to keyboard"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by Penguin Power on 2007-01-01
I installed Ubuntu this afternoon, keeping my existing Windows XP installation. I was hoping to be able to dual boot and choose which operating system i want at startup. I get a boot menu such as this:
[IMG]http://nirlog.com/wp-content/uploads/2006/07/grub.jpg[/IMG] 
although the various Ubuntu options are at the top, and Windows XP at the bottom.

I should be able to use the cursor keys to boot windows, but my keyboard doesn't work ](*,) 

Anyone else had this problem?

---

### Post by akudewan on 2007-01-01
Hmm..thats odd. Does the Num-Lock key work? Can you press Del to enter the BIOS settings? First thing I'd do is check if the keyboard is plugged in correctly.

If you have a wireless keyboard, make sure you haven't run out of batteries

---

### Post by SoloSalsa on 2007-01-01
Do not-cursor keys work?  If no, is it a USB keyboard?  If yes, then it means your computer does not support USB keyboards, in that minimal form.  I use a USB keyboard, and have no control over my computer until I'm at the desktop, when the USB drivers are loaded.

---

### Post by hoges on 2007-01-01
Are you running it on desktop or laptop? If desktop & usb keyboard, as the last poster said it's probably the cause.
If it's a laptop, it may be that the num lock or function key is on. If this is the case, either use the secondary numlock keypad or disable it.

I assume you had keyboard control during the install? If so, i can't see why it wouldn't work. Have you made any hardware changes since the install?

---

### Post by Sef on 2007-01-01
It could be Vista also.   There has been workarounds for dual booting it and Linux.

---

### Post by Frak on 2007-01-01
USB Keyboards rarely work during the GRUB boot loader, because its still being driven by the BIOS, and depending on how advanced your BIOS is, it may not even try to recognize USB ports.

---

### Post by andyp11 on 2007-01-01
If it's a USB keyboard then I suspect what you have to do if to get into the BIOS and ENABLE "usb legacy devices" - or something like that - then that should fix it.

---

### Post by Penguin Power on 2007-01-01
perfect! Legacy USB devices enabled, everything working

i think that's my new record for smallest time spent on trying to fix a problem like that on the computer - post on a forum, go to bed, sleep then get up and fix it. *bing* problem solved.  :rolleyes:

---

### Post by adewale on 2007-01-01
its not a linux problem i had this same problem even before i knew about linux. it occurred when i needed to reinstall windows

---

### Post by Pitt Stains on 2007-01-01
I am having the same problem.  The computer is a desktop and the keyboard is not usb.  The secondary boot is Windows XP.  I did have keyboard control during install, and the only hardware change I've made is to add the second hard drive which contains the Windows installation.

Would moving the keyboard forward in the boot order help?  Is there a way to do that?

Thanks!

[COLOR="Red"]EDIT[/COLOR]
Oh boy, nevermind.  It seems my keyboard was plugged into my mouse port.  Not sure how that happened... miracle Ubuntu recognized it at all!

---

### Post by SoloSalsa on 2007-01-01
Pit Stains, that was clever, LOL.
Does anyone here know *why* USB is *always* disabled?  Why don't the BIOS ship with it on, standard?  I don't see anything bad or different, at all, with it enabled.  Really, why do we always have to go out of our way for it?

---

### Post by nithinraju on 2007-01-01
I'm trying to run the Ubuntu 5.10 Live cd to get a taste of the OS before i decide if i want to dual-boot with it or not. However, i keep getting the same error message.

After tinkering with the boot parameters (seems i only need "live noapic nolapic" to get to the error), it runs fairly well. It goes through the processes, with a black screen and an orange "Ubuntu" logo in the middle. Below it, processes are run and checked. It gets to a black screen with white type, and pauses at "Checking Battery Charge" or something similar.

After that, a blue screen pops up (BSOD in linux?!) and says "There is a problem with your X server (graphical interface), and it may not be setup correctly." It then gives me the option to view detailed information (sorta like system specs) about the error. Then it says that "X server will be disabled" or something, and the paragraph includes "GTD". I forgot to write down the message, but i can retrieve it if it's needed.

So what am i doing wrong? Is there a boot parameter i need to input? What's this X server, and how do i edit how it's setup?

If it matters, i'm running an eMachines with AMD 64 3000+, 1gb ram, 150gb hd, 128mb ATI xpress 200, with XP.
spam link deleted

---

### Post by Frak on 2007-01-02
You might want to try Dapper or Edgy instead, hardware is better supported, Xserver may not see your card, or your card may not support the vesa driver, either way try those and see what happens.

---

### Post by Psquared on 2007-01-22
Same problem with USB Keyboard. I literally have to plugin an old PS2 keyboard at the grub screen to move the cursor.

I checked my bios and there is a "USB Legacy" choice, but its for "mice" only and not a USB keyboard. Weird. 

I wonder if there is an award BIOS upgrade for this mobo. Its a 4 year old MSI with an AMD processor. I guess I'll have to get the model number and go to their website.

---

### Post by SoloSalsa on 2007-01-22
> **Psquared said:**
> I wonder if there is an award BIOS upgrade for this mobo. Its a 4 year old MSI with an AMD processor. I guess I'll have to get the model number and go to their website.
Very, *very*, likely.  Be sure to backup, or locate a copy, of your current version.

---

### Post by Stew2 on 2007-01-22
I also had a problem with the keyboard not being detected at the grub screen. In my case it turned out to be my precious Model M keyboard was not recognized by my Asus P4P800E Deluxe motherboard... something about the Model M's requiring more voltage than a standard keyboard. There is a fix that involves soldering some resistors into the keyboard. Or you can use a  PS2 to USB adapter. In my case I have a KVM switch that I plugged in and that solved the problem. I know this was not the problem the OP had, just figured I would post this in case someone else with a Model M has a similiar problem and finds this thread :D .

Regards,
Stew2

---

