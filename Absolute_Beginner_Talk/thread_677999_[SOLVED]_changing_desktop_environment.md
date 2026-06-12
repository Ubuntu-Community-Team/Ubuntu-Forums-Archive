---
title: "[SOLVED] changing desktop environment"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by brokenhachi on 2008-01-25
hi, i was looking at other desktop environments and i thought that xfce(?) looked nice, so i was wondering, how can i change the desktop environment..?

---

### Post by UltraMathMan on 2008-01-25
```
sudo apt-get update && sudo apt-get install xubuntu-desktop
``` should do it iirc.

To use xfce after you've installed it:

   1. Log out.
   2. Under Session, select xfce.
   3. Log back in again. 

-Hope this helps :)

---

### Post by brokenhachi on 2008-01-26
cool that worked perfectly. i took a guess and tried kubuntu-desktop and it seems like thats working now! that would give me gnome, xfce and kde correct?

anyways thanks for the help, but i have one more question:

if i decide that i want to delete other desktop environments, how can i do that?

---

### Post by LukeCarrier on 2008-01-26
Just use
```
sudo aptitude remove *name of package you want to remove*
```
Replace the *name of package you want to remove* with the name of the package you installed to get the desktop environment. This will uninstall it cleanly, including any entries in sessions.

---

### Post by LaRoza on 2008-01-26
"kubuntu-desktop" == The entire Kubuntu package (really clutters your menu's)
"kde-core" == A smaller KDE package, that doesn't bring every Kubuntu app along

"xubuntu-desktop" 
"xfce"

Are the same concept too.

---

### Post by brokenhachi on 2008-01-26
when i installed the kubuntu-desktop, like you said it came with everything which isnt what i wanted, now when i boot it boots as kubuntu. so i tried to delete it and it said it did, but then it still boots as kubuntu....   ??

so im just going to reinstall (nothing important on my laptop anyways..)


btw, when i tried:  "sudo apt-get install xfce" it says there is no pack called xfce

another question, would this work for other environments such as enlightenment? i thought that looked cool also.

---

### Post by Jelmoh on 2008-01-26
Easier is to search for the package in the repositories...
(System -> Administration -> Synaptic)
There type KDE/Xfce (whatever which you like! :))

You are not booting to Kubuntu, it's just the Kubuntu start-up screen! :)
It's really annoying, I know.. But nothing harmful! :)
You can probably get it out of there, but you should delete some package that I don't know which one.. :P
So if you liked the install experience you should do that, clean install.. :)
And then install Xfce and/or KDE (not the Kubuntu and/or Xubuntu desktop, this will give you extra programs you said you don't want)

Good luck! ;)

---

### Post by brokenhachi on 2008-01-26
thanks for the help everyone, i think ive got it figure out now. i reinstalled and used synaptic(?) to download enlightenment so im now trying e-gnome which i guess is a mix....? 
anyways it seems cool so far :D 

again, thanks for the help.


p.s. im having some other problems now but i will post another thread about it rather than putting it here.

---

