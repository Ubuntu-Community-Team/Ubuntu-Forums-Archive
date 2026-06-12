---
title: "Macbook 5.1 crashes"
date: 2009-03-22
forum: Apple Hardware Users
---

### Post by acron on 2009-03-22
Hi there,

my Macbook started crashing reproducible when using LyX (a Latex GUI program), but I think the problem itself must be something else. A userspace program executed by a non root user isn't supposed to crash my machine, is it?
Well I'm not even sure what crash means. I think it's a kernel panic, but I cannot find evidence in my logs.
Ctrl-Alt-Backspace does not work, the LED when pressing Caps-Lock stays off (which I'm used to pess to see if the module/kernel is still responding).
I currently cannot verify if the Macbook still response to a ping request. So it might also be that only X and keyboard stopped working... But I just don't think so...

The Macbook is installed following this wiki entrance:
[https://help.ubuntu.com/community/MacBook5-1/Intrepid](https://help.ubuntu.com/community/MacBook5-1/Intrepid)
and every thing works as it is said there... backlight, keyboard functions, trackpad and so on. As the guide changed quite often since I own ths macbook, the ubuntu install has also changed often with installing and removing packages which are/were mentioned in this guide.

I will later on attach some logs... syslog, messages, X.org and lsmod and lspci (anything else?) later on.
For now can someone give me some hints how to debug this issue?

Greetings from Germany
acron

---

### Post by acron on 2009-03-22
attachments

---

### Post by acron on 2009-03-22
even more attachments

---

### Post by acron on 2009-03-22
The last thing the kernel writes to the logs seems to be:
```

NVRM: Xid (0002:00): 13, 0001 00000000 0000502d 000008dc 00000000 00000100

```

So the problem seems to be related to the nvidia driver... 
Driver Version is 180 installed from ubuntu...

Here is my xorg.conf
```

Section "Monitor"
  Identifier  "Configured Monitor"
EndSection

Section "Screen"
  Identifier  "Default Screen"
  Monitor   "Configured Monitor"
  Device    "Configured Video Device"
  DefaultDepth  24
EndSection

Section "Module"
  Load  "glx"
EndSection

Section "Device"
  Identifier  "Configured Video Device"
  Driver  "nvidia"
  Option  "NoLogo"  "True"
# Option "Coolbits" "1"
  Option     "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2233; PowerMizerDefault=0x3"
EndSection

```
The last option is to throttle the video card a bit. I'll remove them now and reboot to see if these cause trouble.

Edit: Just tested -> crashed my ubuntu. The option is not the problem.
Hmm... My mouse pointer still moves does that indicate that the kern has not panicked?

Greets acron

---

### Post by acron on 2009-03-22
I just downgraded to nvidia driver 173. Problem seems to be gone...
I'd like to mark the thread as solved... still I do not see this option? :shock:

Greets acron

---

### Post by cyberdork33 on 2009-03-22
> **acron said:**
> I just downgraded to nvidia driver 173. Problem seems to be gone...
I'd like to mark the thread as solved... still I do not see this option? :shock:

Greets acron
they disabled that feature due to server strain. Just add "solved" as a tag.

Jaunty will have a newer nvidia driver version.. You should test to see if it has the same issue.

---

### Post by acron on 2009-03-23
> **cyberdork33 said:**
> they disabled that feature due to server strain. Just add "solved" as a tag.

Ok.
> **cyberdork33 said:**
> 
Jaunty will have a newer nvidia driver version.. You should test to see if it has the same issue.
Yeah, I'll see.

Thanks
acron

---

### Post by namtienus on 2009-07-20
[FONT=Arial][SIZE=2]I have the same problem with My Macbook 5.1 Aluminum Unibody.

First, I installed Nvidia driver 180 as shown "recommended" in the proprietary driver list. Then the Mackbook keep crash (screen frozen) with RapidSVN, X-Unikey (languages typing program other than English), Thunderbird Mail and VMware Server.

The mouse and the computer stop running whenever the problem happened.

Anytime, I encountered this problem, I must manually push and hold the power button then restart again. (I don't know if the hard drive will crash soon).

I tried to remove the Nvidia Driver 180, but there was a error showing up saying there's problem with "Ubuntu Jockey...". I just worked around by installing the Nvidia 173 driver to disable the old one.

But there's a new problem, anytime I open a problem such as firefox or openoffice, when I scroll the mouse to move down, the text keep showing overlapping each others. Let me know if you have solution for this problem.
[/SIZE][/FONT]

---

### Post by acron on 2009-07-20
Hello namtienus,

I had the rendering problem as well. See this thread:
[http://ubuntuforums.org/showthread.php?t=1170830](http://ubuntuforums.org/showthread.php?t=1170830)
so I switched back to 180...
However the freezing issue is gone on my machine now, something must have been changed/fixed in jaunty.

What version of ubuntu do you run namtienus?

Greets acron

---

### Post by namtienus on 2009-07-22
[FONT=Arial][SIZE=2]Hi Acron,

I'm using Ubuntu Jaunty 9.04 with Linux 2.6.28-14-server on i686.

I encounter the same problem before and after upgrading my kernel to server kernel. I want to do this because my Macbook 5.1 came with 4GB of Ram. by default, Ubuntu Jaunty only recognized 2GB.

Also, I tried Ubuntu 8.10 Intrepid Ibex, but the Wireless card doesn't work that why I switched to Jauty.

I still have screen disordering (text overlapping) problem. Let me know if you can fix this.

Macbook 5.1 Aluminum Unibody
Ram 4GB
Ubuntu Jaunty with Linux 2.6.28-14-server kernel

Cheers,
Tien
[/SIZE][/FONT]

---

### Post by luigi.viggiano on 2009-07-22
To me it is happening that ubuntu freezes for some seconds (only mouse is moving), then it get back to work. It's not reproducible. 

ubuntu 9.04 on macbook pro 5.1 with compiz enabled.

---

