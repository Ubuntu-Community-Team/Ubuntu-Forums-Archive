---
title: "terminal"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by jcrnan on 2006-09-24
Ive put my terminal to having a transparent background but only goes transparent to the desktop backgroun. Meaning all apps are ignored, only background shows in the transparency. Any tips on how to fix that?

---

### Post by henriquemaia on 2006-09-24
As far as I know, Xorg does not have real transparency, only a "fake" one. That's why you have that. To achieve real transparency effect, you have to use XGL.

---

### Post by skymt on 2006-09-24
The latest version of GNOME Terminal supports real transparency when used with an accelerated X server, like XGL or AIGLX. So, just wait a couple weeks for Edgy, which will have everything you need.

---

### Post by jcrnan on 2006-09-24
I already run AIGLX so is there any way I can just update to the latet gnome terminal?

---

### Post by skymt on 2006-09-25
> **jcrnan said:**
> I already run AIGLX so is there any way I can just update to the latet gnome terminal?

I don't think so. It's part of GNOME 2.16, so upgrading it would (without lots of hacking) require upgrading the rest of GNOME (library issues, mostly).

Just wait a couple of weeks, or upgrade to Edgy now. It seems to be getting pretty usable.

---

