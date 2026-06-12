---
title: "medion tv-tuner 7134"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by jolger on 2007-03-14
Hello there... i've been struggling with my medion tv-tuner 7134 (wich funny enough based on the saa7134 chip).

Now, my problem is that i can view analog TV, but no dvb-t whatsoever, i've been looking through the forums for the past three days for a solution, with no luck...

If anyone has a "Step-by-Step guide" in how to make your saa7134 chip based tv card working i'd really appreciate it...

if noone has a guide... maybe that person knows how to make it work with dvb-t support...

I got it working for analog, with dma sound and so on (sox)... but i just cant get it working with dvb-t support... each time i try installing v4l i get a lot of error messages when doing the "sudo make reload", and no dvb/ is created in /dev/ ...

So if anyone has a "solution" to my problem i'd really appreciate it...

lspci | grep Multi gives me the following output:

> 00:13.0 Multimedia audio controller: nVidia Corporation MCP04 AC'97 Audio Controller (rev a1)
03:06.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
03:07.0 Multimedia controller: Philips Semiconductors SAA7134 Video Broadcast Decoder (rev 01)

so, as i see it, the device is recognized and all that stuff... but not with dvb-t support...

---

### Post by haelters on 2007-03-15
I'm also struggling with V4L, but with the Radio part. I've got the video to work.

Were you able to install the v4l from the mercury tree? Once you have checked out the code, you should do make followed by sudo make install. If this step is giving errors, post them here (last lines) or put it somewhere on the internet and give a link.

Once the code is compiled, you must ```
sudo modprobe cx88_dvb
```. This will give you the /dev/dvb entries.

Let me know if this worked out.

---

