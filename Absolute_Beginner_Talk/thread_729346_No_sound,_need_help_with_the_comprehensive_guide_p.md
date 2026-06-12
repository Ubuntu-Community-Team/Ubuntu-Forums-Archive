---
title: "No sound, need help with the comprehensive guide please"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by xzarakizraiia on 2008-03-19
Hi there. Thanks to everyone who is reading this- I'm trying to get my sound working but I have some questions/problems the comprehensive sound guide hasn't been able to answer.

Here is the link to the guide:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Step 1 was a success- this is the result I got:

```
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

As was step 2- I found my sound card listed:

```

05:07.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs Unknown device 1013
        Flags: bus master, medium devsel, latency 32, IRQ 22
        I/O ports at bf00 [size=32]
        Capabilities: <access denied>

```

I then checked to see if my sound card was listed as supported under the ALSA project page. It was, under "Sound Blaster LS." The chipset listed on that page was  SB0310
P17. There was a "Details" link that goes here:

[http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106](http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106)

After that the guide says "Try to match the chipset you found in step 2 with the driver(green hyperlink text)." I think the guide may be out of date, because I couldn't find green hyperlink texts anywhere on those pages (and the actual link in the guide appears to be broken; the link I originally used was from a support document not on the forums), and I do not know what my driver version is or how to find it. This is my main problem.

Regardless, I decided to go on to the next step and type sudo modprobe snd- into the terminal, at which point I got this response:

```

FATAL: Module snd_ not found.

```

...Which is my other main problem. I don't know enough to know which of those problems is more important, but, well, here I am. If anyone can help me out with this so I can trudge on with the guide, I would appreciate it immensely!

Thanks

---

### Post by handydan918 on 2008-03-19
Could we have the output of ```
lspci | grep -i audio
``` 
and 
```
lsmod | grep snd
```

pretty please?

---

