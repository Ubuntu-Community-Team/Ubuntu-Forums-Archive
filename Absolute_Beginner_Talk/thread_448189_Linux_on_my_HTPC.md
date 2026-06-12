---
title: "Linux on my HTPC"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Dark Damo on 2007-05-18
Okay guys i have to ask a few questions about switching my HTPC over to Linux from Windows:

1. Does Creative have X-Fi drivers out for linux yet?
2. Does Ubuntu have RAID drivers for my ASUS A8S-X motherboard in installation?
3. Do the linux NVIDIA drivers support hardware acceleration of video?
4. Would it be easy for me to install MythTV on Ubuntu?
5. Does Ubuntu support my DVICO FusionHDTV DVB-T Plus TV tuner?
6. Does Ubuntu automatically enable DMA on your hard drives once done installing?

I have some more to ask later, thanks in advance ;)

---

### Post by reacocard on 2007-05-18
> **Dark Damo said:**
> Okay guys i have to ask a few questions about switching my HTPC over to Linux from Windows:

1. Does Creative have X-Fi drivers out for linux yet?
2. Does Ubuntu have RAID drivers for my ASUS A8S-X motherboard in installation?
3. Do the linux NVIDIA drivers support hardware acceleration of video?
4. Would it be easy for me to install MythTV on Ubuntu?
5. Does Ubuntu support my DVICO FusionHDTV DVB-T Plus TV tuner?
6. Does Ubuntu automatically enable DMA on your hard drives once done installing?

I have some more to ask later, thanks in advance ;)

1, 2 & 5) No idea. Google is your best friend here.

3) Yes, if you install the proprietary drivers (very easy on feisty).
4) Reasonably so. There are packages in the repositories, so it's just a matter of getting it set up after it's installed.
6) If the drives support it.

---

### Post by Dark Damo on 2007-05-18
Found drivers for my card here:

