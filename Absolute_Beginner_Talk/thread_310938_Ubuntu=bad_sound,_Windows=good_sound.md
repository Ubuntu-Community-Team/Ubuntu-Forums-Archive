---
title: "Ubuntu=bad sound, Windows=good sound"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by getut on 2006-12-02
Please help... I have just built a new PC using an ASUS P5L-MX mobo with integrated SoundMax AD1986A chipset.

I am dual booting and the sound is perfect in Windows XP, but in Ubuntu every time there is a sound, there is a VERY high pitched squeeling in the background. The correct sound can plainly be heard, but the squeeling is awful. I've checked to see that the microphone was muted and it was. I don't know where to go from here.

---

### Post by riven0 on 2006-12-02
> **getut said:**
> Please help... I have just built a new PC using an ASUS P5L-MX mobo with integrated SoundMax AD1986A chipset.

I am dual booting and the sound is perfect in Windows XP, but in Ubuntu every time there is a sound, there is a VERY high pitched squeeling in the background. The correct sound can plainly be heard, but the squeeling is awful. I've checked to see that the microphone was muted and it was. I don't know where to go from here.

Hmmm, never had problems with the sound, but I have c-media ac'97. If you're in Gnome, go to the multimedia systems selector. It should be on autodetect. Try out both Alsa and OSS and see what happens.

---

### Post by agonoruci on 2006-12-02
Got the exact problem, tryin Alsa and OSS right now.

---

### Post by agonoruci on 2006-12-02
Yep It Worked, Niice. I LOVE U riven0 lol.

---

### Post by getut on 2006-12-03
Riven, unless I did it in the wrong place, it didn't change anything for me.

In Edgy, I went into System-->Preferences-->Sound and on the Devices tab, it was set for Autodetect as the playback device Sound Events, Music and Movies, and Audio conferencing. I first changed all of those to ALSA and rebooted with no change in squeeling and normal sound also still played, then I did the same for OSS and still have the squeeling on top of the normal sound.

The options available to me are Autodetect, AD198x Digital, AD198x Analog, ALSA, ESD, and OSS.

The funny thing is, I don't remember this squeeling when I booted off the CD. I'm going to boot off of it again and report back here.

---

### Post by getut on 2006-12-03
Nope.. just booted on the CD. Same squeeling. Just to double check, I booted into Windows XP again, and the sound was fine so it shouldn't be a hardware issue. Man I hope I can get this fixed. This was the first PC that I was finally going to dedicate 100% to linux (the XP dual boot is a barebones install exclusively for gaming so far, no office or anything else to reduce my urge/need to boot to it).

---

### Post by adamkane on 2006-12-03
A lot of GStreamer based apps don't work yet.

Use xine based sound applications like gxine, until GStreamer comes out with a functional product.

---

### Post by getut on 2006-12-03
> **adamkane said:**
> A lot of GStreamer based apps don't work yet.

Use xine based sound applications like gxine, until GStreamer comes out with a functional product.

I'm completely lost with what you said. As far as I am aware, I don't have any choice. Every sound, even the logon sounds have the squealing. Its not limited to one application. Watching Divx movies in mplayer or vlc sounds the same (bad).

I've done some more digging with google and it seems there is a bug dealing with this chipset. I didn't catch it at first, but just like is reported for other linux flavors, the squealing comes from only the left channel. One of the Fedora Core forums said a workaround is to disable 5.1 surround sound and go with only 4 speaker sound, but I see no way to do it in Ubuntu (I can't find any control applet to handle it). They may be talking about some kernel patch to do it, which if that is the only fix, I'd rather just pay an additional $60-$80 for an add in sound board.

---

### Post by getut on 2006-12-05
Bringing this one back for one more question. I've been beating on it off and on for two days since my last post and still don't have it resolved. I'm still getting either no sound or squealing from the left channel just like other problems reported from ALSA from other linux distributions when searching with google.

I have seen evidence that there may be fixes for this bug in the latest releases of ALSA. How can I discover which version of ALSA is included in my Ubuntu Edgy? If it is not already at the required level, how would I go about upgrading ALSA to the 1.0.13 that is most current without waiting for Ubuntu to upgrade the package?

---

### Post by getut on 2006-12-05
Ok... more info.

Edgy runs ALSA 1.0.11 and the fix for this sound chipset (AD1986A) is NOT in 1.0.11.

According to the ALSA bug tracker, choose anonymous login for view only access at [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1596](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1596)

The fix went in CVS sometime around late March 2006 which means that it probably JUST missed being release in the final version 1.0.11.

I am reluctant to attempt to upgrade 1.0.13 based on two factors... 1) my newbness and 2) based on postings from users in that problems thread, it seems to be a bear.

I can't find any walkthroughs on fresh installs or upgrades of ALSA... can anyone help here?

---

