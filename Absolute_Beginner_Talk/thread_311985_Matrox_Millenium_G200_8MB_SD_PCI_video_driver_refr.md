---
title: "Matrox Millenium G200 8MB SD PCI video driver refresh problems in Ubuntu/Xubuntu 6.10"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by Foxter on 2006-12-03
Hello 

It seams there is a problem with some of the refresh rates on the Ubuntu 6.10  distribution.

My system: Sempron 2800+ AM2 procesor, Abit KN9 motherboard, 2x256MB Corsair Value DDR 533 RAM, Matrox Millenium G200 8MB SD PCI video card, an old 4,3GB  Maxtor hard disk drive and a Sony CRX 320E DVD/CD-Writer combo.I use a Mag Innovision 570FD Monitor that has no problems with 640x480 at 85Hz,800x600 at 85Hz, 1024x768 at 85Hz and 1280x1024 at 60Hz in Ubuntu/Kubuntu/Xubuntu 6.06  
I now use the Xubuntu 6.06 distro. 

I wanted to update to the Xubuntu 6.10 but I discovered that my video card drivers that came integrated in the 6.10 distro are having big problems with my monitor. I tested with a Ubuntu/Xubuntu 6.10 live CD. Except for the first screen, the starting of the 6.10 distribution was with a blank screen.However at the end I saw the desktop in 1280x1024 at 60Hz. 

Since I used the 800x600 at 85Hz in the Xubuntu 6.06 distro I ajusted the resolution to 800x600 at 85Hz. Unfortunatly the screen became blank and in the middle of the screen I saw the message OUT OF RANGE. I pushed the ESC buton and I tried to set a lower refrash rate but 60Hz refresh rate did not work eather. 

I discovered that the only thing that worked at 85Hz was 640x480. The 1280x1024 at 60Hz worked good but that is the maximum permited by my monitor. It's a 15" monitor by the way.

I had no problems with the 6.06 Ubuntu/Xubuntu distro so I think that something changed in the 6.10 distro, something that made the Matrox Millenium G200 8 MB SD PCI video driver to go crazy.

Can you please help me solve this problem ? At the moment I happily use the  Xubuntu 6.06 distro but what will I do if the problem is not solved and the following distro with LTS will have the same problem ?

Sorry about my mistakes in English, English is not my native language.

---

### Post by Foxter on 2007-03-22
With a bit of luck I should get an answer this year.

---

### Post by kvonb on 2007-03-22
Looks like you slipped through the cracks, sorry about that :?.

Unfortunately monitor frequency detection is non existent in Edgy, what I suggest you do is look on the back of your screen and find the make and model number.

Search on the net for "(make) (model) frequency", you should find them.

Once you have the Vertical and Horizontal frequencies, you can edit your /etc/X11/xorg.conf and put them on the VertRefresh and HorizontalRefresh lines.

Once you restart X you should be able to choose the higher scanrates.

Regards, Kev :)

---

### Post by Foxter on 2007-03-22
Thank you Kev. 
My monitor is a Mag Innovision  570FD, a 15" monitor. I will try to find in the manual the horizontal and the vertical refresh rates and write them in /etc/X11/xorg.conf.

---

### Post by kvonb on 2007-03-23
> **Foxter said:**
> Thank you Kev. 
My monitor is a Mag Innovision  570FD, a 15" monitor. I will try to find in the manual the horizontal and the vertical refresh rates and write them in /etc/X11/xorg.conf.

Once you find them, press <ALT><F2> and type this into the box:

```
gksu gedit /etc/X11/xorg.conf
```This is what mine looks like:

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Sony"
    ModelName      "Multiscan G500"
    HorizSync       28.0 - 121.0
    VertRefresh     43.0 - 160.0
    Option         "DPMS"
EndSection
```Don't use my frequencies, it will do nasty things to your screen :S

Regards, Kev :)

PS. If you don't get a reply to a question with in a few hours, you might want to post a new message in the same thread with just (BUMP) as the message, that brings your thread back into the "limelight" as it were :).

---

