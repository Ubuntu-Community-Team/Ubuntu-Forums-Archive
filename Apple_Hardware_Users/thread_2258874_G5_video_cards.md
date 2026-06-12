---
title: "G5 video cards"
date: 2014-12-31
forum: Apple Hardware Users
---

### Post by robert-mathew-harris on 2014-12-31
I've got a PowerMAC G5 2.3 ghz dual core with the nvidia 6600. I was curious if I could take a PCIe video card from my windows machine and use it in the G5 with Ubuntu. I know I would need Mac firmware for osx but I don't care about that. Would it not be a better option than what's in it considering all the nouveau issues?

---

### Post by robert-mathew-harris on 2015-01-03
well i might be on to something with nouveau + the nvidia 6600 that comes in the PowerMAC G5 towers. ever since ive tried running linux on one i would be very unstable, well the nouveau driver has had issues with this card and specifically on PPC. well i have psensors installed and it opens when i boot up. i had been using the old NV driver i compiled from source so it would stop crashing. with the old NV driver i get no temp sensors, but i tried booting with nouveau just to mess around and noticed a new temp sensor in the list. i had been using the computer alot already and it was at like 81 degree C. ! I thought it was just an error and paid it no mind. well needless to say the computer still locked up on the nouveau driver so i powered it down and went to bed. Well tonight when i got home i fired up the MAC cold with nouveau driver and the temp was down at 40 when i started and was steadilly climbing just sitting there at a desktop with psensors running. within 10 minutes it was up to 70 so i went ahead and shut it down. I'm curious if nouveau's lack of thermal managment is the big issue with this card. by the way im running ubuntu 12.04 lts PPC using gnome desktop manager.

---

### Post by robert-mathew-harris on 2015-01-04
ok im confused. ive been running this PowerMAC G5 for about 3.5 hours now with the nouveau driver.i have no options in my yaboot, not even splash or quiet in my append line currently. i have no xorg.conf file. I dont know what ive done to get it this far. im currently running ubuntu 12.04 because i had so many issue with lubuntu 14.04. I havnt done any updates that i know of. my GPU temps are crazy to me but from what ive read is still acceptable for this card. at cold boot from being off for a few hours gpu temp starts at about 40c and climbs to 81c just at idle. but under load only got to 86c in an hour. has anyone else had this card work with nouveau in a POWERMAC G5? everything ive read was the old NV or fbdev. its a geforce 6600 256mb that comes in the macs.

---

### Post by robert-mathew-harris on 2015-01-04
another weird one i just noticed, was playing game to see what temps it took to lo lock it up and got it to lock at 85c but it apparently still kind of working cause i can still access sensor information from another computer via psensor-server. the screen on the mac is froze no more game sound no keyboard response, not even cap lock light and its and old wired keyboard. as soon as it crashed cpu usage went down and my gpu temp went back down to the 81c idle. is this jus simply a harware issue? i havnt actually run osx on this particular machine but had same issues in an idetical one that has osx when i tried ubuntu on it. can anyone turn on a light at the end of this tunnel lol

---

### Post by James_R_Igou on 2015-01-08
Personally, I can barely get the Nvidia 6600 to work, and it has some display issues with my monitor.
I'd rather use my Radeon 1950GT, but I don't know the boot parameters I would need for that.

---

### Post by robert-mathew-harris on 2015-01-09
as far as the 6600 goes ive got it running stable but slow. ive had to compile the old opensource NV driver and use it.  i tried pputting a card i ihad in it , a geforce 8400gs, but wouldnt boot without a nomodeset yaboot argument which is what i dint want because it use a fbdev driver or somthing and has terrible color, 8bit i think.  the NV driver looks fine just no 3d accel at all. I dont have any other cards to try and i dont want to buy something i can barely use. it would be nice if nvidia would compile their proprietary drivers for PPC but i doubt that will ever happen. im wondering if i would be better off wth an ati card

---

### Post by James_R_Igou on 2015-01-09
Thanks Robert,
I guess this is going to take some work.
As to ATI  cards, the only OF compatible card I know of is the 1950GT, which I'm  having even less luck with than you are having with the Nvidia 6600.
I may follow your lead and switch back.Right mow, the AGP G5s seem better supported.
But I'm using my AGP G5 for MorphOS, so I'm going to keep plugging at this.
Its frustrating.

---

