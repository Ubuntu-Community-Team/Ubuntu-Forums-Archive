---
title: "Can't get sound to work in Lubuntu 14.04 for PowerPC"
date: 2014-07-15
forum: Apple Hardware Users
---

### Post by jacatone on 2014-07-15
Have Lubuntu 14.04 installed on a Powerbook G4. Tried opening alsamixer in a terminal but said "no such app". Have found some other links in this forum but can't seem to find a definative answer. Where should I start with this issue?

---

### Post by Bucky Ball on 2014-07-15
Installing Pulseaudio and Pulseaudio Volume Control might help and be easier. Read here:

[https://help.ubuntu.com/community/Lubuntu/Setup#Sound](https://help.ubuntu.com/community/Lubuntu/Setup#Sound)

You can use Synaptics or a terminal:

```
sudo apt-get install pulseaudio pavucontrol
```

If you use Synaptics, you are looking for the two in the command: pulseaudio, pavucontrol. Once installed, look in 'Multimedia & Video' or 'Sound & Video' (whatever it is in Lubuntu), launch Pulseaudio Volume Control, get a sound stream going (play some music) and that should appear in the 'Playback' tab under the name of the software you're using. Start tweaking in the 'Output' tab and make sure that is set to output to the correct device. 

Good luck and tell us how you go.

PS: You want the command 'asound' in a terminal for alsa. Also, gnome-alsamixer is a cleaner GUI for alsa mixer. If you right click on the speaker icon and 'Properties', doesn't that give you an alsamixer GUI? ;)

---

### Post by jacatone on 2014-07-15
Still can't` get sound to work. Tried both Gnome Player and Audacious. They look like they're playing OK, just no sound. I do hear the Apple startup chimes though.

---

### Post by bapoumba on 2014-07-15
*Thread moved to **Apple Users**.*

---

### Post by jacatone on 2014-07-15
I don't get it. The sound worked fine in v12.04 but not in v14.04. I had to go back to v12.04 because the sound worked.  Finally got the wifi to work as well. Geeez, what a pain. I can see why only 10% of first time desktop Linux users stay with the OS.

---