### Post by getut on 2006-12-06
I guess I was making so much progress on this one by myself that I kept away all my potential help.. but I'm stuck at the ALSA upgrade.

Does anyone know how to help me upgrade ALSA? If not... at the very least does anyone know when the Ubuntu repositories are likely to have a upgraded package ready?:-k

---

### Post by wpshooter on 2006-12-06
> **getut said:**
> I guess I was making so much progress on this one by myself that I kept away all my potential help.. but I'm stuck at the ALSA upgrade.

Does anyone know how to help me upgrade ALSA? If not... at the very least does anyone know when the Ubuntu repositories are likely to have a upgraded package ready?:-k

Dear getut:

I have found the same thing to be true on my systems that you have.  When I was running M/S windows on them the sound was great but now that I have switched to Ubuntu, the sound on my systems leave a bit to be desired.  

My guess is that this is an area of this O/S that no one (programmer or developer) has any great desire to work on.  And, IMO, this is not the only area.  I don't really understand the priorities of the developers on this O/S when they are going about fixing minor things that many users would never have occasion to use and then let things like poor GUI tools, poor application installation tools, general inability to network/share folders/files and printers without having to reinvent the wheel go basically untouched !!!

---

### Post by bsalt on 2006-12-11
> **agonoruci said:**
> Yep It Worked, Niice. I LOVE U riven0 lol.

Hey, just to let you know, I have a Creative Soundblaster Audigy 1 which is old school, and I absolutely am in love with it. I also have 2.1 Boston Acoustics digital speakers, but still, the card itself is SOO nice and a very inexpensive option if you want good sound in *any* operating system (preferrably Ubuntu)

Peace

---

### Post by getut on 2006-12-11
I FINALLY got this one resolved and was able to do it with stock Ubuntu Edgy versions of ALSA.

If you have a board with integrated Analog Devices or SoundMax 1986A (AD1986A) and you have the shrill whistling or screech coming from the speakers and then no sound at all if you try to adjust any of the settings such as speaker volume etc, this fix should do it for you.

1) Switch to one of the consoles and sign in:
CTRL-ALT-F2

2) Stop GDM so that sound hardware will not be in use:
```
sudo /etc/init.d/gdm stop
```

3) Remove the hda_intel sound module
```
rmmod snd_hda_intel
```

4) Reinsert the same sound module but this time with switches that works around the issue:
```
sudo modprobe snd_hda_intel model=laptop
```

5) Restart GDM and you should now have normal sound:
```
sudo /etc/init.d/gdm start
```

Note: I am NOT using a laptop. It is just enabling this switch seems to disable the piece of the driver that is messing up in ALSA.

---

### Post by getut on 2006-12-11
Ahh.. thought my above had it 100% licked, but I am finding I have to do my fix above after every boot.

Does anyone know how to apply my fix above after every boot?

---

### Post by HereInOz on 2006-12-11
> **getut said:**
> Please help... I have just built a new PC using an ASUS P5L-MX mobo with integrated SoundMax AD1986A chipset.

I am dual booting and the sound is perfect in Windows XP, but in Ubuntu every time there is a sound, there is a VERY high pitched squeeling in the background. The correct sound can plainly be heard, but the squeeling is awful. I've checked to see that the microphone was muted and it was. I don't know where to go from here.

Perhaps you can tell others what the problem was, and how you solved it.

---

### Post by getut on 2006-12-11
> **HereInOz said:**
> Perhaps you can tell others what the problem was, and how you solved it.

This whole thread is a documentation, more like a running diary, of the problem that I ran into, the steps I took to resolve it, and 2 posts above yours is the exact fix to it.

I just need help with the one last issue of how to make the fix stick between reboots.

I'm sorry but I really don't know how to document any better than I already have.

---

### Post by ardvark71 on 2006-12-11
> **getut said:**
> Ok... more info.

Edgy runs ALSA 1.0.11 and the fix for this sound chipset (AD1986A) is NOT in 1.0.11.

According to the ALSA bug tracker, choose anonymous login for view only access at [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1596](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1596)

The fix went in CVS sometime around late March 2006 which means that it probably JUST missed being release in the final version 1.0.11.

I am reluctant to attempt to upgrade 1.0.13 based on two factors... 1) my newbness and 2) based on postings from users in that problems thread, it seems to be a bear.

I can't find any walkthroughs on fresh installs or upgrades of ALSA... can anyone help here?

There aren't any upgrades to ALSA in Synaptic?

Best Regards...

:KS

---

### Post by getut on 2006-12-11
> **ardvark71 said:**
> There aren't any upgrades to ALSA in Synaptic?
:KS

Not that shows up here. Edgy runs 1.0.11Ubuntu5 and that is the latest showing up in synaptic.

I posted a working fix above but it has to be re-done each reboot.

---

### Post by ardvark71 on 2006-12-12
> **getut said:**
> Not that shows up here. Edgy runs 1.0.11Ubuntu5 and that is the latest showing up in synaptic.

