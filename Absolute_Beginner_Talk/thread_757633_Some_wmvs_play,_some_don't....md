---
title: "Some wmvs play, some don't..."
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by Will Walshe on 2008-04-17
Hi guys

I've  installed the ubuntu restricted extras package, and I now have a situation where I'm able to play some .wmv files but not others.

Pulling up a properties tab, I see that the ones I can play use the Windows Media 8 codec, while the ones I can't seem to require a codec called "microsoft windows media advanced profile". Is this codec available for ubuntu?

---

### Post by scorp123 on 2008-04-17
> **Will Walshe said:**
>  I've  installed the ubuntu restricted extras package, and I now have a situation where I'm able to play some .wmv files but not others.  I'd recommend the Medibuntu repos. Please read here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

They have restricted video codecs (which were reverse-engineered from Windows it seems so Ubuntu can't ship with them "out of the box") in their repos which help a great deal to get more formats working, e.g. these packages: **non-free-codecs**  and  **w32codecs** ... Install those packages and then try again please.

---

### Post by aeiah on 2008-04-17
bare in mind that if the wmv is DRM 'protected' that you wont be able to play it. i dont know if this is the case though here

---

### Post by Will Walshe on 2008-04-17
Aye, I added the medibuntu repository previously and installed the w32codecs package from it. 

Typing ```
sudo apt-get install non-free-codecs
``` gets me an error message saying ```
E: Couldn't find package non-free-codecs
```.

Have I got the name of the package wrong, or have I messed up adding the repository?

---

### Post by t3hi3x on 2008-04-17
> **Will Walshe said:**
> Aye, I added the medibuntu repository previously and installed the w32codecs package from it. 

Typing ```
sudo apt-get install non-free-codecs
``` gets me an error message saying ```
E: Couldn't find package non-free-codecs
```.

Have I got the name of the package wrong, or have I messed up adding the repository?

If you're not getting an error when updating the repositories, you should have the repostitories in there.

Maybe look through Synaptic to see if you can find them there.

---

