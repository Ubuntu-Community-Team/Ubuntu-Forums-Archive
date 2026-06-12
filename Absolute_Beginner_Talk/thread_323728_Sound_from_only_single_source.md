---
title: "Sound from only single source"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by goodmore on 2006-12-22
I have been using Ubuntu for about six months now. Ever since WGA. My problem is this. I have a cmedia on board sound card. I can only get sound from one source at a time. What ever I fire up first is what I hear. Internet, XMMS, VLC whatever. I would like to be able to hear multiple sounds together. Like the poker game chimes on the net and music. Thank You.

---

### Post by meng on 2006-12-22
What sort of driver are you using? oss?alsa?esd?
Have a look under System > Admin > Sounds (I think).

---

### Post by aysiu on 2006-12-22
I believe you can fix this by going to System > Preferences > Sound Preferences > Sound and unchecking ** Enable software sound mixing**. I could be wrong.

---

### Post by Adramelech on 2006-12-22
echo 'binaryname 0 0 direct' > /proc/asound/card0/pcm0p/oss
echo 'binaryname 0 0 disable' > /proc/asound/card0/pcm0c/oss

I use this when i have no sound with firefox or games it works always, it has to be done everytime you reboot.

---

### Post by user007usa on 2006-12-22
> **aysiu said:**
> I believe you can fix this by going to System > Preferences > Sound Preferences > Sound and unchecking ** Enable software sound mixing**. I could be wrong.

Hello, how would one do this from KDE?  Also does anyone know how to change the screensaver settings in KDE?

---

### Post by goodmore on 2006-12-22
I'm using Alsa. Unchecking the mix sounds did not work. Some apps say the sound card is blocked. Thanx again. I'm not too good at the command line so copying and pasting would help.

---

