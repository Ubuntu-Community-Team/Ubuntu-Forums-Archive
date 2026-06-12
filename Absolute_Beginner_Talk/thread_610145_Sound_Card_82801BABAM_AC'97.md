---
title: "Sound Card 82801BA/BAM AC'97"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by Da King on 2007-11-11
well im using the Intel 82801B/BAM USB AC'97 and sound works fine just that when i put my earphone jack the sound still plays from the inbuilt speaker and inside my earphone..found the same problem in a thread and it hadnt been answered so i tot i wod add it [HERE]("http://ubuntuforums.org/showthread.php?t=589245")

---

### Post by FuturePilot on 2007-11-11
Try muting the master volume. System>Preferences>Volume Control. Mute the slider that says Master.

---

### Post by Da King on 2007-11-11
gutsy doesnt have it..it has "system-pref-sound" rather..where do i try again?

---

### Post by FuturePilot on 2007-11-11
Hmmm. It's there for me. Anyways press Alt+F2 and enter this
```
gnome-volume-control
```

---

### Post by Da King on 2007-11-11
ok i found it just on the top bar..right click on it and i had the options..i musted the masterand yet the on board speaker still plays..i check all the sound devices to uses my card and on the sound playback it had ALSA MIXER attached to the sound card name..there is no other device with the card name only..

---

