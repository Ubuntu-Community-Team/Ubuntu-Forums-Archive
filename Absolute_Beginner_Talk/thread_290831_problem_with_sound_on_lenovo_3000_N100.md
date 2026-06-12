---
title: "problem with sound on lenovo 3000 N100"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by gupvineet on 2006-11-01
I'm having problems with sound on my new Lenovo 3000 N100. Whenever I plugin head phones, the sound from internal speakers is still there. So I end up in listening sound from both the speakers; head phones and internal speakers. Please anyone help me in rectifying this problem so that when I plugin head phone I only get sound from it not from both.

---

### Post by thebluesgnr on 2006-11-20
You need to unset the "External Amplifier" option in the sound mixer. It will probably not appear until you enable it in the Preferences dialog.

---

### Post by neocon2005 on 2006-11-21
I was having a great time with edgy but all of sudden there is no sound either from the speakers or the earphones. Any suggestions what might have happened/ how I can diagnose the problem? Thank you.

---

### Post by xp_newbie on 2006-12-07
> **thebluesgnr said:**
> You need to unset the "External Amplifier" option in the sound mixer. It will probably not appear until you enable it in the Preferences dialog.

This is correct, but it needs to be clarified that there are **two** "External Amplifier" in the HDA Intel (Alsa mixer) applet:

The first one, visible by invoking Edit|Preferences menu item, **must be checked** so that...
The second one, now accessible through the newly visible [Switches] tab, must be unchecked to listen to headphones only.

Last thing I know, this bug [has not been resolved yet]("https://lists.ubuntu.com/archives/kernel-team/2006-April/000833.html").

Thanks!
Alex

---

### Post by Deiza on 2007-08-02
> **neocon2005 said:**
> I was having a great time with edgy but all of sudden there is no sound either from the speakers or the earphones. Any suggestions what might have happened/ how I can diagnose the problem? Thank you.
Hi, I venture to ask once again about this problem - some friends of mine told me I have to write somewhere acpi=off - but where?? I would appreciate any help, 10x

:confused:

---

