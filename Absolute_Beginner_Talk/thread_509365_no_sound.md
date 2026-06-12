---
title: "no sound"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Timmy66 on 2007-07-25
I just installed feisty on a older computer.The install went flawlessly I just have one problem.That is with the sound I have none.I went and got all the codecs I could find.
I also have Windows M.E.  on here for playing games.It can find my on board sound but feisty can't what is up with that.
I would appreciate any help I can get please.

---

### Post by NilsE on 2007-07-25
In a terminal run: asoundconf list



This should return a list of cards.  Yours should be there


In a terminal run: 

asoundconf set-default-card xxxxxxx


Then again with sudo: 

sudo asoundconf set-default-card xxxxxxxxx

  
xxxxxx = the name of your sound card from the list.  I think it is case sensitive.


This will set the defaults for the card and create a config file. 


In sound preferences "ALSA - Advanced Linux Sound Architecture" should be the choice

In the volume control turn on as many options as you can to show up in the panel. Make sure none are muted.

---

### Post by Timmy66 on 2007-07-25
nothing came up at all.

I opened volume control and it says that there is no GStreamer plugin or device found.

I know I installed that GStreamer plugin

---

