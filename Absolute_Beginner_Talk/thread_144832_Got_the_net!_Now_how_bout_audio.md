---
title: "Got the net! Now how bout audio?"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by AlaskaLinux on 2006-03-15
I have a nice soundcard need to know how to config in ubuntu.. loving the switch from MS so far! just new and need help! here is my lspci output.. can someone help?

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8605 [ProSavage PM133] (rev c4)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8605 [PM133 AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
0000:00:0a.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)


thanks!!

---

### Post by meborc on 2006-03-15
you don't hear any sounds when loging in to gnome? ... what about the volume icon on right up corner... can you open it, or does it say _no device found_ ? ...

have you installed all codecs? try automatix if you haven't.

---

### Post by AlaskaLinux on 2006-03-15
I hear no sounds.. I can see the speaker icon and adjust volume.. but still no sounds

---

### Post by meborc on 2006-03-15
how about codecs? read this [https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29)

---

### Post by _simon_ on 2006-03-15
in terminal type: alsamixer

have a play with the sliders. Pressing "M" will turn any on that are off. The up and down arrows control the volume.

My Audigy 2 didn't work until I moved the audigy sliders up.

---

### Post by AlaskaLinux on 2006-03-15
Kaffeine Part...
Part not found. Please check your installation!
KDE...
Found version: 3.4.3
Ok.
xine-lib...
Found version: 1.0.1
Ok.WIN32 Codecs...
Ok.
libdvdcss...
libdvdcss not found. You're not able to play encrypted (most commercial) DVD's. You can get the library here (but using it may violate copyright regulations of your country!): [http://developers.videolan.org/libdvdcss](http://developers.videolan.org/libdvdcss).
DVD Drive...
DMA mode off! For smooth DVD playback run as root: "hdparm -d1 /dev/dvd".
DVB-Device...
No DVB-Devices found. The DVB related functions will be hidden.
Distribution...
Ok.
RESULT: Found some problems, but nevertheless Kaffeine may work.

help?

---

### Post by AlaskaLinux on 2006-03-15
thanks for the reply but the "alsamixer" command didnt work :(

---

### Post by meborc on 2006-03-15
[QUOTE=AlaskaLinux]thanks for the reply but the "alsamixer" command didnt work :([/QUOTE]
what do you mean it didn't work? what was the output in terminal?

---

### Post by AlaskaLinux on 2006-03-15
it worked but they were all turned up.. I need to put a cd in to test my audio I htink

---

### Post by AlaskaLinux on 2006-03-15
There were no decoders found to handle the stream, you might need to install the corresponding plugins

---

### Post by meborc on 2006-03-15
did you check the restricted formats link i posted earlier? ... i am between two things... either you don't have correct codecs... OR you have a mixup in onboard/soundcard settings... if the codecs are ok, then try right-cliking on the volume icon and there should be preferences.. or smth... enyway you should be able to change the device... and that is important...

---

### Post by AlaskaLinux on 2006-03-15
cant hear anything from an audio cd ... dang

---

### Post by AlaskaLinux on 2006-03-15
I can change the device .. but not to the right one! my envy24 is not to be found in the device switcher..?

---

### Post by _simon_ on 2006-03-15
A silly but obvious question...

Are you sure the speakers are plugged into the correct input to the card and have power?

---

### Post by meborc on 2006-03-15
[QUOTE=_simon_]A silly but obvious question...

Are you sure the speakers are plugged into the correct input to the card and have power?[/QUOTE]

:mrgreen: damn... i didn't even think to ask that...

---

### Post by AlaskaLinux on 2006-03-15
the speakers are plugged in and have power :P

---

