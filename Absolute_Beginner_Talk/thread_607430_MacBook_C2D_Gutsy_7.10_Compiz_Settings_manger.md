---
title: "MacBook C2D Gutsy 7.10 Compiz Settings manger???"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by RIDE on 2007-11-08
I have installed 7.10 on my MacBook C2D, and I believe I have installed Compiz-Settings-Manager through the Terminal...

BUT.. when I go to System>>>Preferences>>>    I do not have "Advanced Appearance Preferences"...    Also within System>>>Preferences>>> Appearance>>> Visual Effects Tab, I do NOT have a "Customize" or "Preferences" button before or after clicking "Extra"...

Please help me....   I am trying to figure out how to do the visual effects/settings.

Any help would be greatly appreciated.

---

### Post by bharris25 on 2007-11-09
Make sure you have all of the plugins downloaded and there is 2 different gui for the adjustment of the visual effects one more user friendly than the other, you can also try uninstalling and reinstalling.  And also does your extra effects work?  If it does it's probably a plugin thing.

You might want to try installing Compiz with Synaptic if you can it's probably easier and that's how I did it.

---

### Post by rundee_f on 2007-11-09
Try to install CCSM from Synaptic...

---

### Post by RIDE on 2007-11-09
Thank you both...

It was a plugin issue...   I know have the Advanced Effects in Preferences.

What is the default key command to use the Desktop Cube???  I am on  a Mac keyboard.

Also, how do I add additional desktops...  instead of just 2?

Thanks again.

---

### Post by dhobbs on 2007-11-09
Look under the General Settings for the number of desktops.

Rotating the cube (I think) is Ctrl+Alt+ left click and drag or right/left arrow.  Ctrl+Alt+Up arrow will unfold the cube.  That's at least what my machine defaulted to.

P.S. make sure you have the rotate cube plugin enabled or you can't rotate.

---

### Post by ginistheman on 2007-11-10
Hi everyone - I'm having the same problem. I can't get the ADVANCED DESKTOP SETTINGS option to appear in my preferences.

When I go into Synaptic and I type in compiz config into search, the two entries it returns show a green box (indicating they are already installed?). 

The user above mentioned it was a plugin problem - can anyone give me a step by step on how to rectify the problem? Sorry I'm a total newb :D

---

### Post by TadH on 2007-11-10
yes
sudo ap-get install ccsm should work fine

---

### Post by ginistheman on 2007-11-10
> **TadH said:**
> yes
sudo ap-get install ccsm should work fine

I've typed that in literally and it didn't work.

Should it be sudo apt as opposed to ap?

And can type in ccsm or do I have to type in compizconfig-settings-manager?

Also should I remove the compiz that is installed at the moment first? If so, what is the best method to do this?

---

### Post by DutyDuty on 2007-11-10
It should be apt-get, not ap-get. For copy-paste, here: ```
sudo apt-get install ccsm
```
Type ccsm, not the long thing. 
It should be fine, if it is not, ```
sudo apt-get update
then
emerald --replace
```

---

