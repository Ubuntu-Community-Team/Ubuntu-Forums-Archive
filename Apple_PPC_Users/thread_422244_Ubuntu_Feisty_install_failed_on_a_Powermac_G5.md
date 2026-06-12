---
title: "Ubuntu Feisty install failed on a Powermac G5"
date: 2007-04-25
forum: Apple PPC Users
---

### Post by Kepesk on 2007-04-25
Okay, I went ahead and installed a fresh copy of feisty on my Powermac G5 dual 1.8 using the alternate install CD, but it didn't work!  The install went through okay, and I restarted, and got the fancy Ubuntu loading screen with no apparent errors, but ehrn the progress bar went to the top, the screen went blank with nothing but a frozen cursor (just the horizontal line at the top, but always on).

Has anyone else had this happen to them?

Thanks!

---

### Post by didg on 2007-04-25
Can you try to boot with nosplash?

---

### Post by Kepesk on 2007-04-25
How would one go about doing that?

(Sorry, I've only been working with this for a week, so I suppose I'm still a bit of a noob, so to speak)

---

### Post by didg on 2007-04-26
I had a closer look and If you can't change a file is not obvious :(

What you can try:
1) At the boot second stage (when you see yaboot ...)
type :
Linux debug

2) use the liveCD, again at the second stage 
type:
live-nosplash-powerpc64 debug

At least you'd see where it breaks, there's known issues with graphic cards and maybe sound.

---

### Post by stmiller on 2007-04-27
Yeah, press 'tab' at the boot screen to see the different options, on the alternative cd.

---

