---
title: "Sound Issues - Macbook 4,1"
date: 2014-10-02
forum: Apple Hardware Users
---

### Post by Kale_Freemon on 2014-10-02
Hello all! After being able to fix one issue, the wireless, in my Macbook, another one has reared its ugly head. While this isn't the biggest problem I've had with Ubuntu in the past, it is still a slightly annoying one.

For the most part, the audio in my Macbook 4,1 works fine under 14.04. However, every few minutes, when I'm listening to a song or watching a movie, the audio will play a second of what was played just before, skipping any audio that was supposed to be played at that point, before continuing on in sync with whatever is the source of the audio.

For example, I watch a youtube video (happens with VLC and Rhythmbox as well). At 1:02 the audio cuts out and plays what already was played at 1:00, skipping anything at 1:03, before syncing back up properly with 1:04.

I tried disabling auto mute in "alsamixer" but that didn't solve my problem. I suspect that it's a pulseaudio related problem, but Ubuntu has become so heavily dependent on that broken POS that it would potentially cause more problems by trying to replace it.

Has anyone else encountered this issue? If so, is there a way to fix it?

If it helps, I've attached a screenshot of alsamixer, which shows what my audio hardware is.

Thanks in advance.

---

### Post by este.el.paz on 2014-10-03
K_F:

There is a thread about this more or less issue on the Lubtuntu Users list-serve . . . if you can find your way there and look through the archives from the last few days, you might get some advanced insight . . . but, uh, "sound is a problem" for the recent systems . . . I think on my 14.04 MBPro the sound is messed up, just not worth the time for me to deal with "fixing it" . . . .  But, this isn't a new problem, there should be lots of threads on "fixes" on the forum or on Google . . . .  Hopefully others might stop by and offer some insight, here???

e.e.p.

---

### Post by Kale_Freemon on 2014-10-08
So, I stand behind my original assumption that PulseAudio is a POS as it appears to have been the source of all my discomfort (granted, it works fine on my primary machine).

Because it was being problematic, I decided to disable it, thus forcing everything to use ALSA.

To do this, just go into terminal, and use the command **sudo gedit /etc/pulse/client.conf**. Afterwards, look for the line **autospawn=yes** and uncomment it. Then change the yes to a no. Now, reboot the machine. After this, you no longer have a sound indicator icon. To fix this, I just install QasMixer. **sudo apt-get install qasmixer**

I also added QasMixer to my startup programs.

Volume control keys also didn't work for me. To fix that, I created scripts for each different action. I then assigned keyboard shortcuts to them in the System Preferences.

Shortcuts I used are (all of them require the use of the function key on my Mac):

Volume Up - **CTRL+F12** - ***amixer set Master 5+***
Volume Down -** CTRL+F11 - *[B]amixer set Master 5-***
[/B][S]Volume Mute - **CTRL+F10** - ***amixer set Master mute***
Volume Unmute - ** CTRL+SHIFT+F10** - ***amixer set Master unmute***[/S]

Edit:

I have since edited the **Volume Mute** script to allow for it to trigger between muted and unmuted with the same keyboard shortcut.

```

#! /bin/bash
AM=$(<.AM.conf)
if [ "$AM" = "1" ]; then
	amixer set Master unmute
	echo "0" > .AM.conf
else
	amixer set Master mute
	echo "1" > .AM.conf
fi

```

---

