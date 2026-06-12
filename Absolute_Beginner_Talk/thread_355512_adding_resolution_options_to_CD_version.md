---
title: "adding resolution options to CD version"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by wfcentral on 2007-02-07
I want to learn more about ubuntu, but I'm not ready to install on a hard drive. I have the CD version running fine, but the highest resolution is 800x600.

How do I get higher resolution? such as 1280x1024?

I'm guessing I will have to download a "non-ISO" version and modify some config files, then create a CD from that modified version?

Robert

---

### Post by renzokuken on 2007-02-07
i suppose a temporary fix would be to run  

```
sudo dpkg-reconfigure xserver-xorg
``` and select other resolution there, but you'll prolly have to do that everytime you boot the cd

---

### Post by wfcentral on 2007-02-07
I guess I was just shocked that the only resolutions available from the CD are 640x480 and 800x600.

Is that how it works for everyone? or is it something to do with my hardware? like a video driver not installed or recognized?

Robert

---

### Post by renzokuken on 2007-02-08
its probably using the "vesa" driver by default which has a limit to its resolutions. if you wanted the max resolution for your grafix card you would need to install the fglrx (ATI) or nvidia-glx (nvidia) drivers

---

### Post by steve.horsley on 2007-02-08
> **wfcentral said:**
> I guess I was just shocked that the only resolutions available from the CD are 640x480 and 800x600.

Is that how it works for everyone? or is it something to do with my hardware? like a video driver not installed or recognized?

Robert

It is to do with your hardware. X is not sure it can go higher resolution with your hardware. As renzokuken said, try the command:
**sudo dpkg-reconfigure xserver-xorg**
select the defaults except for the question about resolutions, then when it's finished, use Ctrl-Alt-Backspace to restart X.

---

### Post by wfcentral on 2007-02-08
can I do these things running from the Live CD? I have not installed it on my system (HD).

---

### Post by renzokuken on 2007-02-08
yeah you can but it will probably forget your settings when you shutdown (although i think there is some way of using a USB stick in sync with the live cd to remember your settings)

---

