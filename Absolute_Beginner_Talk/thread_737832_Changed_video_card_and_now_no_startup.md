---
title: "Changed video card and now no startup"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by foxbro on 2008-03-28
I installed a video card i had lying around after I installed 7.10 and now when I turn on the computer it doesn't start up. The furthest it gets is to the "splash" screen where the progress bar moves from left to right then the screen goes black and then nothing happens. Before I installed the card I was just using the on-board video adapter.

EDIT:the keyboard is also unresponsive after it gets to the blank screen.

---

### Post by cisforcojo on 2008-03-28
Unfortunately, a LOT of linux apps are dependent on what kind of video card you have.
What did you have before and what did you switch to? If, for example, you went from ATI to NVidia,
you -might- want to consider a re-installation if you were using an advanced setup like Compiz Fusion.

At the very least, you're probably going to have to boot into safe mode and edit /etc/X11/xorg.conf for your new card.

---

### Post by foxbro on 2008-03-28
The origional video card I was using was the intergrated IBM one that is on the motherboard and the one I installed was I think a nVidia

---

### Post by foxbro on 2008-03-28
is there a way to update the drivers from the Live CD?

---

### Post by mrsteveman1 on 2008-03-28
There aren't any drivers to update, the system should be able to boot just fine using the existing in kernel drivers and the xorg NV driver.

If the system isn't booting past the progress bar, either the init scripts are stalled for some reason (shouldn't happen forever), or the kernel crashed or had a panic.

You should definitely try booting single user mode by adding the word "single" to the end of the kernel line in grub, this should tell you whats working and what isn't. If the kernel refuses to boot in single user mode you will get an error message on the screen as to why most of the time.

---

### Post by cisforcojo on 2008-03-28
I don't believe so, but there's hope yet!
Here's what you should do:
1. Boot up into 'safe mode' and edit /etc/X11/xorg.conf
```
sudo vi /etc/X11/xorg.conf
```
You'll want to change your driver in the "Device" section to "nv".
```
Section "Device"
   ...
   Driver "nv"
   ...
EndSection
```   

vi can be a little tricky if you've never used it before so I'd recommend you check this out first if you're not familiar: [http://www.washington.edu/computing/unix/vi.html](http://www.washington.edu/computing/unix/vi.html)

2. Reboot your computer and go into BIOS. Make sure you integrated/onboard video card is DISABLED.

3. Load up into Ubuntu as normal. System -> Admin -> Restricted Drivers Management and install the nVidia driver.

Let me know if you run into any problems!

NOTE: If you really hate vi, you can always use the LiveCD to mount your existing partition and then edit /etc/X11/xorg.conf with gedit.

---