### Post by este.el.paz on 2015-01-09
> **robert-mathew-harris said:**
> ok im confused. ive been running this PowerMAC G5 for about 3.5 hours now with the nouveau driver.i have no options in my yaboot, not even splash or quiet in my append line currently. i have no xorg.conf file. I dont know what ive done to get it this far. im currently running ubuntu 12.04 because i had so many issue with lubuntu 14.04. I havnt done any updates that i know of. my GPU temps are crazy to me but from what ive read is still acceptable for this card. at cold boot from being off for a few hours gpu temp starts at about 40c and climbs to 81c just at idle. but under load only got to 86c in an hour. has anyone else had this card work with nouveau in a POWERMAC G5? everything ive read was the old NV or fbdev. its a geforce 6600 256mb that comes in the macs.

@robert:

I don't know anything about G5, but I did have to do some work to get linux running on my G4 iMac; one thing I think that would be needed for 14.04 is an xorg.conf file . . . fairly easy to do in the grand linux scheme of DIY--and then you probably could specify any card you wanted to use . . . .  It's interesting that you are still able to get the NV driver, I heard it was no longer available in the "repositories" . . . but, in my Xubuntu 12.04 on my G4 I was able to retro-compile the nv driver, but, really the fbdev driver is fine if you have the refresh rates set properly in your xorg.conf file . . . .  Thinking back on the 12.04 threads here in PPC I don't recall seeing too many heat issues being talked about, but, maybe I wasn't paying attention--the wintel Macs do have a heat management issue . . . .

Anyway, Ubuntu tends to be a little more hungry . . . you could try Lubuntu 12 or 14, or Xubuntu 12.04, but it is no longer supporting PPC in 14.04 . . . you could add the XFCE4 DE to Lubuntu and see how that goes, it's lighter so should run "cooler" . . . .  In terms of your original question, don't know--if it's easy for you to change it, it should be easy enough to change it back.

e.e.p.

---

### Post by robert-mathew-harris on 2015-01-11
i for got to mention this s a later model g5 with NO agp all pcie slots includind the 6600 is pcie.
 
I did try lubuntu 14.04 bt i think there are some issues with the newer kernel or somthing because even compiling and using the old NV driver i would have some hard cpu lockups. ubuntu 12.04 runs great on it i just have no 3d accel of any kind so i have to use either unity 2d or failsafe gnome or something like that. as far as the NV driver goes i jus found the latest source package and compiled it myself, wasn't too difficult i think i even found a guide on it. if i can find it again ill link it if anyone needs it. and with the NV driver i have a very minimal xorg.conf file just a driver and device line, no yaboot parameters needed, not even the famous video=ofonly lol

---

### Post by robert-mathew-harris on 2015-01-11
is it just me or is the 81 degrees C temp seem quite high for idle? I dont have osx installed to check it but that jus seems crazy to me. heck i even put fresh thermal paste on it with no difference. now thats with nouveau, i dont know what my temps are with the NV driver as there is no temp support in it.

---

### Post by robert-mathew-harris on 2015-01-12
Well I've been trying to get my GeForce 8400 GS to work in this mac with no luck.I have both the original 6600 + the 8400 gs and I can boot and get display on the 6600, nothing on the 8400. here's my xorg.conf.

Section "Device" 
        Identifier    "6600" 
        Driver        "nv" 
    BoardName    "GeForce 6600" 
#    BusID "PCI:0:0a:0" 
EndSection 
 
Section "Device" 
        Identifier    "8400gs" 
        Driver        "nv" 
    BoardName    "GeForce 8400 GS Rev. 3" 
#    BusID "PCI:1:6:0" 
EndSection 
 
Section "Screen" 
   Identifier  "screen1" 
   Device      "6600" 
EndSection 
 
Section "Screen" 
   Identifier  "screen2" 
   Device      "8400gs" 
EndSection 
 
Section "ServerLayout" 
    Identifier  "Default Layout" 
    Screen  0   "screen1" 
    Screen  1   "screen2" RightOf "My screen 1" 
EndSection

 I have the BusID comented out because it will boot into low bit display no matter what I've put there

#lspci | grep VGA
0000:0a:00.0 VGA compatible controller: NVIDIA Corporation NV43 [GeForce 6600] (rev a2)
0001:06:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 8400 GS Rev. 3] (rev a2)

Oh a weird one i noticed not only will it not boot without the MAC firmared 6600 in it, it won't even boot if a monitor is not connected to it.
thanks for all the help so far and any more that I may get.

---

