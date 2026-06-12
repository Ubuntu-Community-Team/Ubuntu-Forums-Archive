---
title: "[SOLVED] My Sound....Gone Again!!!"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Don1500 on 2007-12-31
OK I had all sounds al modes (Except Record for some reason)
Turned the system off, Came back and nothing, squat, zippo, Nada.

I will now play around, change all my settings, twice. Fool around in terminal, reinstall my driver (cmipci by the way) reboot a million times and will not get the sound back. Turn the system off, go watch a football game come back and the sound will be there! WHY?.
Is there something I don't know about? Some set up in Grub that I should set up to refresh the system to the last good config, or does my system have little guys from MicroSoft creeping through just to mess my mind until I give up and go back to Wndoze?

Just to get on top of things:
> ~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
02:05.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
02:0c.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
 
So, Yes my Card is recognized.

System=>Preferences=>Sound:
All Tests work, 
Computer Sounds (Log In , Log Out, etc.) Do NOT work.

Movie Player => Works with MP3
Amarok => Will NOT play anything (The Graphic display shows that Amarok THINKS it is playing, but no sound.) It's like it is muted (ALL MUTING IS OFF)

---

### Post by kestrel1 on 2007-12-31
Mine does this on occasion. It also does the same in windoze. I have found that if I get a sound playing & move the volume control, the sound comes back on the system. What sound card do you have or is it built in to the mobo like mine (SIS chipset)

---

### Post by Don1500 on 2007-12-31
I updated the original post to add more data. I have a Diamond LS 7.01 Card with C-media chipset [C-Media Electronics Inc CM8738]

Moving thigs doesn't help. Also it is flawless in windoze.

---

### Post by Don1500 on 2007-12-31
OKJ, this is driving me crazy... I did a complete shutdown, cold boot. Now I have sound again. I did Nothing else!
If this works fine, but I would like to know why.

Thanks anyway.

---

### Post by kestrel1 on 2008-01-01
One thing, have you still got the onboard sound enabled in the BIOS?

---

### Post by Don1500 on 2008-01-01
I forgot all about that. I checked and it was in AUTO. I turned it off and I still have sound, but let's see if I loose it again someday.  Thanks.

---

### Post by kestrel1 on 2008-01-01
Hopefully that was it.

---

