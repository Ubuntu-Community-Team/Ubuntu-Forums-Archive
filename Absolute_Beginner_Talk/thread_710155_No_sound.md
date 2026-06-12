---
title: "No sound"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by Judacoth on 2008-02-28
I am trying to get music to work on my Ubuntu 7.10,, so I Dled XMMS and put some music on my computer.  However, XMMS player seems to be working just fine and shows that its playing the music, but im not hearing anything from my headphones.  Im using a Plantronics Stereo PC Headset. 

I bileave they are the Plantronics Audio 650 USB Multimedia Stereo Headset to be exact.

any help would be very much appreciated.

---

### Post by jan quark on 2008-02-28
what does happen if you run 

```
alsamixer 
```

in terminal?

is something muted?

---

### Post by northern lights on 2008-02-28
Can you please post the output of ```
cat /proc/asound/cards
```

Thank you.

[EDIT]

Just tried it in xmms -
most likely don't need that output.

Right-click on your xmms windows, navigate to "Oprions > Preferences" (or press Alt+P)
Under "output plugin" choose "ALSA", then click on "Configure" pick your USB headset as audio device.

Should be it...

[/EDIT]

---

