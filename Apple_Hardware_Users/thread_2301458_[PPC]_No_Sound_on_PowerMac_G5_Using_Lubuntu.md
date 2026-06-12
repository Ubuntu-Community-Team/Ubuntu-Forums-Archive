---
title: "[PPC] No Sound on PowerMac G5 Using Lubuntu"
date: 2015-11-02
forum: Apple Hardware Users
---

### Post by alexander_martini on 2015-11-02
Just installed lubuntu on a G5 after having resolution problems on a particular television set with linuxmintppc. Lubuntu completely fixed these resolution and frequency issues and is running quite well. However, the sound does not work. I installed Alsamixer and got the sound icon on the toolbar but still no luck. Even installed some alsa gui from the software center but no dice. Anyone have this problem and know a way to fix it? Sound is going to be very important on this computer as its primary use will be in the garage looking up instructions for fixing things.

Thanks in Advance,
Alexander Martini

---

### Post by Roger-H on 2015-11-02
I have different hardware than you (iMac G4) but I just got sound working on my machine with Lubuntu 14.04. I referred to this:

[https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F](https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F)

So  try this. Install gnome-alsamixer. Then edit /etc/modules and add the  following lines (if any of these lines are already there, comment them  out):

```
# snd-aoa
# snd-aoa-fabric-layout
# snd-aoa-soundbus
# snd-aoa-i2sbus
```

Reboot,  then go back, edit the file, each time un-commenting one of these  lines. Hopefully during one of those boots, you see the GNOME Alsamixer  icon in your system tray. Doulble click on it and make sure you crank  all of the different audio levels up before testing.

---

### Post by alexander_martini on 2015-11-02
I appreciate the quick reply Roger, I went top to bottom removing the pound symbols while rebooting and still no luck. I have the sound icon and if I type alsamixer in terminal my master is set at 100. Although it says my card is "SoundByLayout" have no idea what this is.

Alexander Martini

---

### Post by alexander_martini on 2015-11-02
I appreciate the quick reply Roger, I went top to bottom removing the pound symbols while rebooting and still no luck. I have the sound icon and if I type alsamixer in terminal my master is set at 100. Although it says my card is "SoundByLayout" have no idea what this is.

Alexander Martini

---

### Post by alexander_martini on 2015-11-02
Roger,

Just got it working with "snd-aoa-i2sbus" and opening alsa in terminal and boosting "PCM" sorry I thought I had all the levels maxed out but I didn't scroll right :P
Just goes to show human error is almost always the problem. Thanks for the help bud.

Alexander Martini

---

### Post by Roger-H on 2015-11-02
No problem, and I'm glad you figured that the PCM level needed to be boosted. I couldn't remember the label for that setting and I am not home to check my iMac.

---

