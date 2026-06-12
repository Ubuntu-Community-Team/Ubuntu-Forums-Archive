---
title: "I can't play streaming video. Please help!"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by Koech on 2006-05-25
I really like playing streaming video and I have been playing stuff from [aol music]("http://music.aol.com/videos/newthisweek.adp") on my XP box. With Ubuntu, I don't seem to get the trick, I have installed codecs from Restricted Formats [site]("https://wiki.ubuntu.com/RestrictedFormats") therefore I can play mp3. What is missing? I get a message thus: 

   We're sorry, this feature requires the Mozilla ActiveX Plugin. Click here to install.

Need you help.

Also my video player hangs alot, is there anything I need to do?

---

### Post by nalmeth on 2006-05-25
Use automatix to install the mplayer-mozilla plugin, have you done this?
Video problem's might be related to your video card/driver.
You can change the video driver your video player uses in it's settings.

What kind of video card do you have?

---

### Post by Koech on 2006-05-25
I think I've installed the Mozilla plugin you talked of. My video card is S3/VIA Unichrome Pro IGP, but my X settings are set to 'vesa', note that I can play other videos on my NTFS partition.

---

### Post by nanotube on 2006-05-25
hi
i checked out that aol site... and it's not just about mplayer. for some reason they require some kind of evil activex plugin for mozilla. and of course, the whole reason we have mozilla is to get away from the whole activex thing that they had in IE, that made the browser have more security holes than an old sieve... 
so, i suppose if you really want to, you could go and install that activex plugin...

---

### Post by Koech on 2006-05-25
Do you have an idea how to install the plugin? And for Linux?
Another question about my video driver, can i change my settings from vesa to the S3/VIA one?

---

### Post by nanotube on 2006-05-25
well, you could try running
sudo dpkg-reconfigure xserver-xorg
and go through the prompts, and select a different video driver...

might want to first make a backup of your /etc/X11/xorg.conf first, though, just in case that messes it up. :)

and as to activex... i don't know anything about that plugin, it might not even be available for linux at all. you have to look for it...

---

### Post by Koech on 2006-05-25
Thanks alot for your help. Let me try it out. Keep trying too and update me if you can.

---

### Post by nalmeth on 2006-05-25
yes, before you mess with a working configuration, backup the config file:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
Before you do that, you should try changing the video driver for your video player first, you may not need to change video-card driver.

ActiveX is windows business, doubt it's available to linux. You should contact AOL and ask politely why they choose to exclude linux user's from their media.

BTW, can you download the video in question directly?
You can look at the page source with cntl-U and find the address of the video, or use the Video Downloader Firefox Extenstion, though they might have worked around this ability.

---

### Post by Koech on 2006-05-25
It's good you brought up the issue, I have never installed the motherboard drivers while on Linux. How do you do that coz I figured out if I can see things I don't really need to, but now that I have problems with video I may need to. the CD is just there but it has Windows installers, do I use it or I have to get Linux based ones?
About the video, I don't think aol can just allow you to download their music that easily, I have not tried to though. Maybe someone has a way round it and it'll be great to know...
And yes I backed up the conf file. I'll try to talk to aol too.

---

### Post by Koech on 2006-05-25
Anyone knows how to install my video drivers from the vendor's CD? The one I have is made for Windows. Is there a way around it?

---

### Post by nanotube on 2006-05-25
you cannot install windows vid drivers on linux. have to get linux drivers.
but did you try dpkg-reconfigure? linux already comes with a lot of drivers built in, you should try it before going off and downloading drivers from somewhere else...

---

### Post by Koech on 2006-05-25
sorry, had a blackout, i can't be on ubuntu now. there is no option for my driver in dapper, in fact i remember i couldn't boot breezy coz of x server. i don't know whether via or s3g themselves make linux drivers.

---

### Post by nalmeth on 2006-05-25
I would have guessed no, but that's because I am ignorant.
A quick search led me to [this forum]("http://forums.viaarena.com/messageview.aspx?catid=28&threadid=71875&enterthread=y"), you might try to find some information there. 
Try to find out what the linux driver is called, it ought to be included with Ubuntu.
If not, you might find out how to get it working.

---

### Post by Koech on 2006-05-25
Actually I,ve posted a Qn there already. I got a HOWTO for Breezy users on [this link]("http://ubuntuforums.org/showthread.php?t=124604") that explained how to compile VIA drivers. I don't know how well it goes esp for Dapper. I'll look into it though.

---

