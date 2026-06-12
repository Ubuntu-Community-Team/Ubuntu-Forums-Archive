---
title: "Installed, wont boot"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by abzolutxero on 2007-01-06
HI,

i am a newb to ubuntu, and relatively a newb to linux.  I've had successful installs of various other distro's in the distant past, but i cant seem to get ubuntu going.

I tried to install off of the livecd, however, it would not load anything beyond the first boot menu.  it would just plain out stop right before the load screen would finish.  i booted without a splash screen and it seemed to boot fully, until a screen that said "starting hardware abstraction layer hald" and it just stuck there.

so after reading the forums for about 20 minutes or so, i decided to install off of the alternate CD.  the installation went relatively smooth, everything seemed to work in a reasonable amount of time... it finally told me it was done, and to remove my installation disk and restart.  now it hangs once again at the load screen, at like 98% percent complete loaded.  when it gets to this point, it has this thin green line that appears on the screen just below the normal orange loading bar.

my system is the following:
mobo- d915pbl
memory - 1 gig pc2-4300
proc- intel p4 3.4
dvd-rw - sony dru710a
HDD - 120 gb SATA seagate baracuda.
VDO - ATI Radeon X700 256mb pci-e

i assume that it is a problem with the video, however, i dont have any other way around the install.   the board doesnt have a vdo card, and i dont have any alternative pci vdo cards.

thanks for any help....

regards,
Brad


update-- edited grub... booted without splash screen, and got ablue screen error with xserver, said it couldnt load or wasnt configured correctly,

---

### Post by abzolutxero on 2007-01-07
bump... i think my post got burried really fast.

---

### Post by abzolutxero on 2007-01-09
right, well, i think this is why i gave up on the previous installations i attempted.... i couldn't get any help.  i know there alot of people posting to this forum, but i got like 70 views and nobody even said "i dont know man"

i have attempted to reinstall 3 times, all with success, until i attempt to boot for the first time.  i've tried to find out how to install ATI drivers from the get go, but i really dont know what to search for to figure out how to do it.  I think as a last ditch effort, i am going to throw together a different system with an older gfx card and install it onto that one.  at least then i can really get into the meat and potatoes of ubuntu.

...hope it works.

---

### Post by bigken on 2007-01-09
you could try logging in safe mode (single user mode) and run this command 
sudo dpkg-reconfigure xserver-xorg and select vesa as your video driver its worth a shot this if it works this would at least get to the desktop :-k

---

### Post by rbhigday on 2007-01-09
soemething else to consider is in the xorg.conf file to change your video card from ati to vesa.

Ati cards have problems lately. so it worth a shot.

I have the same problem but I have not solved it yet and life has pulled me away.

p.s. I have almost the same card, mine is the 512 version

---

### Post by abzolutxero on 2007-01-09
thanks for the responses, i really wasnt posting that as a cry for attention, moreso, just a being bummed out that i hadnt gotten a reply.

i will try those suggestions when i get home from work this afternoon :-D

---

