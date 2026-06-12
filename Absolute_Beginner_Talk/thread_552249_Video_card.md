---
title: "Video card"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by Trzone on 2007-09-16
I'm not sure if my video card works, google earth doesnt seem to detect one.
here's my lspci output


00:00.0 Host bridge: VIA Technologies, Inc. VT8361 [KLE133] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1d)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1d)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0d.0 Communication controller: Agere Systems LT WinModem (rev 02)
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1 (rev 6a)

any help would be great

---

### Post by overdrank on 2007-09-16
> **Trzone said:**
> I'm not sure if my video card works, google earth doesnt seem to detect one.
here's my lspci output


00:00.0 Host bridge: VIA Technologies, Inc. VT8361 [KLE133] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1d)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1d)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0d.0 Communication controller: Agere Systems LT WinModem (rev 02)
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
[COLOR="Red"]01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1[/COLOR] (rev 6a)

any help would be great

HI I have highlighted your video card and a quick search returned this thread
[http://ubuntuforums.org/showthread.php?t=502391&highlight=Trident+Microsystems+CyberBlade](http://ubuntuforums.org/showthread.php?t=502391&highlight=Trident+Microsystems+CyberBlade)
You may search further good luck!

---

### Post by Trzone on 2007-09-16
According to that post, my video card is really too old.. but in windows i can play some graphic games, in BIOS i can set the video memory up to 8mb and it's at 8 now.  Windows must do something different?  Hmm..

---

### Post by overdrank on 2007-09-16
> **Trzone said:**
> According to that post, my video card is really too old.. but in windows i can play some graphic games, in BIOS i can set the video memory up to 8mb and it's at 8 now.  Windows must do something different?  Hmm..

I agree, I have had some video cards that would run some 3d effects in windows but not in linux. I tend to believe it is to the availability of the drivers in linux. :(

---

### Post by Trzone on 2007-09-16
Linux rather, ubuntu has become a hobby for me :lolflag: 

i think opengl is available on my "video card" but i know that direct x is basically a windows kind of thing.  it's a 5 year old computer *shrugs* it does what needs to be done.

---

