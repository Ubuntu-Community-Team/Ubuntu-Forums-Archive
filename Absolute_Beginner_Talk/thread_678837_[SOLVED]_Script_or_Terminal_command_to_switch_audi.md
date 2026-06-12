---
title: "[SOLVED] Script or Terminal command to switch audio output?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by jjsonp on 2008-01-26
I can switch the audio output by going to System -> Preferences -> Sound and changing the "Sound playback" device from 'Autodetect' to 'USB Audio'.

How can I do this from the terminal (and ultimately from a script)? I want to be able to toggle between 'Autodetect' (my soundcard & speakers) to USB audio.

Thanks!

---

### Post by LaRoza on 2008-01-26
Try using "asoundconf-gtk"

```

sudo aptitude install asoundconf-gtk

```

You can make a launcher for it.

---

### Post by jjsonp on 2008-01-26
Thanks LaRosa; I've installed it. Looks like exactly what I want - now I just have to get it to work.

---

### Post by theproc64 on 2008-01-26
I have two sound card installed, integrated and a pci one and I'm trying to use the pci one. asoundconf-gtk detects both of them but switching them doesn't seem to do anything. Can anyone help?

---

### Post by jjsonp on 2008-01-26
asoundconf (whether run from the GTK GUI or terminal) doesn't seem to do anything. I suspect it changes the *default* sound output, but not the *active* one?

For instance if I switch from 'Headset' to asoundconf-gtk (the only two choices I have, except for 'PulseAudio') but then go to System->Preferences->Sound, the 'Sound Playback' still reads 'USB Audio', and if I press 'Test' the sound comes out over my headset, not my speakers.

---

### Post by jjsonp on 2008-01-26
bump

---

### Post by jjsonp on 2008-01-27
Actually, asoundconf *does* work, but the change is not reflected in the Gnome sound manager. I suspect this is a bug.

---

