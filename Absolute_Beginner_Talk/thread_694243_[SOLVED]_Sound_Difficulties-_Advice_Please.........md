---
title: "[SOLVED] Sound Difficulties- Advice Please........."
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Redptc on 2008-02-11
:)
I have intermittant sound problems that seem a bit weird!

I get the sound all organized in Ubuntu and it works fine. However, If I shut down and return later, there is a good chance that my sound will be silent; no drums, no fanfare, nuthing.       :confused:            I then have to go to the sound control Icon, right click and adjust the master and PCM controls just a bit even if it is on full. Then I will get my good sound back. If I shut down again and boot up again my sound is gone again!

That's not a giant problem **[SIZE="3"]but[/SIZE]** if I reboot and go to windows for my accounting program contained therein and subsequently return to Ubuntu..Voila..I have sound! :KS

Why does my sound(in Ubuntu) come on immediately after I have used windows but not after I have used Ubuntu?

It sounds like something is being shut down in Ubuntu that isn't being shut down when Windows closes!

Any ideas?:redface:[COLOR="Red"]Redptc[/COLOR]

---

### Post by Jewfro_Macabbi on 2008-02-12
Once you have your volume controls set to your liking, try this:

sudo alsactl store

This should save your settings permanently.

---

### Post by BlackLuna on 2008-02-12
I think I have same problem. But, it's different from **Redptc**.
When I turn my laptop on and directly go to Ubuntu, all sound work fine. :KS
Then I reboot it (without turn it off), then I go to windows. All sound work fine too.

Here is the problem,
If I turn my laptop and go to windows, I have sound. Everything running well.
Then I reboot it  (without turn it off), then I go to Ubuntu. My Ubuntu is SILENT. No sound when login window. No welcome sound. When I check my volume control, it's already full. :confused:And I dont change any setting related to sound since I installed ubuntu.

If I want to get sound back. I have to turn my laptop first, then turn it on and go to ubuntu directly.

anybody knows what happen with my ubuntu?

here is my laptop specification:
Compaq Presario V3628TU. She equipped with** Altec Lansing Speaker**. In windows, she uses **Conexant High Definition driver**.

Thanks before.

---

### Post by Redptc on 2008-02-12
> **Jewfro_Macabbi said:**
> Once you have your volume controls set to your liking, try this:

sudo alsactl store

This should save your settings permanently.

:lolflag: 

You beauty mate!!! Yew did it, thanks for you help!


:redface:    Redptc

---

### Post by Redptc on 2008-02-12
> **BlackLuna said:**
> I think I have same problem. But, it's different from **Redptc**.
When I turn my laptop on and directly go to Ubuntu, all sound work fine. :KS
Then I reboot it (without turn it off), then I go to windows. All sound work fine too.

Here is the problem,
If I turn my laptop and go to windows, I have sound. Everything running well.
Then I reboot it  (without turn it off), then I go to Ubuntu. My Ubuntu is SILENT. No sound when login window. No welcome sound. When I check my volume control, it's already full. :confused:And I dont change any setting related to sound since I installed ubuntu.

If I want to get sound back. I have to turn my laptop first, then turn it on and go to ubuntu directly.

anybody knows what happen with my ubuntu?

here is my laptop specification:
Compaq Presario V3628TU. She equipped with** Altec Lansing Speaker**. In windows, she uses **Conexant High Definition driver**.

Thanks before.

Look at this thread it may help sort things out.[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) If it doesn't I suggest you open a new thread so you will get specific attention to your unique problem.

You will get help!

Good Luck! :redface:[COLOR="Red"]Redptc[/COLOR]

---

### Post by BlackLuna on 2008-02-12
Thanks Red

I'll read about it.

---

