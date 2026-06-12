---
title: "[SOLVED] how to play real media"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by bhadotia on 2008-03-27
how can i play real media files on ubuntu -the default player or the vlc player don't support them?

---

### Post by wolfen69 on 2008-03-27
first go to system>admin>software sources and check off all boxes. go to third party tab and check off partner. (not source code) close and reload.
then in terminal,
```
sudo apt-get install realplay
```

---

### Post by brownknight on 2008-03-27
Real player is available on Linux. Download from here:  [http://www.real.com/linux](http://www.real.com/linux)

---

### Post by StOoZ on 2008-03-27
or get 
> win32codecs codecs.
A huge compilation of Win32 codecs:

Video:
- Win32 VfW DLLs:
    Indeo Video 3.2, 4.1
    Microsoft MPEG-4 v1 & v2 beta
    Microsoft MPEG-4 v3 ( also known as DivX ;-) )
    Cinepak Video
    ATI VCR-2
    I263
    Quicktime 6 (includes 3ivX, ZyGo)
    Realplayer 9 (includes RV40)
    xanim (includes 3ivX, Indeo3/4/5)
- Win32 DirectShow filters, decompression-only support:
    Microsoft MPEG-4 v3 ( this decoder is slower than VfW one, 
      but offers wider range of picture control features )
    Windows Media Video 7
    Indeo Video 5.0
    Motion JPEG ( using Morgan Multimedia shareware codec )
- Open-source plugins:
    Motion JPEG ( using libjpeg, very slow )

Audio:
- Win32 ACM DLLs, decompression-only support:
    Windows Media Audio ( also known as DivX ;-) Audio )
    MS ADPCM
    Intel Music Codec
- Open-source plugins, decompression-only support:
    PCM
    AC3
    IMA ADPCM
    MPEG Layer-1,2,3 ( compression into MP3 is also supported )
    MSN Audio
    GSM 6.1 Audio
- Win32 DirectShow filters, untested decompression-only support:
    Voxware Metasound
    ACELP.net


this list is not updated, it supports a lot more by now.

---

### Post by bhadotia on 2008-03-27
thanks to all .wolfen69 when tried that command the following message came:
E: Couldn't find package realplay

i have downloaded the real player but  how do you install it anyway! brownknight


i have also got the codecs stooz. thanks!:)

---

### Post by StOoZ on 2008-03-27
first , make it executable:
chmod +x filename
then run it using ./filename


all in the terminal. filename = the file of real player... cant remember the name , but its suffix is .bin

---

### Post by Malta paul on 2008-03-27
If its any help, I downloaded Real Player as a .RPM package, then converted it to a .deb formate using 'Alien'
The deb package was then installed using the GDeb Package Manager. It now works fine! :)

---

### Post by bhadotia on 2008-03-27
Malta paul, whay is 'Alien'.

---

### Post by brownknight on 2008-03-27
> **bhadotia said:**
> Malta paul, whay is 'Alien'.

Ok. Here we go step by step...

1. Go to [www.real.com/linux](www.real.com/linux)
2. Download realplayer to your /home/username folder (or where ever you can easily access it)
3. Open a terminal and go to the folder where you downloaded the file RealPlayer10GOLD.bin
4. type in the terminal chmod a+x RealPlayer10GOLD.bin to make the file executable
5. then type ./RealPlayer10GOLD.bin 
6. Follow whatever instructions it says....

Good luck

---

### Post by Malta paul on 2008-03-27
Hi bhadotia
Alien is a program to convert .RPM format into a .dep format. It will work most of the time.
Check out [http://www.howtoforge.com/converting_rpm_to_deb_with_alien](http://www.howtoforge.com/converting_rpm_to_deb_with_alien)
and [http://kitenet.net/~joey/code/alien/](http://kitenet.net/~joey/code/alien/) 
for more info.
Have fun :)

---

### Post by philinux on 2008-03-27
There's a ready made deb package here.

[http://archive.canonical.com/pool/partner/r/realplay/](http://archive.canonical.com/pool/partner/r/realplay/)

The bottom one. Dont worry that is says feisty.

---

### Post by bhadotia on 2008-03-27
hello everybody i have installed the real player but how do i create an application menu launcher to real player. hope any one of you is still online!:confused:

---

### Post by philinux on 2008-03-27
Should be under Applications> Sound and Video

---

### Post by bhadotia on 2008-03-27
nope it's not there

---

### Post by Irony on 2008-03-27
> **bhadotia said:**
> hello everybody i have installed the real player but how do i create an application menu launcher to real player. hope any one of you is still online!:confused:

Assuming the launcher isn't already in Sound and Video 

System > Preference > Main Menu

Then browse to the binary to set it up (or just type realplay in the command - that might work).

---

### Post by bhadotia on 2008-03-27
sir what is a binary

---

### Post by philinux on 2008-03-27
When it asks you for a path to the executable file (binary), use this 

 /usr/bin/realplay

Make sure it's installed though. 

In a terminal type

whereis realplay

---

### Post by bhadotia on 2008-03-27
thanks every body i have got it all done now!:guitar:

---

