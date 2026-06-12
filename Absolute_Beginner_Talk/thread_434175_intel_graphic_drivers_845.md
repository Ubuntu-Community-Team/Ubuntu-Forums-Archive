---
title: "intel graphic drivers 845"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by zostra on 2007-05-05
Hi everybody,

this is my first time posting to this forum (big expectations)

i just installed kubuntu i looks nice and everything and as useful as xp (which i will get rid of once i get settled in this new world) may be even more

but i am having trouble getting the screen resolution to go higher than 1024 * 768

i have an intel 845 gevb2 mobo and i am using the onboard video

i searched the forums and installed the 915 resolution modification tool and restarted the computer but i didn't make any difference

anything else i can try

:) zostra :)

---

### Post by kyphi on 2007-05-05
What resolution did you want and what kind of monitor do you use ?  Solutions differ according to the machinery used.

---

### Post by zostra on 2007-05-05
thanks for replying kyphi 

i am looking for 1280*1024 as i had when using xp and i am using samsung sync master 753s

:neutral: zostra :neutral:

---

### Post by kyphi on 2007-05-05
In a terminal (Applications -> Accessories -> Terminal) type

sudo dpkg-reconfigure -phigh xserver-xorg

Use your up/down keys to scroll to 1280 x 1074 and press the spacebar, then Enter and exit.

You will have to restart X by pressing Control+Alt+Backspace.  Then log back in and you are done.

Enjoy.

---

### Post by zostra on 2007-05-05
really appreciate your help  kyphi

but it didn't work

this what came up after i sudo dpkg-reconfigure -phigh xserver-xorg


âââââââââââââââââââââââââ¤ Configuring xserver-xorg ââââââââââââââââââââââââââ
 â For the X Window System graphical user interface to operate correctly,    â
 â it is necessary to select a video card driver for the X server.           â
 â                                                                           â
 â Drivers are typically named for the video card or chipset manufacturer,   â
 â or for a specific model or family of chipsets.                            â
 â                                                                           â
 â X server driver:                                                          â
 â                                                                           â
 â                              sisusb           â                           â
 â                              tdfx             â                           â
 â                              tga              â                           â
 â                              trident          â®                           â
 â                              tseng            â                           â
 â                              vesa             â                           â
 â                                                                           â
 â                                                                           â
 â                                  <Ok>                                     â
 â                                                                           â
 âââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââ

i don't know what any of these mean so i just decided to go with vesa(had read something about tis while researching earlier) 

did put a star in front of 1280 * 1024
and restarted x by ctrl alt backspace
didn't change anything but 1280*1024 got added as an option under system settings
and display settings but i try to change to it there it doesn't do it and just sticks to 1024*768

:)zostra:)

---

### Post by zostra on 2007-05-05
after trying vesa i decided to try tseng
after restarted the x windows manager the computer wouldn't load up

so i went into recovery mode i typed in the same command
sudo dpkg-reconfigure -phigh xserver-xorg

selected vesa and  a star for 1280*1024
restarted the computer and viola i got 1280 * 1024

i don't what i did different the first time i selected vesa but it worked

and thanks for all your help kyphi

 :D zostra:D

---

### Post by kyphi on 2007-05-05
You beat me to it, I meant to suggest rebooting.  That's what did it.

If you run into any difficulties regarding shared video memory, go into the BIOS and increase the memory allocation to 8 MB.  See [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsIntel](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsIntel)

I am pleased to read of your success.

---

### Post by zostra on 2007-05-05
reboot duh
that must have been it

and i already have the shared memory at 8 mb knew about that since a long time back

once again THANKS for all you help kyphi

 :Dzostra:D

---

### Post by ramjet_1953 on 2007-05-05
If you are using Feisty 7.04 you are better off to use the new Intel driver, which is available in the repositories.

If you have installed 915resolution, just un-install it, using Synaptic Package Manager.

After that is done, type this in a terminal:

[COLOR="Red"]sudo apt-get install xserver-xorg-video-intel[/COLOR]

Then re-start your PC and it should have correctly detected your optimum video settings.

Regards,
Roger :cool:

---

### Post by zostra on 2007-05-06
hey thanks roger will try that out and let you know how it went
:D zostra :D

---

### Post by zostra on 2007-05-06
hey roger thanks a lot dude

i installed the new intel driver and the computer is much more responsive than before

while reading up on ubuntu before installing it everywhere it said you get a lot of support in the forums now i see that it was very true

:D zostra :D

---

### Post by shaggy2dope0001 on 2007-08-10
hey i am new on ubuntu and am looking to get away from win xp pro. i am having a similar issue with my graphx  but i can't get over 740*480 all i need is 1024*768 i am using the i810 driver and have no way of getting the intel driver that i need.

i have an intel 82845g/gl vid card

ne help would be appreciated

---

### Post by overdrank on 2007-08-10
> **shaggy2dope0001 said:**
> hey i am new on ubuntu and am looking to get away from win xp pro. i am having a similar issue with my graphx  but i can't get over 740*480 all i need is 1024*768 i am using the i810 driver and have no way of getting the intel driver that i need.

i have an intel 82845g/gl vid card

ne help would be appreciated

HI and first what do you mean you have no way of getting the driver? You have no internet or you just do know what to do?

---

### Post by shaggy2dope0001 on 2007-08-20
no idea what i am lookin for or what i need or where to look then how do i install or is it just another package?

---

### Post by daveshields on 2007-08-21
I had the same problem and -- thanks to all the folks in the Ubuntu community -- I was able to find a working solution in less than fifteen minutes.

I was so impressed that I wrote a blog post about it -- "Configuring Intel 845G video chipset on Ubuntu 7.04 Feisty Fawn desktop" , available at [http://daveshields.wordpress.com/2007/08/21/configuring-intel-845g-video-chipset-on-ubuntu-704-feisty-fawn-desktop/](http://daveshields.wordpress.com/2007/08/21/configuring-intel-845g-video-chipset-on-ubuntu-704-feisty-fawn-desktop/)

---

### Post by shaggy2dope0001 on 2007-08-24
i tried what you said but instead of beginning with the 915 drivers i am starting with the i810 drivers
once i did that it went to a blank monitor with no display at all before i was getting at least 640X480 now nothing.
i am going to try to get the 915 drivers up and going to see if they just might work....  only time will tell.

---

