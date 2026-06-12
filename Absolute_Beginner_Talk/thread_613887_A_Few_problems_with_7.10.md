---
title: "A Few problems with 7.10"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by GeorgiaBoot on 2007-11-15
I decided to give 7.10 a try and upgraded via the internet. Everything went smoothly. The problem is I  have enable so compiz does the cube. When I rotate the cube it looks fine but when I come to one of the workspaces if there is lets say Firefox up it gets all garbled. But when I click on firefox all the garbled look goes away. Is this because the graphics are a wee to high for my system? Is there any settings I can make so just the cube works and all the other mumbo-jumbo is not on?

Next when I am running rythmbox for music it gets garbled allot when I try to move the window. How can I fix this?

Thanks

---

### Post by JawsThemeSwimming428 on 2007-11-15
What are your machine specs? (Graphics, Sound, Processor, Memory, Motherboard, etc.)

---

### Post by GeorgiaBoot on 2007-11-15
Pentium 4 with HT @3.00ghz, 3gb of ram, ati radion x300 128mb, integrated sound.


Thanks

---

### Post by ajgreeny on 2007-11-15
Your specs should work OK.  Video driver?  I use the OS ati driver with my radeon 9200SE and it works great.  I'm sure you can set the compiz-settings-manager to use the cube without all the animations etc, so just try various combinations and see what happens.

---

### Post by Inxsible on 2007-11-15
gutsy doesn't come with ccsm pre-installed.you can install it by ```
sudo aptitude install compizconfig-settings-manager
``` and then after installation you can find it under System>>Preferences>>Advanced Desktop Effects Manager

---

### Post by GeorgiaBoot on 2007-11-15
Strange when I go to 

System>Preferences>Appearance 

All of Compiz is there. Or is this something else I need? Sorry I am wee lost.

Thanks

---

### Post by Inxsible on 2007-11-15
did you install the ccsm yet ?

---

### Post by GeorgiaBoot on 2007-11-15
Why would I install it if when I go to appearance all of compiz config is there? I am just confused, I think  it is already installed since I upgraded to gutsy gibbon. Sorry

---

### Post by Inxsible on 2007-11-15
> **GeorgiaBoot said:**
> Why would I install it if when I go to appearance all of compiz config is there? I am just confused, I think  it is already installed since I upgraded to gutsy gibbon. Sorrywhat do you mean all of compiz is there ? In the Appearance menu, you can only enable/disable compiz

once you install the settings manager, you will see there are a lot more plugins that you can use.

---

### Post by GeorgiaBoot on 2007-11-15
When I go to 
appearance>visual effects>Custom>Preferences

Compiz Config Settings manager comes up. I am able to change a whole bunch of stuff. Is that what you are talking about or is this something else? Basically I was wondering if I could have the bare effects of the cube and not have all this glitching. Or if there is some way to get around it. Thanks for your time.

---

### Post by Inxsible on 2007-11-15
> **GeorgiaBoot said:**
> When I go to 
appearance>visual effects>Custom>Preferences

Compiz Config Settings manager comes up. I am able to change a whole bunch of stuff. Is that what you are talking about or is this something else? Basically I was wondering if I could have the bare effects of the cube and not have all this glitching. Or if there is some way to get around it. Thanks for your time.
Yes its the same. it means that you have already installed CCSM.

So are you saying that you dont have the System>>Preferences>Advanced Desktop Effects Settings option at all ?

---

### Post by GeorgiaBoot on 2007-11-15
Nope I don't have that. I can only go to appearance and change stuff.

---

### Post by Inxsible on 2007-11-15
interesting. For me without installing ccsm, I cannot access the settings at all.

---

### Post by ajgreeny on 2007-11-17
Just for clarity, look in synaptic for compizconfig-settings-manager to see if it is installed.  If you didn't install it yourself, then it shouldn't really be installed at all, but it does sound as if it is there.  The question is, why dont you have the System>>Preferences>Advanced Desktop Effects Settings option in the menu as well as Appearance?

---

### Post by brownknight on 2007-11-17
When you go to System > Preferences> Appearance and go to the Visual Effects tab, do you have 4 choices there? none, normal, extra and custom? If yes, click on custom and try different combinations and see if anything will improve your cube.

---

