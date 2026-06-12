---
title: "DVD play back"
date: 2004-12-30
forum: Apple PPC Users
---

### Post by Castaa on 2004-12-30
I'm still battling to get DVD movies to play on my iBook (G3-600MHz, 256MB, 8 MB Rage 128.)
  
  **Has anyone gotten DVD movies to playback smoothly with a similar iBook running Linux?  If so what is your set up (software/hardware)?**
  
 The Xine player works the best of the players that I have tested but it still drops frames and the audio is out of sync with the video.
  
  DMA for the DVD-ROM is on.  I've tried at both 16 and 24-bit color depths.

---

### Post by khc on 2004-12-30
I remember having this problem with Debian using xine, but I don't have the problem now with Ubuntu using totem-xine. Which sound output are you using with xine?

---

### Post by Ufo on 2004-12-30
I have good experiences using Ogle to play DVD movies.
I don't have iBook, but I also had some trouble with Xine player.
With Ogle I have had no problems.
I must admit thought, that I have not watched that many DVD movies with computer.

---

### Post by Castaa on 2004-12-30
What hardware are you running?
  
 I have a bad feeling that Linux drivers do not support on the video card mpeg-2 decoder which then in turn requires a faster CPU than what I have to decode in software.
  
  I'm assuming this is why the iBook will play DVDs running the Mac OS 9 but not under Linux.  :(

---

### Post by Castaa on 2004-12-30
[QUOTE=khc]I remember having this problem with Debian using xine, but I don't have the problem now with Ubuntu using totem-xine. Which sound output are you using with xine?[/QUOTE] 
 OSS I think.  Emulated by the ALSA drivers.  I could be wrong about this.

---

### Post by Ufo on 2004-12-31
[QUOTE=Castaa]What hardware are you running?
  
 I have a bad feeling that Linux drivers do not support on the video card mpeg-2 decoder which then in turn requires a faster CPU than what I have to decode in software.
  
  I'm assuming this is why the iBook will play DVDs running the Mac OS 9 but not under Linux.  :([/QUOTE]


My hardware is

AMD Athlon XP 2400+ (1.93GHz)
Asus A7N8X-X
512Mt DDR
NVidia FX 5200 128Mt DDR AGP display card

Sad if your bad feeling is true.

---

### Post by chascon on 2005-01-07
on debian, I would instal okle and start it from term, the read the message in term when trying to read the DVD.  Follwo instructions and you're set.

I've gotton DVDs to play fairly well, a little choppy and a little tinny, on an old 400 mhz iMac G3.  Anything less than a G3 will be ugly.

So yes, this is possible (should be possible on the G3 you have).  Not sure about how to do this on ubuntu yet.  But certainly possible.

---

### Post by Momo on 2005-01-21
Hi everyone!  I too am trying to get some kinda of acceptable DVD playback on my iBook (specs are in my sig).

I'm still quite new to Linux and my only experience to now has been with Darwin in OS X, but I'm managing to make some small headway. I managed to get Freevo and mplayer to compile and run, but mplayer is proving to be a complete pain with DVD.  

By default it will compile with Direct Framebuffer as the preferred VO, but this simply doesn't work (fails to create video). I'm not sure if my card is even set up/detected/accelerated correctly yet as I don't know how best to check this out. Could be that the drivers are not working right?

By disabling fbdev, I got mplayer to compile with the regular x11/vidix output options. But vidix turned out to be horribly slow (I expected it to use the mpeg acceleration on the radeon card), and when I quit playback the screen is tinted yellow.

I've enabled UDMA2 on the combo drive (but haven't yet found out how to enable this at boot) and added -cache 8192 to the mplayer command line but playback is still unwatchable.

Ideally I'd like to use mplayer as it allows me to load external subtitles for DVDs which either have bad or no subs. Playback in Xine is bad too, and vlc won't even run.

Apart from the DVD playback, Ubuntu has made a good impression so far. Much better than when I first tried Linux a few years ago with Mandrake on my PC. But  I'm doing this for a better DVD experience (as the Apple one is awful), so I really hope to get this sorted :)

---

### Post by Viro on 2005-01-21
I don't think smooth DVD playback is possible at the moment with the iBook G3 series. I had an iBook G3 800 for some time. Nothing I ever did (recompile kernel, install Gentoo from stage 1 with all optimizations, enable DMA and video acceleration, etc) worked.

