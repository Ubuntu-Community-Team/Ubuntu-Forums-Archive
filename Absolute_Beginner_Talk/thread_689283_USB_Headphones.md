---
title: "USB Headphones"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by killermad34 on 2008-02-06
I have a Microsoft LifeChat LX-3000 Headset.  I don't care about getting the microphone to work or anything as of right now, I just want the sound to work on it.  When I plug it in, it lets me select it as my sound device and I can change all the defaults to USB Audio.  When I click the test buttons I hear the beeps, but when I go to play sound, I don't hear anything.

---

### Post by eggdeng on 2008-02-06
Run
```
asoundconf list
```
to see how alsa identifies the available soundcards. Then run
```
asoundconf set-default-card xyz
```
where xyz is the name of your usb headset according to the output of the 1st command.
Reboot for changes to take effect.

---

### Post by killermad34 on 2008-02-06
It doesn't show my USB headset as an option when I type in the first command.

---

### Post by eggdeng on 2008-02-06
Looks like alsa is not recognising the headset. You might find some help at [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

