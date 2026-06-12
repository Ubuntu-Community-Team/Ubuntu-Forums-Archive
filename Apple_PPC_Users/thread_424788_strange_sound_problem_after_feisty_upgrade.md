---
title: "strange sound problem after feisty upgrade"
date: 2007-04-27
forum: Apple PPC Users
---

### Post by math_penguin on 2007-04-27
Hi I've been using Ubuntu on an old g4 powerbook for quite awhile now without any major problems. THere have been several time when I have had to reconfigure my sound or network drivers, but lately things have been smooth sailing. until........feisty.

The feisty install went kinda sorta okay. I had to force it to install a package named axyl-lucene by manually editing one of the scripts that it was trying to run during the install, but everything else installed fine. Reboot went okay and all is well.... Then I tried playing some music...... The Gnome Music Player Client wasn't responding so I opened XMMS it told me my soundcard was blocked. So I tried quiting every app I could think might be blocking it and tried again, I got sound for like 2 seconds then playback just stops. I keep trying to hit play and sometime I get a small snippet of sound other times I don't. This is also happening when I try playing back movies with mplayer, I can see the video but no sound and it will only pay for a second before just stopping. Can anyone give me some advice about debugging this issue. Do you know of any log files that ALSA is dumping info to that I might be able to look at? Ever heard of anything like this happening before.

BTW before my feisty upgrade I encountered something kinda similar when I would try to print while listening to music. when I started a print job the music would stop. mpd was kind enough to keep trying to get the music started for me but as long as the print job was running it would only play for a sec before stopping. once the job stopped though everything was okay.

thanks for any help or ideas you might have. here are some of my ALSA config files:


asound.conf
------------------------------------

pcm.card0 {
        type hw
        card 0
}

pcm.!default {
        type plug
        slave.pcm "dmixer"
}

pcm.dmixer {
        type dmix
        ipc_key 1024
        ipc_key_add_uid false
        ipc_perm 0666                   # mixing for all users
        slave {
                pcm "hw:0,0"
                period_time 0
                period_size 2048
                buffer_size 32768
                rate 48000
        }
        bindings {
                0 0
                1 1
        }
}

pcm.jackplug {
        type plug
        slave { pcm "jack" }
}

pcm.jack {
        type jack
        playback_ports {
                0 alsa_pcm:playback_1
                1 alsa_pcm:playback_2
        }
        capture_ports {
                0 alsa_pcm:capture_1
                1 alsa_pcm:capture_2
        }
}


.asoundrc
---------------------------------------------------------------
pcm.powermac {
        type hw
        card 0
}

ctl.powermac {
        type hw
        card 0
}

pcm.jackplug {
        type plug
        slave { pcm "jack" }
}

pcm.jack {
        type jack
        playback_ports {
                0 alsa_pcm:playback_1
                1 alsa_pcm:playback_2
        }
        capture_ports {
                0 alsa_pcm:capture_1
                1 alsa_pcm:capture_2
        }
}

---

### Post by stmiller on 2007-04-27
Is this a tibook? There is a possible bug. Read this thread:

[http://ubuntuforums.org/showthread.php?t=412151&page=3](http://ubuntuforums.org/showthread.php?t=412151&page=3)

---

### Post by math_penguin on 2007-04-27
Thanks for the tip. I will move my questions to that thread.

---

