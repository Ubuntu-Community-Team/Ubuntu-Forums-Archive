---
title: "no sound, touch pad doesn't work properly, media player botton doesn't work properly"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by davarse on 2008-04-06
hi everyone, i'm really knew to ubuntu and i just install it to my laptop acer aspire 5920G,,,
i've got few problem, first thing is there is no sound in my speaker (dolby surround), the sound just come out from headphone, i've tried to enable the "surround" on the sound mixer and it does work, however, the headphones doesn't work.. that's just the way around..
the next thing is, my touch pad doesn't work properly; the special effect is not working and the middle botton too... and also the special media botton is not woking properly...
please help>>>> SOS

---

### Post by neurostu on 2008-04-06
What is the "SPECIAL EFFECT" on the middle button you are talking about?

To find out what your touchpad driver is run the following command then paste the output:
```

aptitude search synaptic

```
With that information I can help you trouble shoot your touchpad.

---

### Post by davarse on 2008-04-06
the special effect that i mean is when you touch the top right it's the right click and the auto scrol page which is on the right edge is not working nor the bottom edge... the middle botton is not working either as i should be.

---

### Post by neurostu on 2008-04-06
do you have synaptics installed?
To find out what synaptics package you have installed you can run:
```

aptitude search synaptic

```
then paste the results below, it will help me know what packages you need to install.

---

### Post by neurostu on 2008-04-06
Also what do you want your middle button to do?

---

### Post by danieldumitru on 2008-05-09
This is my reply from this command: aptitude search synaptic
v   gsynaptic                       -                                           
p   gsynaptics                      - configuration tool for Synaptics touchpad 
p   gsynaptics-mcs-plugin           - Gsynaptics MCS plugin                     
p   libsynaptics-dev                - library to access the synaptics touch pad 
p   libsynaptics0                   - library to access the synaptics touch pad 
i   synaptic                        - Graphical package manager                 
v   xfree86-driver-synaptics        -                                           
v   xorg-driver-synaptics           -                                           
i   xserver-xorg-input-synaptics    - Synaptics TouchPad driver for X.Org server

Any idea?

---

### Post by neurostu on 2008-05-09
I've never seen the touch right corner for right click before.... but to get your scrolling I would try installing gsynaptics.
```

sudo apt-get install gsynaptics

```
Then logout-login
go to System->Preferences->Mouse->Touchpad

Let me know if this helps.

---

