---
title: "Macbook Pro Ubuntu 13.04 Graphics switching and battery"
date: 2013-04-30
forum: Apple Hardware Users
---

### Post by bootlessxfly on 2013-04-30
I have kubuntu 13.04 running booting through refind(efi) without grub installed. From what i can tell fglrx driver will not work(Im thinking it has somthing to do with being in efi mode). I really want to get this setup working so i have a few questions.
1.) Can i install flgrx drivers to work with this set up(From what i can tell this is a no) and can i use that to switch between intergrated and discrete(once again this seems like a no)

2.) Since i probally can't install fglrx i will be using radeon witch is fine. However id love for a gui tool for configuring it (similar to catalyst). Is there one available. 

3.) For graphics switching i know there are ways to do with patching a few things. Thats once again fine but is there a way to do all of this without grub. For example turn on integrated graphics at boot(This seems to already be done right now) and turn off amd card. Id like to be able to do all of this through (refind)refind_linux.conf if possible.

4.) I want to try to get atleast 6 hours of battery, has any one come close to this?

5.) Also before i go through all this trouble im curious to know how well the graphics switching works. I know that you turn off the amd card for suspend feature, but can it easily be turned back on. For example i am going to be using integrated for the most part but if i want to use amd card for watching something on my tv how easy would it be to switch. Is there a script to automatically do this, or maybe a program to determine when my discrete card gets turned off and when it gets turned on.

I have a feeling that alot of these answers are going to be no since i have not been able to find anything on it, but id thought id ask anyways.

6.) lastly what is the best guide for switchable graphics(i have come across a few).

Thanks for any help.
EDIT:
It would appear that both integrated and discrete can be loaded with efi stubs. Switching works  but when restarting x using integrated you get a black screen. Currently trying to compile custom kernel to see if this fixes it.
Also if you patch the kernal with a radeon_bios loading patch and use grub, it may be possible to use fglrx using grub? Any thoughts on that

Will comment on if i can get intel graphics to correctly

---

