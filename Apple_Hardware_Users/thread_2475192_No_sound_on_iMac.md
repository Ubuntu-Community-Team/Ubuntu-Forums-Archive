---
title: "No sound on iMac"
date: 2022-05-19
forum: Apple Hardware Users
---

### Post by kanrei on 2022-05-19
I installed Zorin OS 16 Core on my iMac. But unfortunately I have no  sound. (It's my first time using any Linux. So I'm an absolute newbie in  it.)

 Here are the specification of my Mac.
 iMac (21.5-inch, Late 2015), iMac 16,1
Processor: 1.6 GHz Dual-Core Intel Core i5
RAM: 8 GB 1867 MHz DDR3
Graphic Card: Intel HD Graphics 6000 1536 MB

 When I let inxi -SMA run, the following information is shown:
System:
Host: kanrei-iMac Kernel: 5.13.0-41-generic x86_64 bits: 64
Desktop: Gnome 3.38.4 Distro: Zorin OS 16.1
Machine:
Type: Laptop System: Apple product: iMac16,1 v: 1.0
serial: <superuser/root required>
Mobo: Apple model: Mac-A369DDC4E67F1C45 v: iMac16,1
serial: <superuser/root required> UEFI: Apple v: 428.60.3.0.0
date: 10/27/2021
Audio:
Device-1: Intel Broadwell-U Audio driver: snd_hda_intel
Device-2: Intel Wildcat Point-LP High Definition Audio
driver: snd_hda_intel
Sound Server: ALSA v: k5.13.0-41-generic

 I tried the following things, but nothing made a difference:


     sudo alsa force-reload



sudo apt-get install --reinstall alsa-base pulseaudio

sudo alsa force-reload



Using PulseAudio. I don't see anything here which would change anything.
[IMG]https://forum.zorin.com/uploads/default/original/2X/7/7c6f5668c3174de120b5f5e65e0905a0d8fb0396.png[/IMG]
[IMG]https://forum.zorin.com/uploads/default/original/2X/7/7bf4e49bb327733028276339094109567c7744c6.png[/IMG]



Using Alsamixer. I don't think it's anything wrong here. In the  screenshots you can see, how it looked like when I started it and when I  pressed F6 to select a sound card, how it looked there.
[IMG]https://forum.zorin.com/uploads/default/original/2X/7/78f751ef68c9c6e1a1765e04e9a8ddd2762a191a.png[/IMG]

[IMG]https://forum.zorin.com/uploads/default/original/2X/5/5abf25b56ab31c3d50836020c0158a1367b04202.png[/IMG]



sudo gedit /etc/modprobe.d/modprobe.conf
options snd_hda_intel model=mb5
(In general I get an error when using the gedit command, but it seems they saved the file either way.)



Trying out all profiles which I see in sound and pulse audio. 
[IMG]https://forum.zorin.com/uploads/default/optimized/2X/d/dd51552ca043fbdba86055656f9433357dee1f8c_2_999x750.jpeg[/IMG]
[IMG]https://forum.zorin.com/uploads/default/optimized/2X/a/aa0a367ccd8b72f0f122e8dcd41833a7dbfffe81_2_999x750.jpeg[/IMG]



sudo nano /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=imac27
sudo reboot
(I tried out with imac24 too. And also some other endings which I saw online.)



systemctl --user restart pulseaudio
rm -r ~/.config/pulse
pulseaudio -k




sudo gedit /usr/share/pulseaudio/alsa-mixer/paths/analog-output-speaker.conf
Change:
[Element Headphone] 
switch = off 
volume = off
to:
[Element Headphone] 
switch = off 
volume = merge 
override-map.1 = all 
override-map.2 = all-left,all-right

Change:

[Element Speaker]
required-any = any
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

To:
[Element Speaker]
required-any = any
switch = mute
volume = off

Save and reboot.




   I have no problem with having sound in the MacOS. (I have Dual Boot)
 Has anyone an idea what else I could try to get that problem fixed?

---

### Post by smm379 on 2022-07-30
Same problem here on my 2015 iMac. Has been a problem for years and I haven't found a solution that works yet.

---

### Post by arcusm on 2023-02-10
I was having the same problem on my iMac. I stumbled upon this possible solution. Says it's for Macbook Pro but it seems a lot of Macs use the same (or similar) Cirrus chipset for sound. I followed the instructions on my iMac and it worked perfectly. Sound card recognized and I get sound from the interanl speakers. 

[https://github.com/davidjo/snd_hda_macbookpro](https://github.com/davidjo/snd_hda_macbookpro)

---

