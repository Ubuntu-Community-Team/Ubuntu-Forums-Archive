---
title: "[SOLVED] How do I install compiz fusion on gutsy?"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by shedokan on 2007-12-17
Is there a tutorial for compiz installation for gutsy?

---

### Post by atomkarinca on 2007-12-17
It's already installed: System > Preferences > Appearance > Visual Effects.

---

### Post by kpkeerthi on 2007-12-17
And just install **ccsm** using Synaptic to tweak it.

---

### Post by shadow-of-sin on 2007-12-17
You should also install compizconfig-settings-manager to allow you to tweak compiz to your liking:
```
sudo apt-get install compizconfig-settings-manager 
```

---

### Post by hyper_ch on 2007-12-17
Open Synaptic, and search for compiz configuration settings manager... that will make a new entry "adavnced effect" in your system --> settings

---

### Post by grayfox803 on 2007-12-18
i am having loads of problem with this thing. I do not have in system- preferences or system-administration the icon that says visual effects. I did try to apt get the compiz config manager and when i search for it via synaptic, i see it but i cant do jack shat with it.......any imput is greatly appreciated.
Thanks

---

### Post by RomeReactor on 2007-12-18
Hi. grayfox, Visual Effects is not an icon in "System->Preferences" or "System->Administration"; you have to launch the "Appearance" application in "System->Preferences->Appearance". There you'll find a tab named "Visual Effects", with different settings. Try it in "Normal" first. You must have direct rendering enabled for the effects to work:
```
glxinfo | grep direct
```
if the output is "Yes", then you're (mostly) ready to go. What video card do you have?

---

### Post by grayfox803 on 2008-01-05
ok i was really pissed at this last install, had some problems so i just wiped the sucker and did a fresh install. The last install i had on here was i think version 7, now i am on 10. There was a thing in syste-> Preferences-> and in here was something about compusFusion that i could make fire appear on the desktop and rain drops and stuff like that. Now i dont get anything near that. I know before i gave up last week that i downloaded something that i saw in another thread. My graphics card is an Nvidea, however you spell that lol. As of right now, i did figure out the new appearnce tab thinger and got some little cool things going, but i also want to setup like a cubed desktop where it spins and what not. I have a buddy who has this as well and totaly tricked it out, but he has a different graphics card and said i would need to ask on here how to do it.........

---

### Post by grayfox803 on 2008-01-05
ok after diddling more with this, i did figure something out that i still dont understand lol. This is what i have done so far: i went into the synaptic packet manger-did a search for compiz fusion or just compiz, i installed some of the things in there, which in turn, gave me some more options to diddle with, but yet i cant get anything to work, no cool effects at all......

---

### Post by overdrank on 2008-01-05
> **grayfox803 said:**
> ok after diddling more with this, i did figure something out that i still dont understand lol. This is what i have done so far: i went into the synaptic packet manger-did a search for compiz fusion or just compiz, i installed some of the things in there, which in turn, gave me some more options to diddle with, but yet i cant get anything to work, no cool effects at all......

Hi and have you enabled your drivers for you graphics card and what is the model?

---

### Post by grayfox803 on 2008-01-05
Yes the drivers for the graphics card has been enabled, its Nvidia graphics card ii believe its this : NV18 [GeForce4 MX 440 AGP 8x] :) and yes the ouput for the previous is set as YES.

---

### Post by Insomnia777 on 2008-01-05
> **shadow-of-sin said:**
> You should also install compizconfig-settings-manager to allow you to tweak compiz to your liking:
```
sudo apt-get install compizconfig-settings-manager 
```

I just did this but it doesn't install it on the menu but it can be chosen from Appeareance-> Custom... Did I do smth wrong? :S

---

### Post by Insomnia777 on 2008-01-05
Me so noobie lol... restarted and it appeared System-> Preferences -> Andvanced Desktop Effect Settings... thankx ^^

---

### Post by grayfox803 on 2008-01-05
lol i already downloaded that as well.........:guitar:

---

