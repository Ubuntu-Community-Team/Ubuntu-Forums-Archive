---
title: "Help getting Sound Blaster card to work"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by seth556 on 2007-02-11
I have a Sound Blaster Audigy card. It says it's a LS but it has the same chipset as the SE. I'm not sure the difference. But I need help installing it because creative only has windows support for it.

---

### Post by tbroderick on 2007-02-11
Ubuntu should auto detect and setup your card. Open a terminal, (Alt-F2 and type gnome-terminal), and run alsamixer. In the top left of the screen there should be Card: followed by your driver. You might have to mess with the mixer channels to find the one that controls the master volume.

---

### Post by crispy_420 on 2007-02-11
Try the alsa driver.

Set up these items:

System -> Preferences -> Multimedia Selector

System -> Preferences -> Sound

On gnome panel right click volume control -> preferences , select alsa mixer

---

### Post by RomeReactor on 2007-02-11
Hi. I installed [ld10k1]("http://ld10k1.sourceforge.net/") to get my Audigy SE to work

```
sudo apt-get install ld10k1
```

After that, right-click on the volume control applet (little speaker on the top panel), change the driver and select **Analog Front** as the track to control.

---

### Post by seth556 on 2007-02-11
I installed the id10k1 and the card works but is distorted.

It doesn't distort very much if I turn the preamp all the way down in xmms.

---

### Post by RomeReactor on 2007-02-11
If the sound is crackling, try

```
alsamixer
```

in the terminal and play with the sound levels. You can also install a frontend to alsamixer

```
sudo apt-get install alsamixergui
```

or

```
sudo apt-get install gnome-alsamixer
```

---

### Post by seth556 on 2007-02-11
Thanks, I lowered the Analog Front level and it fixed it. I'm now completly happy with Linux.

---

