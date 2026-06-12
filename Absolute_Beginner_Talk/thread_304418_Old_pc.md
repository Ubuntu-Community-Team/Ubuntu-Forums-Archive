---
title: "Old pc"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by japc126 on 2006-11-21
I have an extremly old pc. How can I make it boot from the cd? The only key that I have tried is delete, and it makes a bunch of windows 98 startup options appear

---

### Post by LLRNR on 2006-11-21
Wow... it depends on the PC, really. If it's set to "quiet boot" (I think this is how it's called) you won't see a "Type xyz to enter settings..." at boot time, but it MUST HAVE a BIOS somewhere !

Just try hitting random keys, sorry it sounds stupid, I know, but some PCs need the DEL key (right at boot time), others F1, others ESC... my PC (with a BIOS provided by Compaq) needs F10 key to be pressed, for instance.

Be sure to tap the same key each time you try to boot (before seeing the "loading win98" stuff), and if it's not the correct key... patiently reboot and repeat sequence until you strike the right key. :mrgreen: (Then just choose CD as first boot option.)

Good luck and CALM !

---

### Post by alienexplorers on 2006-11-21
I'm running on a old AMD K6-III 450 system with 384MB memory and 30 GB Hard Drive and ATI ALL IN WONDER video card and the software provided by ubuntu runns great.  A Bit slow due to my processor and 100 MB FSB but, it is very usable.  I am not running any version of windows with this just Ubuntu Linux.

---

### Post by japc126 on 2006-11-21
At least does somebody has a list of keys not to try? I doubt it is set for the a key for example...

---

### Post by DirtDawg on 2006-11-21
> **alienexplorers said:**
> I'm running on a old AMD K6-III 450 system with 384MB memory and 30 GB Hard Drive and ATI ALL IN WONDER video card and the software provided by ubuntu runns great.  A Bit slow due to my processor and 100 MB FSB but, it is very usable.  I am not running any version of windows with this just Ubuntu Linux.

I suggest you try [Xubuntu]("http://www.xubuntu.org/") sometime. You'll find it runs much faster.

```
 sudo aptitude xubuntu-desktop 
```
Then change "Session" to XCFE(or Xubuntu) on the login screen.

EDIT: Also try [Sylpheed-Claws]("http://www.sylpheed-claws.net//") instead of Thunderbird. It's in Synaptic and runs like a champ.

---

### Post by DirtDawg on 2006-11-21
> **japc126 said:**
> At least does somebody has a list of keys not to try? I doubt it is set for the a key for example...

It's F12 on mine. Do you plan to keep your Windows partition around?

---

### Post by confused57 on 2006-11-21
> **japc126 said:**
> At least does somebody has a list of keys not to try? I doubt it is set for the a key for example...
  As someone already mentioned, "del", "esc", or could be any of the "F" keys...F1,F2,etc.

  Many old computer bios do not have an option to boot first from the cd drive...if this is the case, you might want to look into making a Smart Boot Manager floppy:

[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

---

