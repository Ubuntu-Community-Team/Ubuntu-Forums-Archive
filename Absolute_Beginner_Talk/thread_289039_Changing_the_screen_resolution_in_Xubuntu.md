---
title: "Changing the screen resolution in Xubuntu"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by HenningS on 2006-10-30
Hi.

The newly-installed Xubuntu PC has a max resolution of, I believe, 800x600. I mean, I can't set it higher than that. Which is a pain in my .....eyes, since I know this monitor does up to 1600x1200. How do I change that, and do I have to install any graphics card drivers? I know that one would be difficult because I have no idea what brand or model or whatever this onboard thing is.

---

### Post by bruce89 on 2006-10-30
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by HenningS on 2006-10-30
> **bruce89 said:**
> ```
sudo dpkg-reconfigure -phigh xserver-xorg
```Okay, I think it did something. But how do I change the resolution now? The display settings still list 800x600 as the greatest resolution.

---

### Post by bruce89 on 2006-10-30
> **HenningS said:**
> Okay, I think it did something. But how do I change the resolution now? The display settings still list 800x600 as the greatest resolution.

What resolution does it use when you select "Default"?

---

### Post by CatKiller on 2006-10-30
You may also have to check the refresh rate ranges of your monitor.

---

### Post by HenningS on 2006-10-31
> **bruce89 said:**
> What resolution does it use when you select "Default"?I think this is 800x600, maybe even 1024x768, but if you tell me how to do a screenshot, I can tell by the file properties. by the way, how do I switch the Kezboard lazout back to German?

---

### Post by eeried on 2006-11-10
> What resolution does it use when you select "Default"?

Where do you see it? In the settings, default doesn"t say what it is.

---

### Post by dermotti on 2006-11-10
When you run **sudo dpkg-reconfigure xserver-xorg** there is a point in which is asks you what resolutions you want.

Just uncheck all resolutions except the one that you DO want, and that should pretty much gurantee it will default you to that resolution.

---

### Post by eeried on 2006-11-12
> When you run sudo dpkg-reconfigure xserver-xorg there is a point in which is asks you what resolutions you want.

Just uncheck all resolutions except the one that you DO want, and that should pretty much gurantee it will default you to that resolution.

You may run the risk of choosing a resolution the Xserver doesn't like and get an "out of scan range" message.

Why don't you change your resolution from the Xubuntu setting panel (Screen Display)? Then if you get an "out of scan range" message, Just wait until it vanished and choose a different resolution.

How strange this resolution business is! Xubuntu loves very high resolutions for my tiny 14"-15" screen  which supports them though the highest one isn't comfortable because the refresh range isn't high enough. ;)

---

### Post by MimeyNaomi on 2008-06-10
I have the same problem as the original poster, but running dpkg-reconfigure xserver-xorg didn't give me any options to change my screen resolution, only my keyboard layout etc.

---

### Post by eeried on 2008-06-11
MimeyNaomi: Xorg has changed a lot as you can see. This means you can change graphic cards and screen without running dpkg-reconfigure....

You can try changing the resolution through the system or pref menu in Xubuntu.

The problem I find in Xubuntu Hardy is though I can change the size of the fonts, they don't change in the window bar of an application. This is rather annoying but there must be a way :confused:

PS: Thix Xubuntu Hardy is installed on a Pentium III.

---

