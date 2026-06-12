---
title: "Sound no longer works on laptop (after trying to configure ALSA)"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by Tally Solleni on 2007-11-12
Hello there.  I recently installed Ubuntu Feisty Fawn (have yet to upgrade to Gutsy) on my laptop (Compaq Presario, Intel Celeron processor).  It worked completely and absolutely perfectly until I began trying to configure the sound correctly; I wanted to be able to work with MIDI files and such like, so I started doing a bit of searching for drivers and how to configure them.
Essentially, here is what happened: I looked up assorted help files (help.ubuntu.com, ubuntuguide.org, and so forth), and then began to try and locate the correct drivers.  As far as I can gather, my sound card is an Intel 82801DB-ICH4 (I can't find much information on this type, though, so I might be wrong), presumably meaning it falls under the category of intel8x0. (?  Not certain on this.)
I found the standard alsa-driver etc. files, and proceeded to download them.  This is where I hit my first snag- I was able to create the "alsa" directory in usr/src, but no matter what I do, the system refuses to grant me permission to alter that directory in any way (including placing the driver files inside of it).  I have checked and double-checked the permissions in "Users and Groups", just to see if there's anything I am not allowed to do, but to no avail.  I ended up trying to compile and install the drivers from the home folder.  This may be where I messed up, but I couldn't really do anything else.  I followed the instructions I found at help.ubuntu.com ([this one]("https://help.ubuntu.com/community/HdaIntelSoundHowto")), and was informed that the drivers had been compiled and installed correctly.  I briefly attempted to mess with the ALSA sound mixers before deciding that 1)I could make neither heads nor tails of it and 2) the devices did not seem to be muted, despite what I had been told previously.  Unsure of the proper course of action, I then restarted my computer, as per the aforementioned instructions, and decided that I would deal with whatever new problems might arise once the system had rebooted.
After signing in, I noticed that the "login" sound did not play.  I attempted to play an .mp3 file, to see what was going on, and was informed that it could not connect to the sound server.  I then tried to open the Volume Control, and received the message that I completely lacked either Gstream plugins or a sound card.  I checked to see if I was missing any Gstream plugins, and I had indeed missed two, but installing them had no effect.  I tried to install PulseAudio (due to that business about a sound server), but all attempts to run it are met with a "connection refused"message.  By now, when I tried to open the Volume Control, I was instead told that it could not detect any sound hardware.  And through all this, mind, I have still been denied "usr/src" permissions, so the ALSA drivers are still in the wrong place.
At my wits' end, I checked help.ubuntu.com and began following the instructions to "Manually Specify Module Parameters".  But when I try to run the command-line (cat /proc/asound/card0/codec#* | grep Codec) that begins the tutorial, it does not work.  I'm assuming, due to the asterisk, that a number or somesuch is needed after the "code#", but I have absolutely no idea what belongs there.  As a result, I could not use that command to determine the model of my sound card.  Well, no matter, I thought.  I already knew that it was an intel8x0 from assorted business earlier.
I proceeded to the next step, modifying "/etc/modprobe.d/alsa-base", in order to show it what type of sound card I had.  But despite my best efforts, my apparent model was not listed.  I eventually settled on the type of model that was most similar to it, as far as I could tell (can't remember what it was, sorry), and tried to paste the modified line into alsa-base, as instructed.  I then restarted my computer; this had no visible effect.  I changed the type to "laptop" (it remains as this currently), despite the brand being different, and tried again.  This, too, had no effect.
My error message for Volume Control now, once more, states that it cannot find any Gstream plugins.  This means that I **cannot open Volume Control**, just for the record.  If I try to open an .mp3 file in Totem, I am told that it "could not locate a resource for writing", although the visualization and search bar move as if the song is playing normally.  If I try to open PulseAudio Manager, the connection is refused.

In summary...
I don't have permission to edit certain directories, although Administration claims that I should.  Thus, the fact that I cannot add any files to the ALSA directory may be to blame, but I'm not sure.  I compiled and installed the drivers from Home without any apparent issues, but after restarting, I no longer had any sound at all.  The system claims to lack Gstream plugins/devices, although this does not seem to be true, and cannot establish a connection to the PulseAudio server.  I attempted to edit alsa-base to specify my model of sound card, but was unable to do so correctly.  I still do not have sound of any kind, but upon opening a music file, the search bar and visualization move as if the file is playing (despite an error message and the fact that sound is not coming through the speakers).  My computer is a laptop, so I cannot change my sound card.  I currently cannot access Volume Control.

I am still a newbie, and not very good with computers yet, so any assistance is very much appreciated.
Thank you very much for your time.

---

### Post by MrFSL on 2007-11-13
> Essentially, here is what happened: I looked up assorted help files (help.ubuntu.com, ubuntuguide.org, and so forth), and then began to try and locate the correct drivers. As far as I can gather, my sound card is an Intel 82801DB-ICH4 (I can't find much information on this type, though, so I might be wrong), presumably meaning it falls under the category of intel8x0. (? Not certain on this.)
I
To find out information about your audio hardware you can type:```
lspci | grep -i audio
```
Alternatively you can type:
```
cat /proc/asound/cards
```
Also there are other files in /proc/asound that are very informative and useful.

> After signing in, I noticed that the "login" sound did not play.
You might want to check the contents of your log files after a reboot and look for helpful error messages. **System > Administration > System Log**

---

### Post by Tally Solleni on 2007-11-13
Thank you very much!  I found out that my initial assumption as to the model of sound card was, indeed, correct, meaning that the way I had set ALSA as of my post was actually wrong.  However, alsa-base had spontaneously decided that I no longer had permission to edit it.  I used chmod to gain permission to the file, and eventually was able to fix the offending line, after which I restarted...to no effect.
Next, I attempted to gain permission to "usr/src/alsa", which had remained empty all this time.  This was successful, and I promptly put the alsa-driver, alsa-lib, and alsa-utils folders in their proper place.  I restarted afterwards (checked the logs but didn't learn much), and...still have no sound.
The error message when I try to open Volume Control is "No volume control GStreamer plugins and/or devices found."  (I'm still not sure what it means by that.)  The status of pretty much everything else is still the same.
I notice that I CAN access Sound Preferences, and that nothing is listed under the "Default Mixer Tracks" heading.  (The "Device" menu is blank, as is the box that usually lists the tracks.)  I'm assuming that this is a symptom rather than the source of the problem, but I thought it was worth mentioning.
Should I just give up and try to remove the ALSA drivers, since everything worked fine until I installed them?  Or could it just be a problem with using Feisty Fawn instead of Gutsy Gibbon?

---

