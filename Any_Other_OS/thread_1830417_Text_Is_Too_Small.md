---
title: "Text Is Too Small"
date: 2011-08-21
forum: Any Other OS
---

### Post by Kozar on 2011-08-21
So, really weird issue going on with Mint ever since I hooked my comp up to this 32" tv to act as a monitor. With having this bigger screen resolution, the text size on all the menus, programs, web browsers, etc. have gotten so small. Small enough to the point I have to lean in really close to try and make sense of what I'm reading that it is just abusive to the eyes.


My first attempt to remedy this was adjusting the screen resolution. It had me set at 1366x768. The next step down was 1360x768 and that resulted in an even more difficult to read view on account that the screen was squeezed up into a square display. The next step down from that was 960x540.

I've looked all over the different settings menus from display settings to preferences.

Is there some way to change the system font size?

---

### Post by mips on 2011-08-21
1. Set your resolution to the TV's native resolution.
2. Increase your font size.

You don't say which version of Mint you are using etc so I'm not going to bother with any more info as it could be irrelevant.

---

### Post by Kozar on 2011-08-21
> **mips said:**
> 1. Set your resolution to the TV's native resolution.
The native resolution for it in RGB mode is 1366x768

> **mips said:**
> 
2. Increase your font size.

That's what I'm trying to figure out how to accomplish.

> **mips said:**
> 
You don't say which version of Mint you are using etc so I'm not going to bother with any more info as it could be irrelevant.

Linux Mint 9, codename Isadora. LXDE version.

---

### Post by mips on 2011-08-22
> **Kozar said:**
> The native resolution for it in RGB mode is **1366x768**

Ok, set your resolution to 1366x768 then.


> **Kozar said:**
> 
That's what I'm trying to figure out how to accomplish.

Linux Mint 9, codename Isadora. **LXDE version**.

Seeing it's LXDE it uses Openbox & GTK+ stuff. To change your fonts and other desktop related stuff you have to use ObConf & LXAppearance. I dunno what they are called in mint lxde or where they are hidden in the menus but you can always launch them from a terminal with the **obconf** & **lxappearance** commands, you have to set the font in both of them.

If those two utils are not installed then I suggest you install them.

---

