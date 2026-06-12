---
title: "Install video driver"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by leesway on 2007-06-02
I found a video driver for my laptop (Itronix IX250). When I unziped it I have two files. How do I install them? I am using 6.06LTS.

---

### Post by BaffledMollusc on 2007-06-02
> **leesway said:**
> I found a video driver for my laptop (Itronix IX250). When I unziped it I have two files. How do I install them? I am using 6.06LTS.

Okay, from a bit of googling it looks like that laptop uses a Savage S3 chip for graphics. Can you confirm this? If so, that chip is pretty old and I presume that the driver would already be in the Linux kernel. Is there a reason that you think you need to install graphics drivers separately?

Also, are you sure you have downloaded Linux drivers rather than Windows drivers?

---

### Post by leesway on 2007-06-02
The only resolutions that are offered are 800X600 and 640X480. Would like higher screen resolution. I have used "sudo dpkg-reconfigure xserver-xorg" and selected higher resolutions. When I reboot I still just have 800X600 and 640X480.

---

### Post by leesway on 2007-06-02
And yes the video is S3 savage.

---

### Post by BaffledMollusc on 2007-06-02
> **leesway said:**
> And yes the video is S3 savage.

Okay, I'm guessing it's not a driver problem, although I'm definitely not an expert. You could try the suggestions outlined here:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

I think the part that is most likely to apply to your case is the bit starting with "Also if you have an issue where only 800x600 is" - do a search for this. 

Essentially you have to edit your /etc/X11/xorg.conf file, and add the resolutions you want under "Modes" in the "SubSection Display" section. 

Worth trying, at least! I'm off to bed now, but hopefully someone else will have suggestions...

---

