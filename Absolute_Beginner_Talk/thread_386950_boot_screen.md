---
title: "boot screen"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by sohaibma on 2007-03-17
i installed edubuntu artwork and splash screen on my ubuntu 6.10 for trial, through synaptic.
I didnt like it so i removed it. every thing was removed except the splash screen (boot screen). how do i revert back to the default ubuntu 6.10 splash screen.

---

### Post by dmsynck on 2007-03-17
This should do the trick.

```
sudo update-alternatives --config usplash-artwork.so
```

Then just select the number of the one you want to use.

---

### Post by sohaibma on 2007-03-18
I think I confused you, I was asking about changing the boot screen (boot loader), the screen that comes up before the login screen.
please tell me how to change that.

---

### Post by dmsynck on 2007-03-18
Yes, I understand that you are talking about the boot splash. This is the command for changing to a different boot splash. Provided, of course that the boot splash in question is installed.

---

### Post by sohaibma on 2007-03-19
I executed the command but it was unable to find any other screens. Do you know where i can get and how i can install the ubuntu default boot screen again? (i really hate the edubuntu boot screen):(

---

### Post by Jormanks on 2007-03-20
> **dmsynck said:**
> Yes, I understand that you are talking about the boot splash. This is the command for changing to a different boot splash. Provided, of course that the boot splash in question is installed.

Are There only two available?

---

### Post by Mr. Nefarius on 2007-03-30
**[COLOR="Red"]dmsynck[/COLOR]** saved the day!  I'd been doing much tweaking on themes, splashes & beryl...my boot splash managed to end up falling to the poor "edubuntu" boot splash. 

> **dmsynck said:**
> This should do the trick.

```
sudo update-alternatives --config usplash-artwork.so
```

Then just select the number of the one you want to use.

worked for me in Edgy 6.11

...thanx :guitar:

---

### Post by ivoencarnacao on 2007-04-12
> **dmsynck said:**
> This should do the trick.

```
sudo update-alternatives --config usplash-artwork.so
```

Then just select the number of the one you want to use.


This worked fine for the usplash, but the edubuntu splash and the edubuntu gdm theme are still there, as for the gdm theme i have tried through System - Administration - Login Window but it didnt worked!

Any clues on how to restore the default ubuntu splash and gdm theme but leaving the edubuntu artwork (icons & window colors) ?


Thanks!
Ivo.

---

