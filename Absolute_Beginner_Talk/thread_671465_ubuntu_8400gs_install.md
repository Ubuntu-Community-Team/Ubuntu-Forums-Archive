---
title: "ubuntu 8400gs install"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by md389 on 2008-01-18
Hey guys, 
     I just recently bought an 8400gs (just arrived about an hour ago), and Im having some trouble installing it. I was previously using an old fx5200 pci, but the new card is a pci-e card, so I put it in and started up the computer. No signal. So I naturally assumed the computer got confused with so many video cards plugged in, so I took the 5200 out and then started the comp again. No signal. Once again, thought that the comp might be confused, so I took out the 8400 and started the comp. This time I got a signal, but after the splash screen the comp froze up and didn't start up. I tried booting with the onboard card and then going into the bios, changing the primary video adapter to pci-e, shutting down, putting in the card, and then rebooting, but still got no signal. For those of you that are thinking it, yes, I have been putting the vga cable into the proper slot every time I switched video adapters in the bios. I have no clue whats wrong. Im cleaning off everything and reinstalling ubuntu right now, but if you guys could just let me know how you installed your new gfx card in ubuntu (spare no detail, pretend Im dumb as rocks), that would be of great assistance. 

Thanks a lot, 
Mainak DasGupta

Comp Specs: Intel Core-D 3.2GHz
                      1 Gig of ram
                      MSI Geforce 8400GS
                      Ubuntu Gutsy Gibbon

---

### Post by sauronsmatrix on 2008-01-18
hey, i have this card and this is what you gotta do:

boot into recovery mode and let it try to autoconfigure X.

now restart, and boot into ubuntu. It should work, if it doesn't reinstall ubuntu with the "safe graphics mode" choice.

when you get into ubuntu with the display showing and all, go to the synaptics package manager, and install

nvidia-glx-new


then, in a command line run:

sudo nvidia-glx-config enable

Restart, and tell me if it works. it should! :D

---

### Post by md389 on 2008-01-18
Hey man, 
    Here is the status update on the situation. So I reinstalled ubuntu. Put in the new card. Booted with the vga cable still attached to the onboard slot. Everything loaded up just fine. So I installed glx-new and enabled the config in the terminal. Then I rebooted, and switched the vga cable to the gfx card...no signal. So I thought Id check in Screens and Graphics whether my gfx card is detected and it is in fact not. So Im guessing I shouldnt have skipped the first part "autoconfigure X". How exactly do I do that? is that sudo dpkg-reconfigure xserver-xorg? and if it is, when it asks me what slot the card is in the format is "PCI:0:2:0", since this is a pci-e card, what should I put in? Let me know. Thanks for your help so far. 

Mainak

---

