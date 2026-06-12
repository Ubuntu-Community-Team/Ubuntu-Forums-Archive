---
title: "190 Updates - Fast Way to Do?"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by GregA on 2008-02-26
Have just finished installing my first Ubuntu system.  Looks great so far, but now I seen I have 190 updates.   Is there a fast or easy way to deselect all updates, and then just do a few at a time (as much of the time, I'm on a modem dial-up).   Thanks.

---

### Post by wormser on 2008-02-26
I do not think there is a faster way to deselect them.  Your best bet is wait to update until you can get to a high speed connection.  My recent install took an hour to update with cable internet.  Dial-up would take forever.

---

### Post by Oldsoldier2003 on 2008-02-26
> **wormser said:**
> I do not think there is a faster way to deselect them.  Your best bet is wait to update until you can get to a high speed connection.  My recent install took an hour to update with cable internet.  Dial-up would take forever.

Honestly with that many updates i would be afraid that trying to group them in small batches would lead to dependency nightmares...

---

### Post by shad0w_walker on 2008-02-26
I believe you would have best luck with synaptic (System > Administration > Synaptic)

In synaptic select the Custom filters option (Button near the bottom left of the window) and when you select that you will be given a new set of options in the list above the buttons. From the list you want to select Upgradable, this displays all the packages with updates available. I can't remember if they are all selected by default (Quite possible) but either way, you can mass select entries from there.

To select a group of entries, you can either hold down Shift select the start point and then the end point of the list and it will highlight everything inbetween, or you can hold control Control and select individual packages to highlight.

When you have selected the list of packages you can right click and either mark for upgrade or unmark. All marked packages will be downloaded and updated and all unmarked packages will be ignored.

If you want to select from a point to the bottom of the list, select an item, hold down shift and then press End. That will select from the current item to the bottom of the list.

Good luck. :)

---

### Post by jflaker on 2008-02-26
> **Oldsoldier2003 said:**
> Honestly with that many updates i would be afraid that trying to group them in small batches would lead to dependency nightmares...

Agreed~!

---

### Post by wormser on 2008-02-26
> **Oldsoldier2003 said:**
> Honestly with that many updates i would be afraid that trying to group them in small batches would lead to dependency nightmares...

Great point.

---

### Post by shad0w_walker on 2008-02-26
With synaptic it should automatically select the needed dependencies.

---

### Post by Crafty Kisses on 2008-02-26
> **GregA said:**
> Have just finished installing my first Ubuntu system.  Looks great so far, but now I seen I have 190 updates.   Is there a fast or easy way to deselect all updates, and then just do a few at a time (as much of the time, I'm on a modem dial-up).   Thanks.

I'd just wait and update if I were you.

---

### Post by Origin415 on 2008-02-26
> **Oldsoldier2003 said:**
> Honestly with that many updates i would be afraid that trying to group them in small batches would lead to dependency nightmares...

Shouldnt be a problem, its probably just the random bug/security updates since the release of 7.10, which you would get sporadically normally anyway. As long as stuff like linux-image and linux-headers and such gets updated together (synaptic should automatically group them) itll be fine.

You should only worry about full distribution uprgrades really, ie moving from 7.04->7.10

---

### Post by julian67 on 2008-02-26
Before you update from a new install: uninstall all the apps that you don't want, could save a lot of time with the updates.

---

### Post by GregA on 2008-02-26
Thanks much for your help, I do appreciate it.

I think my best option, because there are so many updates, is to bring this laptop (Lenovo 3000 N100) to my workplace, where they have decent wifi broadband.   I see Ubuntu automatically set up my Intel Pro chipset and my Cisco Aironet card (atheros driver).   That's really nice.   Now, I have to see if there's a painless way to install flash, media codecs, and so on.   Is automatix still an option (not sure about the spelling), or is there another tool to do those updates - if there's a preference as to the current tool or method, I'd like to give it a try tomorrow after doing the security updates.   

GregA

---

### Post by JoshuaRL on 2008-02-26
For the codecs, just go into Add/Remove and get Ubuntu Restricted Extras.  All necessary codecs get installed with that.

Flash is a little bit different according to your version.  32bit (or x86) should be really easy, just download the installer from Apache and use that to get flash.  64bit (or AMDx86_64) needs to use this script [here, which works great.](http://ubuntuforums.org/showthread.php?t=476924)

---

