---
title: "Getting Microphone to Work in Kubuntu 7.10 for WoW"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by zyxyellowxyz on 2008-02-22
I found a very useful post about how to get it to work [here]("http://forums.worldofwarcraft.com/thread.html?forumId=11110&sid=1&topicId=2200220013&pageNo=1&") but had problems when I came to the last step (not really the last step, but the last step to get it to work)

> 
3) Configure Wine to use ALSA.
Open up a terminal and run:

winecfg



Once the winecfg main windows is up, navigate to the "Audio" tab.
Here you will see a list of Sound Drivers available to Wine.
UN CHECK "OSS Driver"
CHECK "ALSA Driver"

Within the "Alsa Driver" tree you should now see your device(s) within the "Wave Out Devices" and "Wave In Devices".
Here is what my Alsa Driver tree looks like:

- - Sound Devices

  |- Alsa Driver

   |- Wave Out Devices

      |- dmix:0

      |- USB Audio

   |- Wave In Devices

      |- dsnoop:0

      |- USB Audio


If you have only one sound card, and will be using it for voice chat, you may not see the "USB Audio" device.

Now, at the bottom of this tab we need to change some options.
Make sure the following options are set:
"Hardware Acceleration:" to "Full"
"Default Sample Rate:" to "44100"
"Default Bits Per Sample:" to "16"
CHECK "Driver Emulation"

Now click "Apply", the click "OK" and move on to step 4.


I went to terminal, I entered in winecfg and got the following

> 
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.


can anyone help me with this? I restarted the computer (by "old habit" when all I had to do is log out) and then restarted the X server and got the same problem.

---

### Post by zyxyellowxyz on 2008-02-22
Never mind about the above, I was trying to run it in sudo su

Now that I have Wine Configuration open, and in the audio tab, I only have the following under ALSA:

--MIDI Out Devices
---Midi Through
--MIDI In Devices
---Midi Through
--Mixer Devices
---HDA Intel

Where would I be able to get the WAVE drivers I need for ALSA? This would help so much.

---

