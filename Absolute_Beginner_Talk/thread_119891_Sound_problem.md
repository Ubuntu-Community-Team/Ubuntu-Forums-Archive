---
title: "Sound problem"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by utab on 2006-01-20
Hi

there was a similar thread before but my question is different.

when I lspci 

0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Po rt (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 1 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB 2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH 6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 03 )
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Contro ller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 546 0
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit  Ethernet PCI Express (rev 01)
0000:03:01.0 CardBus bridge: Texas Instruments: Unknown device 8036
0000:03:01.5 Communication controller: Texas Instruments: Unknown device 8038
0000:03:03.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)


So I think I have a sound card installed. But when I try to play some CDs in the combo box using CD Player under Applications > Sound and Video > CD Player I dont hear anything.

Any comments?

---

### Post by christhemonkey on 2006-01-20
Playing CDs in the disc drive you mean?
If so, i wouldn't have thought that it would be listed on lspci.
But dont quote me on that:p

Stupid question but is the CD in the drive?

---

### Post by christhemonkey on 2006-01-20
Sorry, just got what you meant.
Check in the gnome-mixer dialog, that it is turned up to a suitable level.

---

### Post by utab on 2006-01-20
thx

the cd is in the drive.

So I would like to mean that (I think) I have a working sound card(not working but installed :)) )

So??

---

### Post by utab on 2006-01-20
where is it ?

---

### Post by christhemonkey on 2006-01-20
Check to see if the module is loaded:
sudo lsmod | grep snd_intel

If not, try loading the module for this card:
sudo modprobe snd_intel8x0

---

### Post by utab on 2006-01-20
The output of sudo ....

snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm

your advice

---

### Post by christhemonkey on 2006-01-20
Seems that this should be working,
try running:
alsamixer
And turning everything up.
Also try:
[http://www.ubuntuguide.org/#configuresoundproperly]("http://www.ubuntuguide.org/#configuresoundproperly")

---

### Post by utab on 2006-01-20
thx for the help 

I will check all of them tonight if could not solve I will start another thread unfortunately.

regards goes as well

---

### Post by utab on 2006-01-20
I did not try the link

[http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)

but it is OK now.

thanks again.

---

### Post by christhemonkey on 2006-01-20
OK.
But why start a new thread?
Just as likely to get noticed with a new post than a new thread, IMO.

---

