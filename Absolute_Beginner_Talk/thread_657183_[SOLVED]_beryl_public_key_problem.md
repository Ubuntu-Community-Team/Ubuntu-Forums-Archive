---
title: "[SOLVED] beryl public key problem"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by Phil420 on 2008-01-03
I've tried for a long time now to install beryl but it doesn't work. i checked out this link: [http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)
and it helped a bit, but when i want to quit the software sources after entering the repo, this pops out and tells me no public key was found...

[IMG]http://i263.photobucket.com/albums/ii146/420phil/errorpubkey.png[/IMG]

i read that it was ignorable but... it doesn't work..?

---

### Post by overdrank on 2008-01-03
HI and first off that is for edgy and I assume you are using gutsy that has compiz installed. But did you run the key in the terminal that was referenced ```

wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```

---

### Post by Goop on 2008-01-03
If you're using Gutsy and want all of those fancy features in Beryl, such as Desktop Cube and window animations, try installing Compiz advanced settings from Add/Remove programs (sadly I am on I windows PC right now, so I can't check the exact name. The short name is CCSM). From there you can change all the settings of your desktop effects.

---

### Post by Phil420 on 2008-01-03
yea i did that thing. i'm so confused i just need a nice cube background and it turns out to be so complicated...

---

### Post by Phil420 on 2008-01-03
yea i went in compiz thing and changed all those things to rotating cube and all... and it hasn't changed at all :(

---

### Post by overdrank on 2008-01-03
> **Phil420 said:**
> yea i did that thing. i'm so confused i just need a nice cube background and it turns out to be so complicated...

HI and have you enabled the desktop effect under system, preference, appearance. Then the effects tab. Have you enable the driver for you graphics card and what is the model?

---

### Post by Phil420 on 2008-01-03
> **overdrank said:**
> HI and have you enabled the desktop effect under system, preference, themes. Then the effects tab. Have you enable the driver for you graphics card and what is the model?

i tried the system, preference, themes thing.. and it didn't work. mainly because there was no "themes" in preferences. haha sorry if i'm mistaking or something i'm new to this and it really annoys me. I really don't find what you tell me and haha it kinda makes me laugh but emm i have a ATI radeon 1650 plus i think but now that you've mentioned i didn't install it on ubuntu... haha okay let me some time i'll finally come to an end someday.. i'll restart from the beginning and do the correct things. i'll aks if i need more help after that.. thanks

---

### Post by overdrank on 2008-01-03
> **Phil420 said:**
> i tried the system, preference, themes thing.. and it didn't work. mainly because there was no "themes" in preferences. haha sorry if i'm mistaking or something i'm new to this and it really annoys me. I really don't find what you tell me and haha it kinda makes me laugh but emm i have a ATI radeon 1650 plus i think but now that you've mentioned i didn't install it on ubuntu... haha okay let me some time i'll finally come to an end someday.. i'll restart from the beginning and do the correct things. i'll aks if i need more help after that.. thanks

HI and you are correct my mistake, I was on feisty at the time of responding. :oops: I have edit my previous post. And you have not installed Ubuntu yet so you are working from the live cd?

---

### Post by ~LoKe on 2008-01-03
If you're running the LiveCD, you shouldn't be able to use the desktop effects until enabling the restricted driver?

---

### Post by oldos2er on 2008-01-03
You're lookiing for System, Preferences, Appearance, Visual Effects.

---

### Post by Phil420 on 2008-01-03
> **overdrank said:**
> HI and you are correct my mistake, I was on feisty at the time of responding. :oops: I have edit my previous post. And you have not installed Ubuntu yet so you are working from the live cd?

nah nah nah i have installed ubuntu, just not the graphic card yet. but i have now, i just have to restart my pc

---

### Post by Phil420 on 2008-01-03
> **oldos2er said:**
> You're lookiing for System, Preferences, Appearance, Visual Effects.

lol talking about the visual effects... is it normal that they don't work? i tried each of them and a message poped up saying it couldn't be enabled... ??

---

### Post by ~LoKe on 2008-01-03
> **Phil420 said:**
> lol talking about the visual effects... is it normal that they don't work? i tried each of them and a message poped up saying it couldn't be enabled... ??

You need to enable the restricted driver in order to have direct rendering (which compiz requires).

---

### Post by Phil420 on 2008-01-03
> **~LoKe said:**
> You need to enable the restricted driver in order to have direct rendering (which compiz requires).

I enabled the restricted driver... and now another message pops and says the Composite extention is not available... what does that mean?

---

### Post by ~LoKe on 2008-01-03
Try adding this to the end of /etc/X11/xorg.conf:
```
Section "Extensions"
        Option          "Composite"     "Enable"
EndSection
```

---

### Post by overdrank on 2008-01-03
> **~LoKe said:**
> Try adding this to the end of /etc/X11/xorg.conf:
```
Section "Extensions"
        Option          "Composite"     "Enable"
EndSection
```

HI and forgive me if I am wrong but I thought ati was compsite 1
  Option          "Composite"     "1"
:confused:

---

### Post by ~LoKe on 2008-01-03
> **overdrank said:**
> HI and forgive me if I am wrong but I thought ati was compsite 1
  Option          "Composite"     "1"
:confused:

Damn it.  Used to nVidia didn't even think of it.  Yes, I think you're right.

---

