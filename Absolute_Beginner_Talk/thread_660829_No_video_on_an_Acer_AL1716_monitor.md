---
title: "No video on an Acer AL1716 monitor"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by davidwfox on 2008-01-07
I'm running 7.10 on a Sony laptop with an Acer AL1716 external monitor.

When I run video the laptop screen shows the video but the Acer monitor remains blank. The programme to run the video opens OK on both screens but the section where the video should be displaying remains blank on the Acer screen.

I've tried both with Movie Player and with MPlayer Movie Player. Static images (.jpg and similar) all show OK on both screens - the problem only occurs with video.

How do I overcome this problem??

---

### Post by dcstar on 2008-01-07
> **davidwfox said:**
> I'm running 7.10 on a Sony laptop with an Acer AL1716 external monitor.

When I run video the laptop screen shows the video but the Acer monitor remains blank. The programme to run the video opens OK on both screens but the section where the video should be displaying remains blank on the Acer screen.

I've tried both with Movie Player and with MPlayer Movie Player. Static images (.jpg and similar) all show OK on both screens - the problem only occurs with video.

How do I overcome this problem??
```

gksudo dpkg-reconfigure xserver-xorg
```
with the external monitor plugged in may set up your system correctly to use both devices.

---

### Post by davidwfox on 2008-01-08
Thanks David, but there seems to have been no improvement.

Running the gksudo command brought up a multi-coloured screen, very difficult to read (pale blue text on a bright green background). I selected "Yes" - Attempt to Auto-Detect video hardware (red text on a black background) and a purple cursor appeared to the left and just below "Yes". The cursor continued flashing, with no HDD activity. I closed the terminal window, reloaded it and re-ran the command, and this time tried to select "No" but couldn't get my cursor to settle on "No".

I retried this process another 2 - 3 times, with the same results, so tried to run a video clip again. Same result - video on the Sony screen, nothing on the Acer.

Any further thoughts? (and thanks for trying so far).

---

