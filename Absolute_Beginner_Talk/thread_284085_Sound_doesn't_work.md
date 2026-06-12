---
title: "Sound doesn't work"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2006-10-25
My sound doesn't work on my laptop when I use say, VLC, but it does work when I listen to youtube videos on the net. I HAVE read the thread entitled "If you can't play mp3, wma, mp4 or mostly any other codec read this" and did what it said, but I still get the following error when I click on the sound icon:

No volume control GStreamer plugins and/or devices found.

The odd thing is that I have installed GStreamer via Synaptics and it still doesn't work. My (onboard) sound is by ESS technology (not sure exactly what the onboard sound version is) and it isn't disabled in the  bios.

So does anyone know how to fix this problem?

thanks :)

---

### Post by spamzilla on 2006-10-25
I found out what my sound make/version is:

0000:00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)

---

### Post by Bachstelze on 2006-10-25
IIRC, Youtube uses Flash and I heard sound in Flash can be problematic. Try searching for it in the Wiki.

---

### Post by spamzilla on 2006-10-25
> **HymnToLife said:**
> IIRC, Youtube uses Flash and I heard sound in Flash can be problematic. Try searching for it in the Wiki.

I couldn't find anything in the wiki about this problem :/

---

### Post by spamzilla on 2006-10-25
Hmmm I think my problem is that my sound card isn't compatible with Linux. What can I do to fix this?

---

### Post by Bachstelze on 2006-10-25
First, try other players like Totem or Rythmbox - assuming you're using GNOME. None of them works ?

---

### Post by Kateikyoushi on 2006-10-25
Try the sound guide, I bet it is just a setup problem. [LINK]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")

If you solve it please report back what was the problem.
In case you stuck post the output of these two lines.

```
aplay -l
lspci -v
```

---

### Post by spamzilla on 2006-10-25
> **HymnToLife said:**
> First, try other players like Totem or Rythmbox - assuming you're using GNOME. None of them works ?

I have tried totem and vlc. Both do not output any sound.

Katie - in that setup guide, I got to section 3, and my sound card driver is not listed [here](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-ESS_Technology#matrix)  , so I cannot go any further.

Here's the terminal command output:

```
matt@matt-laptop:~$ **aplay -l**
aplay: device_list:221: no soundcards found...
```

I only pasted the relevant info here.
```

matt@matt-laptop:~$ **lspci -v**
0000:00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
        Subsystem: Dell Latitude C600
        Flags: bus master, medium devsel, latency 32, IRQ 5
        I/O ports at d800 [size=256]
        Memory at f3ffe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>
```

---

### Post by spamzilla on 2006-10-25
Could this be the problem?

```
  Capabilities: <available only to root>
```

If so, how do I fix it?

---

