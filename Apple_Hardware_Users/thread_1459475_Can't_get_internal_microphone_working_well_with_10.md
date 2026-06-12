---
title: "Can't get internal microphone working well with 10.04 on iMac 27&quot; i7."
date: 2010-04-21
forum: Apple Hardware Users
---

### Post by jisaac on 2010-04-21
Hi all!

I'm making some tests with the internal microphone and I've managed to record sounds but the results have a very low volume. I mean, I have to put the input volume to the max and I still get a pretty bad result.

Any idea?

Thanks.

PD: I've checked too the input volume in the alsamixer but no way, can't get better results.

---

### Post by sambarluc on 2010-04-22
Same problem here, but I can raise the volume as much as I like, and I can hardly go above noise. Oh, and I have a totally different machine. I had this problem before, with a fresh install of 9.04 and 9.10 (on other machines as well), but obviously I don't remember the solution, and I can't find it anywhere... Anybody has a clue?
Thanks

---

### Post by sambarluc on 2010-04-23
Suddenly, it works. Don't know if it's the RC update I have just done, or simply the rebooting, or this command I issued too:
amixer set Capture 100% rec

But one of the three, it should solve

---

### Post by jisaac on 2010-04-24
> **jisaac said:**
> Hi all!

I'm making some tests with the internal microphone and I've managed to record sounds but the results have a very low volume. I mean, I have to put the input volume to the max and I still get a pretty bad result.

Any idea?

Thanks.

PD: I've checked too the input volume in the alsamixer but no way, can't get better results.

Ok guys, there is a workaround (thanks to jaco223 and ZeroLinux) here:
[http://ubuntuforums.org/showthread.php?t=1439009](http://ubuntuforums.org/showthread.php?t=1439009)

Work for me in 9.10 too: Just select "alsa_input.pci-0000_00_1b.0.analog-stereo" instead of "alsa_input.pci-0000_00_08.0.analog-stereo".

Skype works well too!

---

### Post by jisaac on 2010-04-24
I don't mark this thread as "Solved" because I've noticed another problem: The recorded sounds are left speaker only!?

You can see it clearly with the PulseAudio Volume Meter.

Does anyone experience something similar?

---

### Post by odedjuglj9 on 2011-01-10
> **jisaac said:**
> Hi all!I'm making some tests with the internal microphone and I've managed to record sounds but the results have a very low volume. I mean, I have to put the [[COLOR=#000000]input[/COLOR]](http://www.changeformat.net/change-avi-format/change-avi-to-ipod-nano-4th-gen.html) volume to the max and I still get a pretty bad result.Any idea?Thanks.PD: I've checked too the input volume in the alsamixer but no way, can't get better results.It is just the solution for my problem, Thanks for your explanation! Now I got it.

---

