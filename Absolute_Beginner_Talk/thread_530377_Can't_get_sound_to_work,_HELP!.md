---
title: "Can't get sound to work, HELP!"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by northerndude81 on 2007-08-20
So I just installed Ubuntu (7.04) and it won't give me any sound at all.  When I try to open Volume Control is gives the error message "No volume control GStreamer plugins and/or devices found."  I've been looking on these forums and all over Google, but cannot solve this.  I've re-installed three times now but that didn't solve anything.  I'm not sure what kind of soundcard I have if any.  I just got this computer from a guy who built it himself so I'm not sure what sort of parts are in it.  He told me it's reliable with good parts but at the very least it should have onboard sound right??  There are three plugs in the back of the computer for sound to go in/out/mic, so I know that it is capable of sound!!  Why won't Ubuntu work with this?  I don't want to put on a rock concert, just basic sound.  Please help me I switched to Linux to end the frustration of Windows but this is just as frustrating!!  Thanks.

---

### Post by mikeyphi on 2007-08-20
Look here first
[https://help.ubuntu.com/community/Sound?highlight=%28sound%29](https://help.ubuntu.com/community/Sound?highlight=%28sound%29)
Come back if you still have problems!!

---

### Post by Dr Small on 2007-08-20
Have you tried accessing the bios and seeing if your sound card is enabled?

---

### Post by raijinsetsu on 2007-08-20
open a terminal, run "lspci", and post the results. You should see a sound card listed. If there is one, run "lsmod" and post those results. It could just be that the driver isn't loaded for your card.

---

### Post by northerndude81 on 2007-08-20
Yes I read through that link but I couldn't find the answer there.  When I try "lspci -v" I don't see anything that looks like a sound card... so maybe there isn't one?  Or Ubuntu just cannot see it?

I tried going into the BIOS also but didn't see any options in there that looked like audio options.

What next??

---

### Post by raijinsetsu on 2007-08-20
If it's a laptop, list the make/model.
If it's a custom PC, list the motherboard and add-on soundcard, if any.
If it's a GateWay/Dell/Etc. PC, list the make/model

---

### Post by northerndude81 on 2007-08-20
Here are the lspci results.  Am I missing something?

pbr@pbr-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev 02)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:04.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:04.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:0d.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] (rev b2)
pbr@pbr-desktop:~$

---

### Post by northerndude81 on 2007-08-20
It's a custom PC but I don't know how to find out what kind of motherboard, sorry.  Is there a way I can look at it in Ubuntu (I mean without taking the case off and trying to read the physical label on the board)?

---

### Post by raijinsetsu on 2007-08-20
... Well, according to LSPCI, you don't have a sound device. Do you know if the sound is onboard? or is it an addon card? And has it ever worked in windows?

---

### Post by Dr Small on 2007-08-20
If the sound is onboard, then perhaps you missed it in the bios. I had the same problem with my brandnew motherboard, which had onboard sound, and ubuntu would not play any sounds. I had to go into the bios and find the onboard sound, and turn it from [auto] to the sound device and then everything worked.

Dr Small

---

### Post by northerndude81 on 2007-08-20
I think it's onboard sound and yes it worked in Windows before I installed Ubuntu.

---

### Post by northerndude81 on 2007-08-20
Is there any way you could give me some direction as to what to look for in the BIOS?  Like I said I tried that earlier and couldn't find any kind of audio options in there, but maybe I missed something.

---

### Post by Dr Small on 2007-08-20
Give me a couple minutes. I'll look on the bios of this computer. I may find something... It's on the other computer where I know where to look.

*I shall return...* - General Duglas McArthur

---

### Post by Dr Small on 2007-08-20
Here, I even took a picture of it, while I was in there.
Try looking around and see if you see something similar:

---

### Post by northerndude81 on 2007-08-20
Thanks I'll try that and see what I can do.  Will be back with results in a few minutes.

---

### Post by northerndude81 on 2007-08-20
Ugh... no there is no "ONBOARD AUDIO" option or any similar looking option in my BIOS.  At least not that I can see but I looked through every menu I could find.  What's wrong??

---

### Post by ajgreeny on 2007-08-20
> It's a custom PC but I don't know how to find out what kind of motherboard, sorry. Is there a way I can look at it in Ubuntu (I mean without taking the case off and trying to read the physical label on the board)?
In a terminal type:-
sudo lshw -html
which will give a long readout of all your hardware incl you mobo, all memory sticks, cpu, usb, sound and video, etc. etc. as an html file which can be read by your browser (firefox or whatever).

---

### Post by northerndude81 on 2007-08-20
OK I got:

 description: Motherboard
       product: <K7V-T>
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: REV 1.xx
       serial: xxxxxxxxxxx
       slot: USB1

How does that help me?

---

### Post by raijinsetsu on 2007-08-20
[This]("http://www.motherboards.org/files/manuals/1/k7vt-101.pdf") is the manual for your mobo. It has some jumper settings you should look at (page 19).

---

### Post by Dr Small on 2007-08-20
The jumpers are usually only used for frontpanel audio ports, let me remind you. If he is plugging the audio in directly in the back, then he is plugging directly into the motherboard, so the jumpers would be ilrelivant.

Dr Small

---

### Post by raijinsetsu on 2007-08-20
... This is a very old mobo. These jumpers are for enabling or disabling the audio codec. This comes right from the manual for the mobo.

---

### Post by northerndude81 on 2007-08-20
Ok I looked at the jumper section you recommended but... Jesus Christ, I am not an engineer.  I have no idea what any of that means.  What happened to "it just works"????  Maybe I'll just junk this whole thing and go buy a Mac.

---

### Post by Dr Small on 2007-08-20
I'm no engineer, but I built my own computer and got Ubuntu installed and had audio work... Sometimes I think it takes patients, what most of us around here ain't got.
I wouldn't buy a MAC, when you are so close with Ubuntu....

Dr Small

---

### Post by raijinsetsu on 2007-08-20
Make sure the jumpers for audio are set to pins 1 and 2, and not pins 2 and 3. You'll see it clearly labeled on the board. Otherwise, if you want sound, you'll need either a sound card, or a new mobo w/ a snd-card.

---

### Post by Nikron on 2007-08-20
You guys made sure he was in the audio group, right?  Try playing something as root.

---

### Post by raijinsetsu on 2007-08-20
LOL. That would be nice if it were the issue. I just assumed he was in the audio group... heh

---

### Post by northerndude81 on 2007-08-20
OK, how about if I just buy a cheap used sound card for $10 and pop that in, do you guys think that will solve my problem?

(And yes, I am in the audio group...)

---

### Post by raijinsetsu on 2007-08-20
Most cards are supported. so, it should solve your problem...

---