I think the reason is that the DVD player code isn't optimized for the PPC architecture, and if it is, it requires Altivec. Currently on my Powerbook, when I clock it down to 666 MHz, it still plays movies fine, and I'm quite certain it's because of Altivec.

In time as the code gets more optimized, we might be able to play DVDs on the iBook G3 line of notebooks. Until then...

---

### Post by Momo on 2005-01-21
If we were talking software rendering I'd agree, but the Radeon has hardware DVD decoding onboard (which is how playback is accelerated in OS9/X). 

Does this mean that the current kernel/driver in Ubuntu doesn't enable the acceleration by default? If so, can either be compiled to enable it?

---

### Post by Castaa on 2005-01-22
[QUOTE=Momo]If we were talking software rendering I'd agree, but the Radeon has hardware DVD decoding onboard (which is how playback is accelerated in OS9/X). 

Does this mean that the current kernel/driver in Ubuntu doesn't enable the acceleration by default? If so, can either be compiled to enable it?[/QUOTE]
 I believe that the OS 9/X ATI Rage drivers support the on card mpeg-2 decoding hardware.  This enables DVD to be played smoothly.  Since the Linux display drivers do not support  decoding hardware the mpeg-2 decoding is done in software.  This cannot be done at full frame rate on the G3 CPUs.

I do not know if all the above is fact but I believe it explains why it doesn't work.

Idea:
I wonder if I convert my DVD movies to Divx and stored the Divx video files on the hard drive it would play back smoothly using a Divx player?  Has anyone tried this?

---

### Post by Viro on 2005-01-22
[QUOTE=Castaa]I believe that the OS 9/X ATI Rage drivers support the on card mpeg-2 decoding hardware.  This enables DVD to be played smoothly.  Since the Linux display drivers do not support  decoding hardware the mpeg-2 decoding is done in software.  This cannot be done at full frame rate on the G3 CPUs.

I do not know if all the above is fact but I believe it explains why it doesn't work.

Idea:
I wonder if I convert my DVD movies to Divx and stored the Divx video files on the hard drive it would play back smoothly using a Divx player?  Has anyone tried this?[/QUOTE]
 The open sourced ATI drivers don't support hardware decoding. Converting to DivX will probably not help since DivX (MPEG-4) is more processor intensive than DVDs (MPEG-2).

Update:
Just spent some time playing around with xine. I've found that I'm using the Xv extension to display my videos. This provides hardware accelerated color space conversion and other stuff I'm not familiar with. When playing DVDs in Xine using Xv as the display method, I get about 25% CPU time used by Xine (read DVD, do sound, etc) and 35% CPU time used by X.org(just display each frame). Things play smoothly, and I've got no complaints.

