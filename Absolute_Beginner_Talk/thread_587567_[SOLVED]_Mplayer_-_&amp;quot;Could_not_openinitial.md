---
title: "[SOLVED] Mplayer - &amp;quot;Could not open/initialize audio device -&amp;gt; No sound&amp;quot;"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by homerj742 on 2007-10-22
I'm getting this error after upgrading to Gusty, it was working great before! Please, any help would be greatly appreciated. Thank you!

---

### Post by Maestro23 on 2007-10-22
Maybe a setting got changed.  In Mplayer go to Prefs>> Audio Tab

See what it's set to, and is it the same as you had it before.

---

### Post by cairn on 2007-10-22
I have the same issue. Sound works fine for me in AmaroK and Totem and system sounds play fine. I just upgraded to Gutsy and when I did the upgrade, it gave me a little info pop-up right after the upgrade saying I needed to update some sort of sound thing and gave me a command to enter into the terminal. I accidentally clicked onto the next info-pop-up-message thing without entering the command and without realizing that there was no way to go back to the previous message. I'm not sure if that has anything to do with this problem with mplayer.

---

### Post by homerj742 on 2007-10-22
the Audio Prefs are set to "alsa"

Cairin, now that you mention it, I had the same message. crap!

---

### Post by homerj742 on 2007-10-24
Bump,
Anyone else find a solution? Any help would be greatly appreciated...

---

### Post by wolux on 2007-10-24
I got the same after installing pulseaudio for audio preview in nautilus... And as a consequence no more sound in flash videos, and impossible to mplayer to open the audio device BUT when I kill pulseaudio no more troubles...
Pulseaudio doesn't release (sorry for my english) /dev/dsp...
So it's ok for me but no more audio preview...

---

### Post by cairn on 2007-10-24
I was able to get the sound working in mplayer by selecting "OSS" as the driver instead of ALSA. The setting is in "Preferences" then on the "Audio" tab, make sure that "oss" is the highlighted option. I clicked on the "configure driver" option and ensured that the options were left on the defaults. Hope that helps someone else!

---

### Post by homerj742 on 2007-10-24
I got it working, I had to set the default sound card:

Check out this site:

[http://technical-itch.co.uk/2007/10/19/ubuntu-710-upgrade-first-impressions/](http://technical-itch.co.uk/2007/10/19/ubuntu-710-upgrade-first-impressions/)

Here is an example of the code:

```
asoundconf list 
**list of sound cards**

asoundconf set-default-card **name of sound card**
```

---

### Post by Maestro23 on 2007-10-24
> **homerj742 said:**
> I got it working, I had to set the default sound card:

Check out this site:

[http://technical-itch.co.uk/2007/10/19/ubuntu-710-upgrade-first-impressions/](http://technical-itch.co.uk/2007/10/19/ubuntu-710-upgrade-first-impressions/)

Here is an example of the code:

```
asoundconf list 
**list of sound cards**

asoundconf set-default-card **name of sound card**
```


Good deal.  Mark this SOLVED using Thread Tools.

Thanks.:)

---

### Post by dmfrey on 2007-10-27
Is this a setting you have to continually set after each reboot?  If yes, can it be set permanently?

---

### Post by mynoks on 2007-11-06
I have this same problem but the solution did not work for me, after surfing a bit a found this Brazilian people ([http://www.softwarelivre.ufsc.br/pipermail/gufsc/2007-June/002405.html](http://www.softwarelivre.ufsc.br/pipermail/gufsc/2007-June/002405.html)) explaining a solution that worked great :

1. run the file from terminal i.e.: 
```
#mplayer song-artist.mp3
[...]
alsa-lib: pcm_hw.c:1242:(snd_pcm_hw_open) open **/dev/snd/pcmC0D0p** failed: **Device or resource busy**
[...]

```
so it is busy ... someone is using the device ... ¿witch one? run :
```
#fuser -v /dev/snd/pcmC0D0p
                     USER       PID ACCESS COMMAND
/dev/snd/pcmC0D0p:   suser     6120 F.... /usr/bin/gnome-
```

and now lets kill the process (by using its Proces ID) :
```
#kill -9 6120
```

wish this helps someone.

---

