---
title: "When Booting, USB keyboard is not detected."
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by APNelson.L on 2006-12-29
My problem is that I have duel booted my hard drive with Windows XP and Ubuntu. When I am at the boot screen my keyboard is not detected so all I can do is sit and wait for the countdown to end and Ubuntu to be selected. How do I configure my system so that I can use my keyboard? It is a USB keyboard thanks for your help.

---

### Post by smoker on 2006-12-29
sometimes you have to enable usb detection in the bios, try entering setup when the computer is started, usually the correct key is displayed, maybe f2,f10 or the del key, and look for usb options available,

hope this helps

---

### Post by APNelson.L on 2006-12-29
I am not really finding what you are talking about, I have tried changing the boot priority but that seems to do nothing.

---

### Post by teaker1s on 2006-12-29
in the bios it should have something like LEGACY SUPPORT OR USB LEGACY SUPPORT without this turned on your have keyboard problems

---

### Post by smoker on 2006-12-29
hme, it is hard to describe as each type of bios is different, and shows different named options for things, if you can get into the bios setup, make a note of the bios maker, and version, and check on their website for a guide or pdf.

in my bios, there is a list on one of the pages that scrolls down to something like 'usb detection', and you can choose some options there, but all bios's are different.

maybe you could post your pc type and bios details and hopefully someone may have the same type to advise,

---

### Post by APNelson.L on 2006-12-29
Alright, it looks like a have Phoenix - awardBIOS. I am wondering if it would be a BIOS problem or not, because I can type now and I can use the keyboard in BIOS, the only problem is using the keyboard when my system boots up. Could this be a problem with GRUB?

---

### Post by bulldog on 2006-12-30
Grub only points out where the OS's are located and has nothing to do with hardware support.
It should be a BIOS thingy.

But you can alter the count down time in GRUB,you can make windows boot by default too.
[code]## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0 **count the entry's in menu.lst till you see windows and change zero with     that number**

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3 **change this in the amount of seconds you like**

---

### Post by davidleelambert on 2007-01-11
I have the opposite problem:  I use a Dell P4/3.4GHz workstation with Ubuntu Breezy installed,  hooked up to a KVM switch using PS/2 cables.  The USB support in the BIOS has been turned off,  because otherwise Linux won't detect the PS/2 keyboard and mouse (I tried booting it that way,  and had to go hunt down a USB keyboard to shut the system down).  Unfortunately,  that means I can't use any other USB devices.  Is there a kernel option I can add to grub to force preference of a PS/2 keyboard and mouse?

---

### Post by Erlander on 2007-01-12
In my Award bios there is an option to enable/disable usb Keyboard support.

Go to Integrated Peripherals, scroll down to it using your down arrow key, press Enter press the down arrow key to move to enable, press enter again.

Then with your arrow keys move to Save and Exit Setup, press enter and enter again to save.

That should do it.

Rob

---

