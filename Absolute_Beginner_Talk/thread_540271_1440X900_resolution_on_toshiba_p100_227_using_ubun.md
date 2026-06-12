---
title: "1440X900 resolution on toshiba p100 227 using ubuntu?"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by ovidiul on 2007-09-01
how do i change the resolution? can i change it in some way?
thank you.
ovidiu

---

### Post by mikaelsnavy on 2007-09-01
What kind of graphics card do you have? (This only matters if the resolution you want is not in System -> Preferences -> Screen Resolution).

---

### Post by Majorix on 2007-09-01
First go to toshiba's site and check what your monitor's horizontal and vertical refresh rates are.

Then open a terminal, and paste this in:
```
sudo dpkg-reconfigure xserver-xorg
```

Leave everything to default except for when it asks you about your monitor's configuration choose advanced and enter those info you got from toshiba's site. And next select/deselect the res modes you want/don't want.

---

### Post by ovidiul on 2007-09-01
> **mikaelsnavy said:**
> What kind of graphics card do you have? (This only matters if the resolution you want is not in System -> Preferences -> Screen Resolution).

intel

---

### Post by ovidiul on 2007-09-01
> **Majorix said:**
> First go to toshiba's site and check what your monitor's horizontal and vertical refresh rates are.

Then open a terminal, and paste this in:
```
sudo dpkg-reconfigure xserver-xorg
```

Leave everything to default except for when it asks you about your monitor's configuration choose advanced and enter those info you got from toshiba's site. And next select/deselect the res modes you want/don't want.

the laptop specs are - I'm pasting them for toshiba site, hoping that someone will help me set up the sound as well. i have no sound at all, the tosh is completely silent, and i tried all the possibilities existant: i played with all the combinations of mixers, and other options available. but i don't know how to install things like drivers, usin the terminal. i've been a windows user all my life. I'm on vista business now, and i really want to switch to ubuntu. thank you for taking the time to help me.

----------toshiba p100 227 - pspa0e:

Technology  type : Intel® Centrino® Duo Mobile Technology featuring Intel® Core™ Duo Processor T2300E, Intel® PRO/Wireless 3945ABG network connection and Intel® 945GM Express chipset 
clock speed : 1.66 GHz 
front side bus : 667 MHz 
2nd level cache : 2 MB 
 
 
System memory  standard : 1,024 (512 + 512) MB 
maximum expandability : 4,096 MB 
technology : DDR2 RAM (533 MHz) 
 
Hard disk  capacity : 80 GB 
certification : S.M.A.R.T. 
 
DVD Super Multi drive (Double Layer)  compatibility : CD-ROM, CD-R, CD-RW, DVD-ROM, DVD-R, DVD-R(DL), DVD-RW, DVD+R, DVD+R(DL), DVD+RW, DVD-RAM 
maximum speed : Read: 24x CD-ROM, 8x DVD-ROM/ Write: 24x CD-R, 4x CD-RW, 10x HS CD-RW, 10x US CD-RW, 8x DVD-R, 2x DVD-R (Double Layer), 4x DVD-RW, 8x DVD+R, 2.4x DVD+R (Double Layer), 4x DVD+RW, 5x DVD-RAM 
type : DVD Super Multi (Double Layer) drive 
 
Display  size : 17 " 
type : Toshiba TruBrite® WXGA+ TFT display 
internal resolution : 1,440 x 900 
 
[B]Graphics adaptor  manufacturer : Intel® 
type : 945GM Express chipset 
memory : up to 128 MB 
memory type : DDR2 RAM (UMA) 
 
Internal video modes  resolution : 1,440 x 900 
maximum number of colours : 16.7 Million 
 
Max External Video Modes  Max Resolution : 2,048 x 1,536 
Max Colours : 4.3 billion 
Max Refresh Rate : 100 Hz 
Non-interlaced resolution with max refresh rate : 1,600 x 1,200 [/B] 
Interfaces  1 x DC-in 
1 x line-in 
1 x external monitor 
1 x RJ-11 
1 x RJ-45 
1 x TV-out (s-video) 
1 x i.LINK® (IEEE 1394) 
1 x external microphone 
1 x headphone (stereo) 
1 x 5-in-1 Bridge Media slot (supports SD™ Card, Memory Stick®, Memory Stick Pro™, MultiMedia Card™, xD-Picture Card™) 
4 (Left 1, Right 2, Rear 1) x USB 2.0 
 
Expansion  2 x memory slots (1 to configure) 
PC Card slot for 1x Type II card, type : ExpressCard slot 
number of expansion types : 1 
 
Wireless communication  Compliancy : Wi-Fi™ 
Network Support : 802.11a/b/g 
Wireless Technology : Wireless LAN (802.11a/b/g) 
 
Wired communication  topology : international V.90 modem (V.92 ready) 
speed : 56 Kbps data (V.90) and 14.4 Kbps fax 
topology : Ethernet LAN 
speed : 10BASE-T/100BASE-TX 
 
[B]Sound system  supported audio format : 16-bit stereo 
supported sound standards : MIDI support 
speakers : built-in Harman Kardon® stereo speakers 
manufacturer : Toshiba Bass Enhanced Sound System with SRS® TruSurround XT™ technology [/B] 
Keyboard  keys : 103 
Windows keys : 2 
inlaid numeric keypad : yes 
Hot Keys : 1

---

### Post by Majorix on 2007-09-01
Well it certainly doesn't tell enough info. I was awaiting an info in this form:
> Horizontal Refresh Rate: 50-100
Vertical Refresh Rate: 30-100

Don't get me wrong, these are not the values for your monitor ;)

You have to look around until you find an info of the sort I told you.

---

