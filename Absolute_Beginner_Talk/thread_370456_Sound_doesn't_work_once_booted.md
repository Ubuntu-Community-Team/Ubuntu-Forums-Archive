---
title: "Sound doesn't work once booted"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Meson on 2007-02-25
The Ubuntu splash screen plays the gnome sound (or whatever it is) as the computer is booting up, however once running sound doesn't seem to work other than system beeps. 

The sound preferences are set to auto-detect however when i switch manually to my sound card and click test there is no sound.

The card is listed as Intel 82801DB-ICH4 (there is also a listing for 82801DB-ICH4 - IEC958)  I think this is correct, it's what is listed in windows.  It came on my Dell Latitude D800.

Any ideas?

---

### Post by apjone on 2007-02-25
Check the users privilages under 'System > Admin > Users + Groups > Double click on user.

---

### Post by Meson on 2007-02-25
Use audio devices was already enabled.

---

### Post by Meson on 2007-02-25
Ok, major breakthrough.  When my external speakers are unplugged sound works fine through the laptop speakers, however when the external speakers are plugged into the headphone jack (as they normally are) the sound is not getting through.

Has anyone had a problem like this before?

---

### Post by Kevkill on 2007-02-25
Double click on the volume icon and make sure your headphone volume is turned up. Also check your PCM volume while you are there. 

-Kev

---

### Post by Meson on 2007-02-25
Despite the fact that I had no idea that was there, it didn't work.  I went to preferences and displayed all options.  I unmuted them and turned them all to the maximum (I'm sure I'm in for a really rude awakening one of these days).  However I did not see a headphone option.

I'll be tinkering meanwhile...  thanks!

---

### Post by Meson on 2007-02-25
Ok, another breakthrough.  When the external speakers are plugged into the headphone jack of my laptop, all is well.

However, I like to leave the external speakers plugged into the headphone jack on my docking station.  Right now the only place without sound is when the speakers are plugged into the Dell docking station.

---

### Post by Rednarb on 2007-03-30
Just wanted to add that I'm having the same problem on a Latitude D510. Plug in external speakers in to the docking station and no sound. Unplug them and sound through the notebook speaks works.

---

### Post by NorLan on 2007-05-21
Hi i have had this problem for a couple of months ago ...

since i blow away breezy after a update i have switched to win for nearly a year now -- but now i am back and this problem i also have with the new 7.04 -- no sound if speakers are plugged into the output of the docking station.

for a couple of minutes it helps to change the samplingrate with this lines

     amixer controls                     %% search the id of IEC-default
     amixer -c 0 cset numid=35 6   %% 35 is IEC-default 6 = 96kHz

you can find this also in [http://ubuntuforums.org/showthread.php?t=27205](http://ubuntuforums.org/showthread.php?t=27205)

here is a bugreport concerning this i think [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/55150](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/55150)

perhaps anybody has a fix or a hint where to search the bug ...

mfg norlan

---

### Post by Toady11 on 2007-07-29
I'll bump this post. I'm having the same problem on my Inspiron 8500 - No sound piped through the docking station sound output. anyone have any luck fixing this?

---

### Post by Toady11 on 2007-07-29
The system does recognize that it is a sound port though - when I plug my speakers into the dock, it disables my onboard speakers, just doesn't play through the dock.

---

### Post by sagesparrow on 2007-10-28
I've got a similar problem with the docking station for dell x300.  the computer speakers work fine, but there is a small subwoofer built into the docking station that really improves the sound quality.  The subwoofer does work with Win XP (dual boot system), but does not work with Gutsy.   The headphone jack is through the computer body, not the docking station so that's not a problem either.  But I think my problem is basically the same problem as reported in the above posts

Any solutions come up yet?

---

### Post by Meson on 2007-10-29
[QUOTE=http://www.alsa-project.org/main/index.php/Matrix:Main]Even if we have vendor supplied driver documents they may refuse to provide all the necessary information to support devices fully. [/QUOTE]

This may just be one of those problems.

---

### Post by Cardamar on 2007-10-29
I'm getting the same problem. I just can't seem to get my sound working after the log in screen. 
I'm on 7.10 with a Dell XPS 410 Desktop and an Intel HDA Sound Card.

---

