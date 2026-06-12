---
title: "No Sound"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Frank_F on 2007-08-24
Hello,

Not able to get any sound out of my computer speaker using Rythmbox or any other app


frank@frank-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 Communication controller: Agere Systems LT WinModem (rev 02)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]


Thanks

---

### Post by SpiritIsReality on 2007-08-24
howdy

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

best to open up your box and check for your sound card specs
or your manual if you have one, or check your manufacturer's 
web page

not sure if that's your sound card or a modem
once you're sure what your sound card is you can follow
along here and search for what's right for your card
hope this helps til someone more knowledgeable shows up

[http://www.google.ca/search?hl=en&q=site%3Aubuntu.com+sound&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntu.com+sound&btnG=Google+Search&meta=)
[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)
[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)
[http://alsa-project.org/main/index.php/Main_Page](http://alsa-project.org/main/index.php/Main_Page)
[http://alsa-project.org/main/index.php/Matrix:Module-via82xx](http://alsa-project.org/main/index.php/Matrix:Module-via82xx)

once you know the right driver module name, like it says, you add it to the
/etc/modules file

free linux books online
[http://ubuntuforums.org/showthread.php?t=484846](http://ubuntuforums.org/showthread.php?t=484846)

trails
(in debian i ran alsaconf to get the card to work after adding the module,
but i don't think it's included or necessary in ubuntu)

---

### Post by jcconnor on 2007-08-24
Are you using ALSA or OSS?

Found this:

    * Sound Chip
          o Works under alsa using the VIA 82C686A/B, 8233/8235 AC97 Controller driver in the kernel, under PCI sound cards. 

in this[ site]("http://gentoo-wiki.com/HARDWARE_Acer_Aspire_1353").

One other thing would be to make sure that the sound is not muted (I know you probably have but :) ).  Just right click on the Volume control and choose Open Volume Control.  You can adjust the volume, and also check the device under the File menu.

John

---

