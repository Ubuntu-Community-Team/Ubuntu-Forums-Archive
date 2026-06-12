---
title: "why does my sound card not work in feisty?"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by acorn22 on 2007-08-19
I have used ubuntu for a while and have never had a problem like this before. On a clean install of Feisty Fawn the sound card does not work. 

When I do 'lspci' the cad shows up, but whenever I try to play a sound file in xmms for example, it tells me there is no device or it is busy or something.

When I right click on the volume control and select open volume control, it says there are no Gstreamer plugins or devices found.

I have no idea how to start diagnosing this problem :/ 

Thanks

---

### Post by Happy_Man on 2007-08-19
I hope you have installed the Gstreamer plugins and such? If so, then what is the name of your sound card?

---

### Post by acorn22 on 2007-08-19
Yes it is installed. What do you mean what is the name of my card? How do I check this?

---

### Post by Happy_Man on 2007-08-19
Enter the command ```
lspci
``` it should tell you.

---

### Post by Hobo Joe on 2007-08-19
Try running the commmand
```

sudo asoundconf list

```
Then out of the card(s) it lists, you need to select a default. Even if there is only 1, try running this command
```

sudo asoundconf set-default-card <yourcard>

```
That fixed it for me.

---

### Post by Dr Small on 2007-08-19
Is your sound enabled in your bios? If not, that would be my first guess...

---

### Post by acorn22 on 2007-08-19
Thanks everybody

```

lowell@minty:~$ sudo asoundconf list
Password:
Names of available sound cards:
lowell@minty:~$ 

```

```

lowell@minty:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0a.0 Ethernet controller: Microsoft Corporation Unknown device 0002 (rev 11)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
lowell@minty:~$ 


```

I'll look in my bios next time I reboot (soon)

---

### Post by acorn22 on 2007-08-25
Ok I checked in my bios, everything is ok (I even reset all settings via the jumper on the mobo) And still there is no sound. I tried the Sayabon live DVD and it gives me a simmilar error message.

Also when I try to play a .avi file in Mplayer it tells me the device -vo was not found. Is this a gstreamer problem?

---

### Post by AstarothCY on 2007-09-18
> **acorn22 said:**
>  I tried the Sayabon live DVD and it gives me a simmilar error message.


Sounds like your card is fried.

---

