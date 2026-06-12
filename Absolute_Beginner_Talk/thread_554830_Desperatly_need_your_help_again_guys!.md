---
title: "Desperatly need your help again guys!"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by HawkST on 2007-09-19
Hey guys, I'm a Ubuntu newbie-ish, I have it installed on my PC, and needed to install it on my new laptop before I go to Uni (Windows doesn't recognize my 250GB USB Drive!), all has worked fine, except there is no sound! It's is a dual boot with Vista, which has sound.

Also, when I go to Uni I will have no internet for at least 2/3 weeks and really need it working before then!

Running 'lspci' told me my audio device is "ATI Technologies Inc SB540 HDA Audio (rev 01)"

The sound is not muted or anything like that..

I would be extremely grateful of any help! Thanks!

---

### Post by CaptainInsaneO on 2007-09-19
You need to go into "Volume Control" or "Sound" (can't remember which, my Ubuntu machine is out of commission for now) and change your device (that is, if you have another sound card). I have this problem whenever I reinstall because the onboard sound defaults, and I have to change my device in Volume Control to my PCI soundcard. Also, try disabling onboard sound in your BIOS.

---

### Post by sailor2001 on 2007-09-19
in synaptic: search alsa (base) and oss

---

### Post by notwen on 2007-09-19
You may also want to make sure all of your volumes are extremely low, which tends to happen with new installs.  Open up a terminal and type in "alsa-mixer" and this will bring up a screen where you can adjust your default volume settings, simply press ESC to exit.  Hope this helps. =]

---

### Post by HawkST on 2007-10-14
hey guys, sorry to bring up an old thread again, but I've just got my internet back and I don't have sound on my Ubuntu, still!
I tried all the things above but so far, no luck. Is there anything else I could try? Someone mentioned a new flavour (?) or Ubuntu thats being released soon (or may be out already), would installing that help do you think? Or, is there anywhere where I could check if my sound card is compatible, or how I could get drivers or something?

---

### Post by HermanAB on 2007-10-14
When all else fails, go to the ALSA project web site and start reading.

---

### Post by MatthewPlanchard on 2007-10-14
What kind of laptop are you using? I had the same problem on my Toshiba A135-S2246 and was able to fix it with the advice in this thread:
[http://ubuntuforums.org/showthread.php?t=473425&highlight=toshiba+sound]("http://ubuntuforums.org/showthread.php?t=473425&highlight=toshiba+sound")

---

