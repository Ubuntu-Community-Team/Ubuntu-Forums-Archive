---
title: "Please check my config  *new user here*"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by pentax on 2007-05-17
Hi, this is my first post here, I'd really appreciate if some of you gurus could look over my setup and tell me if this looks OK for a problem free Ubuntu setup.
I have a lot of questions, first off let me tell you that I am not exactly new to linux, I used to use SuSe linux about 6 years ago, and installed SuSE on several boxes, although my Linux knowledge has severally faded since then.
My main interest is photography, I currently use CS2 to convert Pentax K10D RAW files, I would [COLOR="Red"]absolutely[/COLOR] love to dump CS2, and[COLOR="Red"] mostly w[/COLOR]ould LOVE to delete the  worm, spyware, and  virus infested XP.
As far as I can tell there are several capable RAW conversion programs that should work fine on Ubuntu, I'm more worried about the Video setup here are the specs for my system.
Athlon 64 X2 3800
2 gigs DDR2 800 ram
Lite-On 20X lightscribe DVDR-CD SATA
WD 200 gig 3mb SATA
GIGABYTE GA-MA69VM-S2 motherboard W/ATI Radeon Xpress 1200  onboard video
19" ViewSonic 1440 x 900 WXGA+
My main concerns is getting the video to work in the full 1440 x 900 resolution with the onboard ATI card, I don't play games so 3D acceleration is not a big deal - but I need decent resolution.
I don't have a lot of peripherals, I'm a photographer,  but I upload my prints to Costco.
Also as a big bonus I do need to connect via Remote Desktop to a Windows 2000 server, is ths possible using Ubuntu?
If anyone can answer my questions I will be very gratefull:)

---

### Post by mahy on 2007-05-17
I'm using ATI with the proprietary flgrx driver and it works great. The rest is ok, imho. Never tried the remote connection, though, only SSH! :D

---

### Post by hyper_ch on 2007-05-17
Actually Photoshop CS2 runs on Ubuntu with wine :) so you don't need to dump it... although I think it has a few bugs but I'm not 100% sure...

Well, the main thing that will give you a headache is the ATI card... ATI in gerneral isn't that good supported... you will have to search the forums for it.... or use the Ubunto Table of Hardware... just google for "ubuntu hardware" and you'll get some result that points you to the right site.

Another thing that often gives a headache is a wifi card... you use wifi or ethernet?

If you install a vnc service on the windows 2000 server you can connect to it without problems.... e.g. [www.realvnc.com](www.realvnc.com) (free version is not encrypted)... then you get a vncviewer for linux and that's it :)

Regarding the resolution: If you can get the ati card working fine, then you'll also have no problems getting the right resolution (I think).

With that setup you could even run Windows XP or Windows 2000 in virtualbox or vmware and run Photoshop in there without too much performance degradation... just another thought :)

---

### Post by hyperair on 2007-05-17
Hey remote desktop works in Ubuntu out of the box using the Terminal Server Client!

As for Adobe Photoshop CS2, the installer won't run on my Wine. However, the portable Photoshop CS2 works.. with a couple of bugs. Rather unresponsive though.

My setup is a 2.67 GHz P4, with 1278 MB DDR RAM and VirtualBox runs without a hitch, so fast that it feels almost native.

---

### Post by hyper_ch on 2007-05-17
I had CS2 runnin in Dapper... so I assume it runs also in feisty...

---

### Post by pentax on 2007-05-17
thanks for the replies so far. A few more questions.
Should I install the 64 bit or 32bit version? I've been reading a lot of threads on this and my head is swimming - my geek side says yes, absolutely install the 64bit version, but my practical over-worked side of my doesn't want to spend hours getting something simple to work.
My main interest is photography, I'm mainly interest in giving LightZone and digiKam a try, any know problems running these with 64 bit Ubuntu?
Thanks so much - great forum!

---

### Post by nickpaton on 2007-05-17
Hi Pentax and welcome to the forums and Ubuntu.

Agree about what the geek side says, but ignore it and use 32bit!

---

### Post by swatF1RESTORM on 2007-05-17
I did listen to my geek side and installed the 64bit version. Just about everything worked off of a fresh install (I installed Feisty) and I went to YouTube and wasn't able to watch movies. I did a little research and found that adobe didn't have support for 64bit systems yet so there was no flash player. From there I began downloading the i386 ISO for Feisty. I think I've come across a few work arounds to deal with Flash support on 64bit systems but I already uninstalled and moved to the 32bit version.

Just wanted to share my experiences. Hope it helps.

swatF1RESTORM

---

### Post by smooth_b on 2007-05-17
If you are going to use a remote desktop connection through SSH I would use NXSERVER. You can check it out at [http://www.nomachine.com](http://www.nomachine.com)

 NX works much faster than VNC and Windows RDP.

---

