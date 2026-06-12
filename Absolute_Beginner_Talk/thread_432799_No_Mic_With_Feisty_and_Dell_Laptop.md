---
title: "No Mic With Feisty and Dell Laptop"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by RichPicker on 2007-05-04
What have I read about installing Drivers?

I had my mic working with Edgy, but not yet with Feisty. I have the mic plugged in, nothing is muted, capture is at max. I'm not sure what's going on. The only irregular thing is the "Bad Device" massages I get when I start kmix. The sound works fine - maybe kmix is not recognizing the devices? I'm grasping at straws at this point. Haven't had the mic working since an Edgy update, and not since installing Feisty - maybe one month now. When I record my voice with Audacity, I hear static, and just barely my voice. I'm puzzled.

---

### Post by viciouslime on 2007-05-04
You could try running "alsamixer" from a terminal and playing with that, might get it working for you.

---

### Post by RichPicker on 2007-05-04
I've adjusted the settings in  alsamixer, amixer, kmix, volume control; and the preference options in Audacity and Sound Recorder. None of those help.  Still no mic.

---

### Post by RichPicker on 2007-05-04
Seems that the mic is tricky with HDA Intel sound on laptops - from Dapper to Feisty. Could it be that the workaround for Feisty has not yet been created?

Also, my laptop does NOT have a built-in mic. Could it be that the computer is looking for one of those instead of the external mic plugged into the jack?

---

### Post by RichPicker on 2007-05-10
Could I go backwards, and install Dapper Drake? Does anyone know if the mic worked on Dell laptops with that distro? It worked for me with Edgy until the notorious update. Maybe the mic would work with Dapper? Anyone have experience using their external mic with Dapper on a Dell laptop?

---

### Post by NilsE on 2007-05-10
I used the following to get my Dell sound card and mic working. There was a config problem introduced in 7.04 which this should fix.  I found this on the forum somewhere but I also keep a log of what works so here it is.

```
In a terminal run: asoundconf list

This should return a list of cards.  Yours should be Intel
```

```
In a terminal run: asoundconf set-default-card Intel

Then again with sudo: sudo asoundconf set-default-card Intel


This will set the defaults for the card and create a config file. If yours is not Intel replace it with the name you found in list.

```
In sound preferences "ALSA - Advanced Linux Sound Architecture" should be the choice except mixer should be Sigmatel.

In the volume control turn on as many options as you can to show up in the panel. Make sure none are muted.

---