Switching the display method to XShm which is what Ogle uses(and perhaps Totem but I'm not sure) my CPU usage shoots up to 40% for xine and 45% for Xorg. To top it off, while my CPU was throttled to half the max clock speed when using Xv, because of the jump in CPU usage the powernowd daemon bumped my CPU speed to the max 1.33 GHz. Guess what? Movies were still jerky with the occasional dropped frame.

Moral of the story, hardware acceleration may actually be supported under Linux. Show what I know :oops: . When playing your DVDs, try if possible to use the Xv method of displaying videos. Ogle doesn't support it, Mplayer does, VLC does, Xine does, Totem doesn't provide a way of selecting it. Dont know about other players, so there's still some hope of getting DVDs to play smoothly on the old iBooks :).

---

### Post by Castaa on 2005-01-22
[QUOTE=Viro]The open sourced ATI drivers don't support hardware decoding. Converting to DivX will probably not help since DivX (MPEG-4) is more processor intensive than DVDs (MPEG-2).
 
 Update:
 Just spent some time playing around with xine. I've found that I'm using the Xv extension to display my videos. This provides hardware accelerated color space conversion and other stuff I'm not familiar with. When playing DVDs in Xine using Xv as the display method, I get about 25% CPU time used by Xine (read DVD, do sound, etc) and 35% CPU time used by X.org(just display each frame). Things play smoothly, and I've got no complaints.
 
 Switching the display method to XShm which is what Ogle uses(and perhaps Totem but I'm not sure) my CPU usage shoots up to 40% for xine and 45% for Xorg. To top it off, while my CPU was throttled to half the max clock speed when using Xv, because of the jump in CPU usage the powernowd daemon bumped my CPU speed to the max 1.33 GHz. Guess what? Movies were still jerky with the occasional dropped frame.
 
 Moral of the story, hardware acceleration may actually be supported under Linux. Show what I know :oops: . When playing your DVDs, try if possible to use the Xv method of displaying videos. Ogle doesn't support it, Mplayer does, VLC does, Xine does, Totem doesn't provide a way of selecting it. Dont know about other players, so there's still some hope of getting DVDs to play smoothly on the old iBooks :).[/QUOTE]
  You got Xine to smoothly play back with what CPU and video chipset/card?
 
 I tried using the Xv display option with Xine but no improvement. I still drop the same about of frames.  'top' reports that the CPU utilization is around 95%.  70% going to xine.  25%  going to XFree86.

---

### Post by Momo on 2005-01-22
Xv doesn't work well here either. Of the various modes I managed to get working in mplayer, xvidix had the best performance, but audio sync was poor and the audio sounded like it was being played back at the wrong frequency.  And of course, xvidix also screws up the entire display necessitating a logout/reboot to fix.

I have seen Debian howto pages from guys with similar iBooks to mine posted a couple of years ago which claim to have DVD playback fine.  They mostly talk about using a certain XF86Config-4, the DRI thing and compiling a kernal from BenH in order to get everything working. Whether it truly is fully accelerated, I don't know yet.

UPDATE:

Had a look at the [Linux page](http://www.ati.com/support/faq/linux.html) on the ATI website:

> Some ATI hardware has DVD acceleration features. However, this functionality is NOT currently available in any Linux driver that we know of. ATI is investigating the possibility of providing these features in a future driver release.So there it is in black and white. No acceleration :(

---

### Post by Viro on 2005-01-22
A 1.33 GHz G4 clocked down to 666 MHz. I know it isn't in the same ball park as the G3, but I didn't think Altivec made *that* much of a difference since your G3 has 133 MHz advantage. I'm using an nVidia card, which isn't accelerated since nVidia didn't make the specs available to the OSS community.

The ATI drivers are only released for x86. It isn't really applicable since we're using PPC based machines and x86 drivers are kinda useless.

---

### Post by innodonni on 2005-05-02
```
grep -e "video.driver" ~/.gnome2/totem_config ~/.gxine/config
```

Doing something like this may give you lines with `video.driver:auto' - edit those files to say `video.driver: xv' to ensure players are using xv. They should do by default, but it's worth being sure.

I've found that DVDs gave dodgy playback (froze half-way), and I read [here](http://xinehq.de/index.php/faq#STATUS0X51) that you need multimode on by default, and my debian kernel package did not have this. Just goes to show what reading the documentation will do!

---

### Post by garcirog on 2006-09-22
I hate to say this but you could dual boot have a small MAC OS X, the reason is if you upgrade to tiger 10.4 and playing movie it works just fine I have never really had any problems. But their is a problem if you try to watch cartoon movies or anime movies you will get fram dropping but normal movies are just fine. I have a pismo g3 500mhz with 768MB of RAM and 8MB ATI video card, a lot lower then what you have on your G3, also my S-video output also plays movies just fine to the TV, I watched Harry Pottor on the big screen. But I can't run any other programings in the background or I will have problems watching movies.

As for ubuntu if  you want you could try the xubuntu's movie player which is xfmedia, I was able to get movies to play with that one but this is a slit frame frezzes like it's buffing, but it's less then a sec, but that's the best I can do on my system.

Hope this helps. :-)

---

### Post by cmorgan47 on 2006-10-24
i'm having the same issues, have tried the same solutions, with the same results, and came to the same conclusions....ie,DMA on drive, DRI enabled, still have choppy playback, ATI sucks for not putting out decent drivers for PPC.  

that said, i'm going to try using maconlinux tonight in full screen to see if it uses the mac drivers.  if so, i'll strip the mac install down to the DVD player.  long shot, but a slightly more elegant solution that dualbooting for DVD....which will be my next plan.

---

