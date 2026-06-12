---
title: "Problems with X server"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by culmen on 2005-12-04
I got a cd rom to install ubuntu 5.10 to run in my pc which has windows xp operating system. I found in internet a good tutor how to do the partioning and so on. However at the end I got a message that said:
"Failed to start the X server (your graphical interphase). It is likely that it is not set up properly."
I can login in the "black screen" but can't do more because I'm an amateur with Ubuntu and configuration.
Hope that somebody can help. I am very pleased to hear do I have something wrong with my hardware or is there something special I have to do when installing Ubuntu into my system. Is there some tool available and advice how to use that tool to help me out from this problem?
Thanks in advance

---

### Post by davmac on 2005-12-04
What sort of video card and monitor is it you're trying to set up? There's a list of supported video cards at [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards?highlight=%28video%29](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards?highlight=%28video%29)

Hope this helps,

Dave Mac

---

### Post by culmen on 2005-12-04
Hi Dave Mac,
Thanks...I checked my video card and when cheking the list it looks yhat my CeForce FX 5200 will work if I just install the nvidia-glx. I tried to run this command: "sudo nvidia-glx-config enable" but that command wasn't accepted. How can I install this NVIDIA driver? I'll be more than pleased if I can some hints how to go on with this..step by step instructions will be super to a beginner like me. I really have a feeling that the problem is in front of keypad.

Culmen

---

### Post by davmac on 2005-12-10
To install it, open up a terminal and type "sudo apt-get install nvidia-glx".

It is not something I've had to do myself, but hopefully once it is installed you'll be able to use the command you tried earlier.

Hope this helps,

Dave Mac

---

### Post by Qrk on 2005-12-10
Before you can install it you have to enable mulitverse I believe. Mulitverse is where the non-Free software for Ubuntu is.

```
sudo nano /etc/apt/sources.list
```

Remove the # from the lines with only 1 of them; the link lines.

---

