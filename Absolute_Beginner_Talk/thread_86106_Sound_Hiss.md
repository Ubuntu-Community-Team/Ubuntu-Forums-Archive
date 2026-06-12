---
title: "Sound Hiss"
date: 2005-11-04
forum: Absolute Beginner Talk
---

### Post by Cufishing on 2005-11-04
Ubuntu found and installed all my 'onboard' hardware. Sound works, but when I started to listen to music last night, I could hear a distintive 'hiss' in the speakers. Connections are good, and hiss is NOT present under WinXp.

MSI 6570 Delta. nVidea Nforce 2 chipset, onboard sound.

Can anybody point me in a clear direction?

---

### Post by wishyjr on 2005-11-04
yes, i have similar issues - my sound works ok generally just minor hisses and crackles on certain things (no examples spring to mind right now). Thing is, my sound worked pretty well on Hoary but is less than great since i updated to the Badger :)

Im also using onboard sound -nforce 4 family i think.

---

### Post by Kapre on 2005-11-04
[QUOTE=Cufishing]Ubuntu found and installed all my 'onboard' hardware. Sound works, but when I started to listen to music last night, I could hear a distintive 'hiss' in the speakers. Connections are good, and hiss is NOT present under WinXp.

MSI 6570 Delta. nVidea Nforce 2 chipset, onboard sound.

Can anybody point me in a clear direction?[/QUOTE]

Cufishing - try playing with your sound settings (ALSA, ESD, OSD). Maybe thru this you can remove the hissing.

K

---

### Post by SilentCacophony on 2005-11-04
I had the same problem, though I use a soundblaster.

In my case, it was just low signal-to-noise ratio caused by the volume (mixer) settings. Here's what I did:

Set your 'Master' volume to a comfortable setting (not too loud,) and play some sound. Note the loudness.

Right-click the volume icon, and select 'Open Volume Control'

In the Volume control dialog, select the second tab (named 'Capture',) and increase the 'PCM' volume setting to at least 75% (mine's about 90%.)

Play the same sound that you did before, and see if it's louder. If so, then adjust it so that the 'Master' volume gives you the range that you want. You may also want to raise the 'CD' volume.

In my case, it made a huge difference, and I don't hear any hiss anymore.

You can also try playing with the sound prefs in *System->Preferences->Multimedia Systems Selector*.

---

### Post by Cufishing on 2005-11-05
[QUOTE=Kapre]Cufishing - try playing with your sound settings (ALSA, ESD, OSD). Maybe thru this you can remove the hissing.

K[/QUOTE]
If your willing to assist, here is some info that leaves me :confused: 
From the Nvidia website: "NVIDIA's audio driver is an OSS driver, and requires OSS sound support in the kernel. NVIDIA's audio control panel is a Qt-based application, and requires Qt run-time libraries in order to run."

I do not have OSS available!

Also, I have learned there is a chipset driver out for 'my' chipset. It has a pretty easy to follow install, but not sure if it will have said OSS, or if I need to go find it somewhere?

All of my options work, but I have not tested for performance. Sound, Network, Video, USB, IDE etc.

---