[http://www.fusionhdtv.co.kr/ENG/Support/FAQBeforeBuy.aspx?act=RD&id=26&pg=0&CATID=8&SCATID=37](http://www.fusionhdtv.co.kr/ENG/Support/FAQBeforeBuy.aspx?act=RD&id=26&pg=0&CATID=8&SCATID=37)

Still cant find anything on RAID though, not too sure about Creative as i haven't searched.

Anyone else here used MythTV who can comment on it?

---

### Post by newlinux on 2007-05-18
1. Don't think so - [http://ubuntuforums.org/showthread.php?t=440866](http://ubuntuforums.org/showthread.php?t=440866)
2. Think so. I know a linux raid driver for AS8-X exits
5. If it is like the Regular DVICO FusionHDTV DVB-T or DVB-T Lite, yes. You would probably just need to load the cx88-dvb module.

---

### Post by TriggerHappyChewie on 2007-05-18
It is very easy to install MythTV on Ubuntu.  Take a look: [https://wiki.ubuntu.com/MythTV](https://wiki.ubuntu.com/MythTV)

---

### Post by Dark Damo on 2007-05-19
> 5. If it is like the Regular DVICO FusionHDTV DVB-T or DVB-T Lite, yes. You would probably just need to load the cx88-dvb module.

Its a DVICO FusionHDTV DVB-T Plus

Does the A8S-X RAID driver automatically run when installing ubuntu, so it sees one 500GB drive rather than 2x250?

---

### Post by Dark Damo on 2007-05-19
Sorry to bump but i noticed [**_THIS_**](https://help.ubuntu.com/community/MythTV_Feisty_Frontend). That is what i would like. That makes it so its just the MythTV application yes?

So if i turn it on when its all installed it auto loads MythTV? That would be soooo handy and even easier for my dad to use than windows!

---

### Post by newlinux on 2007-05-19
Yes, I realized it is Dvico FusionHDTV DVB-T Plus, but I'm only sure about the lite and regular.  know what's different about the Plus, but if it uses the same chipset you're fine. Dvicos are generally well supported in newer linux kernels.

i don't know if hte RAID driver automatically runs.

Yes, you can have it so MythTV automatically loads, but that is a frontend only instruction you are looking at. Unless you have a backend somewhere else, you will still need to install a backend on that machine (but you can still have the frontend automatically log in and load up). So if you are using it only as a mythbox and not using as a regular desktop then you are probably interested in [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend)

---

### Post by Dark Damo on 2007-05-19
Yeah it'll be a MythTV only box because otherwise it will get way to complicated for Dad and then he'll refuse to use it. So the one i was looking at was wrong?

---

### Post by newlinux on 2007-05-19
The one you were looking at was frontend only. For myth to work you have to have a frontend (basically a viewer) and a backend (basically a server that sends the content to the viewer - the machine with the tuner card needs to be a backend). They don't have to be on the same machine, which is why there are instructions for a frontend only (and even a backend only). But if you don't already have a backend, you will probably want to make this machine a frontend/backend only machine. It won't look any different than a frontend only to your dad. Hope this makes sense. If not, feel free to ask more questions :).

---

### Post by Dark Damo on 2007-05-19
Yeah thats exactly what i want, will the frontend start up on bootup? Or will it go into a GUI and i'll have to select it from somewhere?

---

### Post by reacocard on 2007-05-19
> **Dark Damo said:**
> Yeah thats exactly what i want, will the frontend start up on bootup? Or will it go into a GUI and i'll have to select it from somewhere?

You can have it either way, I believe the posted guide does it automatically on boot.

---

### Post by newlinux on 2007-05-19
By default, the guide will wait about 5 seconds and then autologin and start up mythfrontend.

---

### Post by Dark Damo on 2007-05-20
Hmm, i asked dad what he wants and he said thats exactly what he wants. He'll be really happy if this works out smooth.

One problem will be with the creative sound card. We decided to switch over to the onboard but i have to be able to switch the mode to "6 channel" mode (5.1). Can i do that in ubuntu?

---

### Post by newlinux on 2007-05-20
Do you mean via spdif out (coax or optical) or have the card do the processing and connect it directly to the speakers? Which onboard card is it? Most creatives I've heard of are well supported.

---

### Post by Dark Damo on 2007-05-21
I got one of those X-Fi ones. So i have to use onboard sound until they release linux drivers :(

I'm using the analogue connections, but i have to be able to switch it to 5.1 mode in software settings for it to work.

---

### Post by reacocard on 2007-05-22
> **Dark Damo said:**
> I got one of those X-Fi ones. So i have to use onboard sound until they release linux drivers :(

I'm using the analogue connections, but i have to be able to switch it to 5.1 mode in software settings for it to work.

It should be recognized automatically, you'll just have to set the video player to use 5.1.

---

### Post by Dark Damo on 2007-05-23
Cool thanks for that.

Is there a linux version of AutoGK by any chance?

---

### Post by Dark Damo on 2007-05-23
Never mind made a new topic and it got answered to :)

But, do i need to be connected to the internet all the time to use MythTV? Or will it run without the EPG?

---

### Post by Dark Damo on 2007-05-25
Bump, sorry i need to find out about the EPG.

---

### Post by Dark Damo on 2007-05-26
I seem to have hit a snag following the wiki [here](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend).

I am up to backend configuration capture card. 

I set it to pcHDTV DTV capture card (w/v4l drivers)

video devices: /dev/video0
DVICO FusionHDTV DVB-T Plus [cx8800]
Signal timeout: 500
tuning timeout: 2000
Default input S-video (Only other is composite, no antenna)

Now video sources:

name: lol
XMLTV: Tramsmitted guide only
channel frequency table: Australia


Now when i go to scan for channels it keeps scanning ASTC or something and keeps timing out picking up 0 channels. I want it to scan DVB-T not ASTC. How can i change it to DVB?

---

### Post by Dark Damo on 2007-05-26
bump. please help.

---

### Post by Dark Damo on 2007-05-26
bump please help me.

---

### Post by newlinux on 2007-05-26
It should be setup as a DVB capture card (not pcHDTV or V4L), and then you may get an "analog options" button that should be set /dev/video0. 

Then you should be able to set the proper DVB-T scanning frequencies after you have defined and assigned and input to the dVB card, and you can define and set an analog input for /dev/video0 if the analog options was recognized.

I don't know much about scanning and setting up DVB-T, but hopefully this will put you on the right path.

perhaps:

[http://www.users.on.net/~jani/dvico-mythtv-11.html](http://www.users.on.net/~jani/dvico-mythtv-11.html)

or this

[http://www.mythtv.org/wiki/index.php/DViCO_FusionHDTV_DVB-T_Lite](http://www.mythtv.org/wiki/index.php/DViCO_FusionHDTV_DVB-T_Lite)

will help. Not exactly your card, and I think they may be for older versions of myth but I'm pretty sure at least the initial setup is the same (defining the capture card).

---

