---
title: "[SOLVED] Dual boot troubles on MacBook Pro 12.1"
date: 2015-10-04
forum: Apple Hardware Users
---

### Post by Maktube on 2015-10-04
I'm trying to dual boot Ubuntu 14.04.3 on my early 2015 13" MacBook Pro w/retina display (hardware version 12.1), and I've been having a couple really frustrating problems. 

rEFInd doesn't seem to see the bootable USB drive I've made according to the instructions here: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx). I can boot into ubuntu by holding down alt/option when I star the macbook, and booting from the flash drive from there.

Once I do, though, when I try and install Ubuntu, the installer hangs at the "preparing to install ubuntu" screen after I press continue. I know other people have had the same problem, but I can't find anyone who's had it on a macbook pro, so I haven't been able to find any solutions. I don't suppose anyone knows what the fix for this is?

Thanks!

OK: I've figured out the problem. For anyone else stuck here: Ubiquity checks for free space before allowing you to proceed with the installation. For whatever reason, it thinks that my macbook doesn't have any drives large enough to install ubuntu. There's currently no way around this that's even slightly reasonable, but the workaround I used was to edit 

/usr/lib/ubiquity/plugins/ubi-prepare.py

after changing the file to read-write (with CHMOD or your choice of utility) you need to change False to True on line 53 so that it looks like this:

self.controller.allow_go_forward(True)


You can then run the installation software without further problems.

Needless to say this is pretty awful, and I think it's pretty clear that ubiquity needs some kind of option to skip the free space check, or at the bare minimum throw some kind of useful error rather than just hanging. Unfortunately this bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124)

has been around for nearly five years and nothing seems to have been done about it, so I doubt we'll see anything get fixed in the future.

---

### Post by bartatubuntu on 2015-10-05
Write the steps short but clear down that you have already managed to do. 
Then we can maybe find out when and what is going wrong. 
Also be sure you have create your USB key on MacOS X exactly the way described here: 
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)


Important: 
# If MacOS X puts .dmg after the .img keep it like that! 
# You have to have administrator permissions. 
# The USB key have to be complete empty before you begin. To be sure format it. 
# The USB key has only one partition.

---

### Post by Maktube on 2015-10-05
Here's the steps I took:

1. Installed rEFInd by downloading it and running './install.sh --alldrivers', according to [http://www.rodsbooks.com/refind/installing.html#installsh](http://www.rodsbooks.com/refind/installing.html#installsh)

2. created the USB key exactly the way the link you posted describes (OS X did add the .dmg, and I kept it. I also did format the USB stick first, and it had only one partition)

3. restarted the laptop once to be sure rEFInd was working, and it seemed to be

4. created a ~40GB partition on my hard drive that was formatted as free space

5. shut down the laptop, plugged in the bootable usb, and turned it on.

At this point, rEFInd didn't (and still doesn't) see the USB stick, only the mac hard drive and recovery hard drive. So I shut down the computer and restarted it holding down alt/option. The apple boot manager (or whatever it is) that came up had the hard drive, and another option called "EFI boot", which was the USB stick. I selected this, and it booted into ubuntu.

When prompted, I chose 'try ubuntu', and after ubuntu loads (which seems to work just fine, and I can connect to the internet, etc) I use the installation utility on the desktop. This asks me to choose a language, connect to the internet, and then asks if I want to install 3rd party software (I tried choosing both yes and no), then when I hit continue on the screen that says "preparing to install", the cursor does a loading animation for a few seconds and then the whole computer freezes. 

Hopefully this is helpful, please let me know if there's anything I need to specify better. Thanks again for your time!

---

### Post by luciano.x on 2015-10-08
Maktube, you're close.
Can you at least move your mouse?
My iMac took several minutes before "choose installation type". Maybe you have to wait a little longer?

Cheers,

edit: just noticed the "solved".

---