I posted a working fix above but it has to be re-done each reboot.

I read that and short of installing 1.0.13 from source or installing a regular sound card (preferably something from Sound Blaster) and disabling the onboard chip, I'm not sure what else you can do unless someone here knows more how to tweak settings and code.

Best Regards...

:KS

---

### Post by bruceathome on 2006-12-13
You might want to try this:


Add "options snd-hda-intel position_fix=1 model=3stack" to "/etc/modprobe.d/alsa-base"

Sound worked fine for me after restart.

Found it on [this]("http://www.planetamd64.com/lofiversion/index.php/t23938.html") page, about half way down, a post by chumba.


Good luck.

---

### Post by Smerity on 2007-03-15
I love you guys ! ^_^

The high pitched shrill was killing me, but having done exactly what **bruceathome** suggested it now works perfectly!

So yes, to others I'd suggest you give that a try.

Once again thanks guys!
*Smerity*

---

### Post by bourger on 2007-03-21
Well, I have the title problem, but not that which was discussed here.
Motherboard MSI MS6712, onboard sound VIA 8235.
lspci -v
```
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7120
        Flags: medium devsel, IRQ 201
        I/O ports at d400 [size=256]
        Capabilities: <available only to root>
```

The sound quality is just awful, when I play an audio CD it sounds like 16bit mp3. But there is no noise or squeling - simply low quality. The same issue was under Mandriva 2007 (changes of ALSA/OSS etc. didn't help).
In System-->Preferences-->Sound there is no other option but switching ESD on-off (no Devices tab).
In Windows, everything is OK.

---

### Post by danishbuddha on 2007-10-03
then i try edit the base, it says that i don't have the rights to do it.. still new to Ubuntu..

---

### Post by bourger on 2007-10-03
**danishbuddha**
You mean this base - 
/etc/modprobe.d/alsa-base ?
Most likely you should edit it as a root, i. e. before the command ```
gedit
``` you should type ```
sudo
```. So, the whole line will be ```
sudo gedit /etc/modprobe.d/alsa-base
```
And be careful when changing anything as a root (sudo) :).

---

### Post by danishbuddha on 2007-10-03
i could edit the file, but it did not remove the noise :(

---

### Post by danishbuddha on 2007-10-15
finally got it to work.. don't know why but it didn't work with ubuntu ultimate 1.5.

---

### Post by mithbuntu on 2007-10-15
Just wanted to add that I had hissing sounds after installing and playing music with amarok.  Using the above code fixed my problem right up!  I don't know how you guys can figure some of this stuff out but thanks ;]

---

### Post by mithbuntu on 2007-10-16
Ugh.  I am now hearing the hiss again after playing music in amarok AND the code that fixed it last time is still present in /etc/modprobed

Any other brilliant ideas?

---

### Post by ekstee on 2007-12-13
i'm also having the same problem.

---

### Post by briang on 2007-12-13
I have the same problem, I am running feisty on amd 64 4000 with asus avv8 mother w/ integrated sound, and I have that horribly annoying squeal....I hate it! please make it go away!!! I saw that there is a new distro of Ubuntu..... maybe they fixed it?????

---

### Post by Dharzen on 2008-05-03
I am also having some trouble here...

I have no screeching or annoying sound whatsoever, but the sound quality is quite bad. My music sounds distorted, particularly the low pitched sounds (or the bass) and, overall, my mp3s sound like 64kbps files. In Windows, however, I had no problems at all, and the sound was pretty clear....

Is there any solution for this??? I have an integrated Intel sound card and driver (82801AA AC 97, i think), and I am using Ubuntu Gutsy..... Please help!

---

### Post by Dharzen on 2008-05-03
Forget it, I've just found what was wrong. The PCM volume in the ALSA mixer was way too high, and this caused the distortion. My music now sounds fine. Thanks anyway....

---

### Post by nrwilk on 2008-05-09
> **Dharzen said:**
> Forget it, I've just found what was wrong. The PCM volume in the ALSA mixer was way too high, and this caused the distortion. My music now sounds fine. Thanks anyway....

Thank you, for some reason, I just started having this problem with distorted sound all of a sudden, and this fixed it.

It sounded like the high-pass crossover had been removed from my mids and tweets.

---

### Post by chrisdugdale on 2008-05-09
Thanks for the suggestions. I had no sound at all. Turns out I could use autodetect but needed to set sound capture to ALSA and the device to USBox46d.oxada(alsa mixer). I guess it was because my desktop speakers are USB powered. I got the hint where to look System>Preferences>Sound from here, then rebooted from my other working disk setup and just put in those settings.

---

### Post by uhappo on 2008-06-22
Disable software sound mixing (ESD) from preferences!!!

Before this I had terrible sound, sort of highpass filtered and overly boosted on highs. Now I'm good! Ugh!

---

