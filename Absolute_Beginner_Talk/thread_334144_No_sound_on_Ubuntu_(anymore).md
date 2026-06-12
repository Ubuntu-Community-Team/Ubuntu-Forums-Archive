---
title: "No sound on Ubuntu (anymore)"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by noisc on 2007-01-08
My computer dual-boots into both Windows XP and Ubuntu. Now since I've had Ubuntu (for about two weeks now) the sound has worked perfectly. This morning I booted it up and tried to play some mp3's, and there was no sound. Tried to play some wav's, same thing. Tried to play something on Youtube and again, no sound. 

On Windows XP, the sound works perfectly, so I'm pretty sure it's not a hardware problem. Here's what I know

- the system beep still sounds
- the system volume is not muted
- Ubuntu lists a recognized audio device when I run lspci
- The 'no sound' thing applies across all programs I've tried so far including Rhythmbox, Amarok, and Firefox. 
- The Ubuntu startup sound doesn't play, either
- Everything was fine before today. I don't know what I did to mess it up. 

If anyone could list some basic sounds tests/settings I could do to see what the problem is, I'd be very thankful.

---

### Post by scrooge_74 on 2007-01-08
Go to synaptics, uninstall everything related to alsa, and then reisntall it

Should take you a few minutes and will probably clear up whatever is messed up

---

### Post by noisc on 2007-01-08
Thanks for the reply.

Um, I'm a little squeamish about doing what you're asking because Synaptics gives me the following list of 'alsa' things I have installed:

alsa-base
alsa-utils
gstreamer0.10-alsa
libesd-alsa0
libpt-plugins-alsa
libsdl1.2debian-alsa

Ok, so when I mark those for removal, Synaptics gives me a list of other packages that are required to be removed. Among them are some packages that seem to be Ubuntu-critical, like ubuntu-minimal, ubuntu-desktop, gnome-terminal, and a whole slew of programs that seem to be some basic, almost built-in programs, (e.g. gedit). Some of these packages are recommended *not* to be uninstalled. 

Are you sure this is something I should be doing? It almost seems safer to reinstall the whole OS....

---

### Post by ardvark71 on 2007-01-08
> **noisc said:**
> Thanks for the reply.

Um, I'm a little squeamish about doing what you're asking because Synaptics gives me the following list of 'alsa' things I have installed:

alsa-base
alsa-utils
gstreamer0.10-alsa
libesd-alsa0
libpt-plugins-alsa
libsdl1.2debian-alsa

Ok, so when I mark those for removal, Synaptics gives me a list of other packages that are required to be removed. Among them are some packages that seem to be Ubuntu-critical, like ubuntu-minimal, ubuntu-desktop, gnome-terminal, and a whole slew of programs that seem to be some basic, almost built-in programs, (e.g. gedit). Some of these packages are recommended *not* to be uninstalled. 

Are you sure this is something I should be doing? It almost seems safer to reinstall the whole OS....

I'm not sure if it will work but what if you just tried reinstalling The ALSA components?

Best Regards...

---

### Post by Efwis on 2007-01-08
you don't have to remove them, mark them for re-installation, if that doesn't work then we need to look somewhere else.

---

### Post by hazillow on 2007-01-08
I had the very same problem. What I did (at the prompting of someone here) was run the live CD, and check if the sound works there. (It did) I ran alsamixer in konsole and wrote down all the settings...what was muted, what wasnt, volume levels, etc. I went back to the installed version and changed the settings to what worked in the Live CD. Worked perfectly.

---

### Post by noisc on 2007-01-08
ahhh, thanks for the clarification.

Ok, I did the reinstallation, but I've still got no sound. I even restarted the system.

Any other suggestions?

When I go to System->Preferences->Sound, everything seems to look ok. There seem to be some samples I can play under the "Sounds" tab, and when I click those, nothing plays.

Edit:
[QUOTE="hazillow"]I had the very same problem. What I did (at the prompting of someone here) was run the live CD, and check if the sound works there. (It did) I ran alsamixer in konsole and wrote down all the settings...what was muted, what wasnt, volume levels, etc. I went back to the installed version and changed the settings to what worked in the Live CD. Worked perfectly.[/QUOTE]

Just saw this. Ok, I'll see if that works.

---

### Post by Azakus on 2007-01-08
In the console type "alsamixer" and raise the volume of everything up. Use the <- and -> keys to go between the bars and the up and down arrows to change the volume.

---

### Post by noisc on 2007-01-08
Whew, everything's fine now.

Thanks hazillow and Azakus.

My 'PCM' channel was muted in alsamixer (muted AND at 0 volume, had to press 'm' to unmute, and then raise the volume with up/+; props to wikipedia for alsamixer commands :-D ). Obviously I didn't consciously change this. Anybody know what I could've done that would've changed this? I didn't install any audio/video-related packages yesterday.

Is alsamixer the only way to change these settings?

By the way, I've got an 'IEC958' channel that's also muted in alsamixer. Anybody have any idea what this is and if I should unmute it?

---

### Post by hazillow on 2007-01-08
> **noisc said:**
> Whew, everything's fine now.

Thanks hazillow and Azakus.

My 'PCM' channel was muted in alsamixer (muted AND at 0 volume, had to press 'm' to unmute, and then raise the volume with up/+; props to wikipedia for alsamixer commands :-D ). Obviously I didn't consciously change this. Anybody know what I could've done that would've changed this? I didn't install any audio/video-related packages yesterday.

Is alsamixer the only way to change these settings?

By the way, I've got an 'IEC958' channel that's also muted in alsamixer. Anybody have any idea what this is and if I should unmute it?

you can download "alsamixergui" to get the same thing, but in a (ugly) GUI. kmix also does the same thing (i think).

like i said, the same thing happened to me - all of a sudden it muted things that i needed. luckily your problem wasn't as bad as mine - half the stuff i needed was muted and half the stuff i didnt need was on. there's a way to save those alsa settings, [http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449) addresses it.

anyway, it would probably be a good idea to write down the settings anyway - just in case something changes it without you knowing again.

glad i could help!

---

