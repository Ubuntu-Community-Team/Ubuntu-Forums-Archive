---
title: "Computer won't start after Ubuntu shutdown"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by Roaster on 2007-09-07
Hello, I asked about this awhile back and have still not found a definitive answer. I'll ask again in the hope that somebody out there will know how to fix this. I have Windows XP Pro and Ubuntu dual booting on a built computer using Asus P5N32 SLI SE Deluxe motherboard. When I shutdown in Ubuntu 7.04 the computer will not power up when I try to start it. I have to unplug and replug the computer to get it to power up. If I shutdown from Windows XP the computer powers up with no problem. I suspect some setting in the BIOS but I do not know what it is. Anyone? Thanks in advance and best regards to all.

---

### Post by oilchangeguy on 2007-09-07
enter the bios, make notes about the settings. then restore the default settings. and see if anything changes.

---

### Post by banewman on 2007-09-07
This is a best guess sort of reply so please take it as that. Your mboard is pretty new which means the linux developers haven't had much time to get all things sorted out, The next kernel upgrade should have it sorted if they are still on form, but as a test, what happens if you try to restart instead of shutting down?

---

### Post by Roaster on 2007-09-07
Hi, the computer restarts OK. It's only when I do a 'cold' start that this happens. I have had all the settings set to default in the bios and have tried different settings with the same result. BTW the bios is flashed to latest update. It's not a big deal but as I'm using Ubuntu more now than Windows it's a pain to restart and shutdown in Windows in order to keep from doing the unplug routine. As you said maybe the Gutsy will fix this. Thanks

---

### Post by aaabbb on 2007-09-24
I, for one also have an ASUS a8n32-sli deluxe, and i have a slightly different problem. I had been dual booting ubuntu and XP, but xp crashed and i don't use that hdd anymore. Well, come to find out, after installing an IDE hdd, and loading XP, it worked fine for ahwile. Well, i shut it off on time a few days ago, and now it won't turn on all of the way. 
1. it will not produce a video signal
2. it used to make a beeping noise, and now it doesn't
3. it will not go into bios

I am starting to thinki have fried another $$$ computer..........
i know my problem does not relate to yours, but maybe it will put another perspective on things. plz and thx in advance.

---

### Post by lisati on 2007-09-24
Just wondering: One thing that came to my attention recently is that with some BIOSes and some flavours of *ubuntu, doing a "shutdown" doesn't always power off the computer completely - perhaps what you're experiencing is related. A symptom of this is the light on your mouse staying on. I'm not sure of the solution however.....

---

### Post by splintercellguy on 2007-09-24
Accidental standby?

---

### Post by Roaster on 2007-09-24
I don't know if this has anything to do with this problem but when booting a message flashes momentarily on the screen about an 'MP bios bug 8254 timer not connected to ACPI' or something to that effect. I'm sure it's a bios problem that only the bios maker can address. In that case American MegaTrends. Thanks for your interest. The computer does shutdown all the way from Ubuntu but I haven't checked to see if the mouse light is still on:).I'll check that the next time I shutdown.

---

### Post by splintercellguy on 2007-09-24
Could be an ACPI thing, maybe use APM, though I forgot how.

---

### Post by Roaster on 2007-09-24
> **splintercellguy said:**
> Could be an ACPI thing, maybe use APM, though I forgot how.

Thanks,:)I'm to much of a noob to be knowing what that is!

---

### Post by lisati on 2007-09-24
> **Roaster said:**
> I don't know if this has anything to do with this problem but when booting a message flashes momentarily on the screen about an 'MP bios bug 8254 timer not connected to ACPI' or something to that effect. I'm sure it's a bios problem that only the bios maker can address. In that case American MegaTrends. Thanks for your interest. The computer does shutdown all the way from Ubuntu but I haven't checked to see if the mouse light is still on:).I'll check that the next time I shutdown.

I don't think this is related - I get the timer error message just about every time I boot, and I'm still able to boot.

---

### Post by Sef on 2007-09-25
Is your video card Nvidia?

---

