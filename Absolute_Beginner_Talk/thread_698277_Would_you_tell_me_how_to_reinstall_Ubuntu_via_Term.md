---
title: "Would you tell me how to reinstall Ubuntu via Terminal?"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by ahuman on 2008-02-16
[COLOR="Darkblue"]**I'm using a Dell Inspiron 531s with Ubuntu Linux 7.10 Preinstalled**[/COLOR]

[COLOR="SeaGreen"][B]Specifications:
Type: AMD Athlon 64 X2 3800+ Processor  
Model: WL400GSA1672 
Video-Card: Integrated NVIDIA GeForce 6150 LE Graphics 
Including: VGA Output

_Important note_:[/B][/COLOR]
[COLOR="Red"]**I've been using a LCD Monitor: HP Pavilion f1503 for that computer.**[/COLOR]

[COLOR="Darkblue"][B]Please tell me what to do to solve this problem:
When I started my Dell computer (with Ubuntu 7.10 preinstalled ), Ubuntu loaded within 1 minute, and as soon as the "Installation-Wizard" window was displayed on my LCD monitor a warning message (seen below) appeared:[/B][/COLOR]

[COLOR="Red"]Warning
PC video resolution setting is out of range
Change setting to Recommended resolution
1024x768@60Hz[/COLOR]

[COLOR="Darkblue"][B]I changed the display-settings to the "recommended resolution", and restarted my computer, then after Unbuntu's login window appeared again, it was completely illegible  (the login-page and everything else on Ubuntu, such as the desktop image & icons were completely blurry, overlapping each other in a tile-like pattern). After that I called the person, who sold the computer to me, and he told me to restart the computer, wait for the login screen to appear on Ubuntu, and type:

```
ctrl+alt+delete
sudo nvidia-xconfig
ctrl+alt+F7
ctrl+alt+delete
```[/B][/COLOR]

**[COLOR="DarkBlue"]Those terminal commands didn't allow me to change my display-settings in the terminal, so now I'm lost. Please help me find a way to either reinstall Ubuntu or fix the screen-resolution via the terminal on Ubuntu.[/COLOR]**

---

### Post by LaRoza on 2008-02-16
Run in recovery console:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by ahuman on 2008-02-16
**[COLOR="Darkgreen"]Thanks for helping me. Please tell me what would be a "safe' resolution for a 17x17 inch monitor?[/COLOR]**

---

### Post by LaRoza on 2008-02-16
> **ahuman said:**
> [COLOR="DarkOrange"]Thanks for helping me.[/COLOR]

It worked?

---

### Post by ahuman on 2008-02-16
**[COLOR="Darkgreen"]Yes, it worked. Would you please answer 2 more questions for me? I have over 10 different resolutions to choose from a list shown on the "package configuration (a.k.a. the Configuring xserver-xorg) window; dialog-box:[/COLOR]** **[COLOR="Purple"]So would you please tell me what you think would be a "safe' screen-resolution for a 17x17 inch monitor?[/COLOR]**

---

