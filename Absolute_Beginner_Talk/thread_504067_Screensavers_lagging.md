---
title: "Screensavers lagging?"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by Hybrid86 on 2007-07-18
I recently installed ubuntu, and my screensavers seem to either lag horribly or not work at all (blackness and or random colors)
I have a Dell laptop inspiron 8600 with a GeForce FX Go5200 graphics card, 512mb or ram, and a pentium M processor. Beryl and Emerald both run absolutely fine.

---

### Post by nitro_n2o on 2007-07-18
Ubutnu comes with Random screen savers by default and maybe the screen saver style is slow... so if you go to System->preferences->Screensaver choose some screensaver and preview it. the first one should be fast.. if not then you have a problem!! but i'm sure its solvable

---

### Post by Hybrid86 on 2007-07-18
I'm sorry, I should have specified more clearly.

When I select any screensaver, it previews fine in the little window to the right. When I click "preview" to see it in fullscreen however, _that's_ when the problem occurs.

---

### Post by ubanchaos on 2007-07-18
o i c well does it do that on all your screen savers

---

### Post by Hybrid86 on 2007-07-18
The only one that runs is "galaxy".

---

### Post by RomeReactor on 2007-07-18
Hi. Try disabling Beryl and run the screensaver fullscreen then. It may be due to the 512 MB RAM and your GeForce card not being able to run them both at the same time (some screensavers are 3D).

---

### Post by Hybrid86 on 2007-07-18
I've actually had this problem since the beginning; before I installed beryl.

---

### Post by Hybrid86 on 2007-07-21
Anyone?

---

### Post by benx009 on 2007-07-21
does doing "glxgears" give u satisfying framerates?  if it does, then maybe this yours is a software problem, not hardware...

---

### Post by acowboydave on 2007-07-21
Hello, could be your driver, the wrong one installed, Google what card you have, specify ubuntu. There is a few related articles there similar to yours. Meaning driver for your graphic card.

---

### Post by koganinja89 on 2007-07-21
> **acowboydave said:**
> Hello, could be your driver, the wrong one installed, Google what card you have, specify ubuntu. There is a few related articles there similar to yours. Meaning driver for your graphic card.

FoSho'izy

or your card has crap for openGL support doubt it though.

---

### Post by Hybrid86 on 2007-07-23
Just updated my drivers with envy. Still have the problem though

---

### Post by philter on 2007-07-23
What kind of framerates are you getting out of glxgears?

---

### Post by Hybrid86 on 2007-07-24
> **philter said:**
> What kind of framerates are you getting out of glxgears?
Runs fine in the demo, but doesn't run at all when previewed.

---

### Post by RomeReactor on 2007-07-24
What do you mean? Post the output of
```
glxinfo | grep rendering
```
and also
```
glxgears
```
let it run for a while, until it prints about five lines in the terminal. Make sure you don't minimize the gears screen or hide it behind another window.

---

### Post by lemonseed on 2007-07-24
I had the same problem when I first installed Ubuntu. After enabling the NVidia drivers in System > Administration > Restricted Drivers Manager they all worked fine.

---

### Post by Hybrid86 on 2007-07-25
> **RomeReactor said:**
> What do you mean? Post the output of
```
glxinfo | grep rendering
```
and also
```
glxgears
```
let it run for a while, until it prints about five lines in the terminal. Make sure you don't minimize the gears screen or hide it behind another window.
"glxinfo | grep rendering" yeilded:
```
direct rendering: Yes
```
running glxgears yeilded:
```
2695 frames in 5.0 seconds = 538.352 FPS
2626 frames in 5.0 seconds = 525.183 FPS
2610 frames in 5.0 seconds = 521.856 FPS
2659 frames in 5.0 seconds = 531.786 FPS
2758 frames in 5.0 seconds = 551.068 FPS
2667 frames in 5.0 seconds = 533.219 FPS
2676 frames in 5.0 seconds = 534.177 FPS
```
> **lemonseed said:**
> I had the same problem when I first installed Ubuntu. After enabling the NVidia drivers in System > Administration > Restricted Drivers Manager they all worked fine.
Restricted drivers are enabled.

---

### Post by RomeReactor on 2007-07-25
You're getting very low framerates. How much RAM does your GeForce card have? is it using shared memory from your system's 512? If your card has 128 MB or less (or it's using shared memory), and if you have Beryl running while the screensavers appear, that would probably explain it: neither Beryl or Compiz are smart enough (yet) to disable themselves when a full screen 3D application runs, so your card is trying to run Beryl plus the 3D application at the same time (some screen savers are 3D).

---

### Post by Hybrid86 on 2007-07-26
I beleive the GeForce FX Go5200 only has 128mb of ram, but this was a problem since before I even installed beryl. Assuiming ram *is* the issue though, would simply getting more ram solve this whole issue?
3d games like neverball and chromium lag, but at least they work, unike the screensavers which remain blank in full screen mode.

EDIT: When I disabled beryl, Everything ran fine. weird. Is there a way to make beryl disable itself when a screen saver is running or something? And again, would getting more ram solve this issue entirely?

---

### Post by RomeReactor on 2007-07-26
> **Hybrid86 said:**
> I beleive the GeForce FX Go5200 only has 128mb of ram, but this was a problem since before I even installed beryl. Assuiming ram *is* the issue though, would simply getting more ram solve this whole issue?
It would help, though it wouldn't solve the problem completely.
> When I disabled beryl, Everything ran fine. weird. Is there a way to make beryl disable itself when a screen saver is running or something? And again, would getting more ram solve this issue entirely?
I don't think there is a way to make Beryl (or Compiz) disable themselves yet. As for the RAM issue, if you want to run Beryl comfortably, yes, you would need more RAM, and probably a more recent video card, possibly from the GeForce 6 line; I have a GeForce 6200 with 256MB RAM, 1 GB system RAM, and it runs fairly well, if that is anything to go by.

---