### Post by robert-mathew-harris on 2015-01-13
Well i just tested and there is deffinatley a temerature difference between linux+nouveau and osx whith these GeForce 6600 cards. OSX at idle the GPU is at 51 C, ubuntu 12.04 ppc with nouveau its 81 C. I think that may have to do with it crashing under the nouveau driver, I cant test the temps with the open source NV driver, but it runs on NV without constant crashes, unlike nouveau.

---

### Post by rican-linux on 2015-01-13
You may need to set cpu frequency scaling to help with that. See [the Ubuntu wiki]("https://wiki.ubuntu.com/PowerPCFAQ#How_can_I_use_powernowd_for_CPU_frequency_scaling.3F").

---

### Post by robert-mathew-harris on 2015-01-14
see its not CPU its GPU, the grapghics card is over heating with nouveau.not the CPU, sorry I should have put graphics card , GPU and CPU do look very similar.

---

### Post by robert-mathew-harris on 2015-03-10
Has anyone had any experience with the G5 on Ubuntu lately.

---

### Post by este.el.paz on 2015-03-10
If you check the thread "Testers wanted for Ubuuntu MATE 14.04 lately it's all been about G5 . . . which I again, don't have, but they seem to be cooking some fun stuff there.

e. . .

---

### Post by luigiburdo on 2015-03-12
If you have a more  Pcie slots like is my Quad G5 you can use a RadeonHD video board on G5 but you need the 16x slot used by the Video Board with Apple PPC firmware (example the 6600) and the 8x used by RadeonHD . 

 This is mate running on my configuration .
Note RadeonHD is working only (for now) on Mate 14.04.x on 15.x.x for now is not working 
and on Lubuntu 14.04
On debian the Radeon HD are not working .

Mate (nvidia+radeonhd)
[https://www.youtube.com/watch?v=NyShy_ey7Ds&list=UUkb4bw4N19d-x_tn2FXLojQ](https://www.youtube.com/watch?v=NyShy_ey7Ds&list=UUkb4bw4N19d-x_tn2FXLojQ)

Lubuntu (ati x1900gt +RadeonHD)
[https://www.youtube.com/watch?v=zp_IvG7h5_0](https://www.youtube.com/watch?v=zp_IvG7h5_0)

i suggest to everyone to use the nvidia + RadeonHD becasue the x1900 boards speens like turbo jet when linux start running on RadeonHD


edit : i hope the mos team can use this tip for make Mos running on Radeonhd on g5 quad ;-)

---

### Post by robert-mathew-harris on 2015-03-12
hey can you tell me how you got the non apple radeon to work on there? what was your xorg.conf like? i couldnt ever get my non apple nvidia to display anything.

---

### Post by luigiburdo on 2015-03-13
Hi robert just did experiments ;-)
but all my experiments was related radeonhd ...  i dont have an invida to test here.
I cant share my xorg.conf because there isnt a /etc/X11/xorg.conf file in my filesystem all was did by the dri and kernel i think.
How i make the video work?
this is my Linux start command line

```

Linux video=offb:off video=nouveaufb:off video=radeonfb:off nouveau.modeset=0 radeon.modeset=1

```

I think for your pc invidia will be 

```

Linux video=offb:off video=nouveaufb:off video=radeonfb:off nouveau.modeset=1 radeon.modeset=0

```

Note i was not luck to have my Nvidia (Apple firmware) work with Mate but nvidia work great with Debian Wheezy 
do a try to Debian(wheezy and Jessi) too ;-)

---

### Post by robert-mathew-harris on 2015-03-14
thats awesome you got it to work so easily, so far the only success ive had with this apple firmware nvidia has been to compile the old open source NV driver and set xorg.conf to use it instead of nouveau or fbdev.  I have been think about try debian out, seems people have better luck with it and the nvidia cards.

Does anyone know if you can run 2 diferent nvidia drivers at the same time? id like to use nouveau on one card and nv on another but i think they would conflict eachother.

---

### Post by luigiburdo on 2015-03-14
whit radeon x1900 i had the opportunity to have the radeonhd working probably will be the same for the nvidia.
the tip is in the video=offb: off this command deactivate the open firmware video boards

---

### Post by luigiburdo on 2015-03-14
just buy this ... will test and report  ;)


[http://www.ebay.it/itm/131445848576?ssPageName=STRK:MEWNX:IT&_trksid=p3984.m1439.l2649](http://www.ebay.it/itm/131445848576?ssPageName=STRK:MEWNX:IT&_trksid=p3984.m1439.l2649)

---

