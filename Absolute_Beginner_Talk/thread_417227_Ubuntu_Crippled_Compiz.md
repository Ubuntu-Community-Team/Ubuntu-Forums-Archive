---
title: "Ubuntu Crippled Compiz"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Happy_Man on 2007-04-21
So yeah, I was looking through my brand-spanking new Feisty install and saw the words: Desktop Effects. Wondering what it was about, I clicked, only to see that it was some interesting Beryl-like stuff. This explains the "compiz-core" part of the upgrade, I figured, and enabled them. Lo and behold, I got a grand total of two --yes, two -- settings I could change. I immediately went to Synaptic and searched for something I could tweak Compiz with, and found gnome-compiz-manager. Well, it was an improvement. But, I still can't get to half the things Beryl could do. Is that really all Compiz is, or is there more that the devs are hiding from us? if so, how do I outsmart them and get all them settings?

---

### Post by Campingman on 2007-04-21
You could always install beryl again.  I installed it from Feisty from the repositories and it worked out of the box.  I was well impressed as it took me hours with edgy.

---

### Post by ButteBlues on 2007-04-21
> **Happy_Man said:**
> So yeah, I was looking through my brand-spanking new Feisty install and saw the words: Desktop Effects. Wondering what it was about, I clicked, only to see that it was some interesting Beryl-like stuff. This explains the "compiz-core" part of the upgrade, I figured, and enabled them. Lo and behold, I got a grand total of two --yes, two -- settings I could change. I immediately went to Synaptic and searched for something I could tweak Compiz with, and found gnome-compiz-manager. Well, it was an improvement. But, I still can't get to half the things Beryl could do. Is that really all Compiz is, or is there more that the devs are hiding from us? if so, how do I outsmart them and get all them settings?
The entire set of Compiz settings can be edited with  gconf-editor: look in /apps/compiz.

---

### Post by Happy_Man on 2007-04-21
> **Campingman said:**
> You could always install beryl again. 

All right, I did, now how do I turn it on? The usual "run beryl-manager from command line" has absolutely no effect; the manager does open, but in Metacity, not Beryl. Grrr.

---

### Post by Happy_Man on 2007-04-21
> **ButteBlues said:**
> The entire set of Compiz settings can be edited with  gconf-editor: look in /apps/compiz.

Oh, ok. That makes life a bit easier. Now, for my next question. How do I enable the cube to rotate when I press and hold the middle mouse button on the desktop?

---

### Post by Campingman on 2007-04-21
Oops, sorry.  The joys of Ubuntu.
Is it not in applications/system tools/beryl manager.  I can run beryl from there on mine.  I installed with aptitude also not synaptic

---

### Post by pppetter on 2007-04-21
> **Happy_Man said:**
> All right, I did, now how do I turn it on? The usual "run beryl-manager from command line" has absolutely no effect; the manager does open, but in Metacity, not Beryl. Grrr.

Just click on the beryl-manager icon and select from the menu that shows up.

---

### Post by Campingman on 2007-04-21
If the manager opens go to select window manager and select beryl, you should be able to select beryl,compiz or metacity.

---

### Post by Happy_Man on 2007-04-21
> **pppetter said:**
> Just click on the beryl-manager icon and select from the menu that shows up.

Yeah, but there is no icon. That's the thing.

---

### Post by BiodieselMan on 2007-04-21
I had Edgy 6.10 configured with Beryl and NVIDIA drivers (2 different cards on 2 different machines), Both machines functioned flawlessly  - I loved the transparency of the windows and the minimize flame burning effects - and was able to rotate the 3d desktop cube by holding down CTRL, ALT and left mouse click drag.  

After upgrading to Feisty Fawn 7.04, the restricted drivers show loaded and I can get the desktop effects of Wobbly windows to work just fine. 

 The 3d desktop effect (rotating cube interface) worked immediately after upgrade to Feisty, then suddenly, i cannot seem to rotate the cube desktop anymore.    Is there something that got changed/disabled or some ini file to edit or some other keys to hold down to see the rotating cube style workspaces?    

-Matt-

---

