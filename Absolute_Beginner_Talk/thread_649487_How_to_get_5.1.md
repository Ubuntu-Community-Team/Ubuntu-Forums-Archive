---
title: "How to get 5.1"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2007-12-25
umm how can i get 5.1 surround sound working in ubuntu. I just got a brand new pair of logitech X-530 and i cant seem to get the surroung sound working in them at all please help.

---

### Post by xelapond on 2007-12-25
What sound card do you have?  Have you installed the drivers for your card(If any available)?

---

### Post by fedex1993 on 2007-12-25
yeah i ahve i dont think there are any for linux. It is a built in 7.1 channel surround sound card that worked very well but ever since i plugged in myy 5.1 sysstem it hasnt worked yet. It is thinking that the main l and r are the rear left and right and this is making me mad since i got it for a xmas present

---

### Post by rkd on 2007-12-25
I have no idea whether this will work for you, but it apparently has worked for others:

[http://www.arsgeek.com/?p=971](http://www.arsgeek.com/?p=971)
[http://www.newlinuxuser.com/surround-sound-in-ubuntu/](http://www.newlinuxuser.com/surround-sound-in-ubuntu/)

Those pages are two descriptions of the same thing (the second really was copied from the first).  It is setting some parameters into a file named .asoundrc, which apparently is used by ALSA.  The directions are short, so I'll copy them here, just to save following those links:

Open a terminal and enter
```
gksudo gedit .asoundrc
```

Then delete anything currently in .asoundrc and paste in these lines:
```
pcm.!default {
type plug
slave.pcm “surround51&#8243;
slave.channels 6
route_policy duplicate
}
```

I have to say I'm a bit suspicious of the "smart quotes" around the word surround51.  If you get any complaint about that command or this doesn't work, try changing them to ordinary double quotes (").

I assume you also need proper drivers for your sound card for this to work.  Maybe Ubuntu already installed the right drivers and the above is the only missing piece.  But if the above doesn't make the sound work right, we probably need the output of lspci to see what your sound card is.

---

### Post by fedex1993 on 2007-12-26
ahh okay i will try again. Yeah thanks for the help. i will try later tonight. i will post my lspci here if it doesnt work

---

