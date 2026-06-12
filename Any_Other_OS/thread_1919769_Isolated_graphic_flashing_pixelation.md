---
title: "Isolated graphic flashing pixelation"
date: 2012-02-03
forum: Any Other OS
---

### Post by HappyLinux on 2012-02-03
Since a few days ago, a problem has shown up. In the top left of my screen I get some flashing black rectangular pixels. It's always in the top left of the screen.

If you split the screen into say a 6x6 grid, it's only in square 1 in the top left. never in any others. That's why it's isolated.

This flashing remains no matter what program I load. Firefox, LibreOffice, etc.

To get rid of it for the time being, a simple logout and back in gets rid of it.

It's not a hardware problem because I'm on a dual-boot with Win7. So if it's a hardware problem, it'd show up there.

If you have any questions for finding the problem, then please ask away.

---

### Post by sudodus on 2012-02-03
It is always good to know about the computer and the operating system, when trying to help.

- What computer is it? motherboard, cpy, graphics card
- What version (11.10?) and flavour [KLX] or 'vanilla' of Ubuntu is it?
- Is it depending on the screen resolution?

---

### Post by HappyLinux on 2012-02-03
Sorry, that slipped my mind. I've been rushing about today, and having a medical condition which renders you unconscious on a regular basis doesn't help. however, down to business.

Asus P7P55LX mobo
Intel i3 720
4GB memory
nVidia GTS450
Samsung SyncMaster 943

OS is Linux Mint 12 dual-booted with Windows 7.

All the Win7 drivers are up to date, and I typically only use windows for gaming.

the nVidia drivers under Linux that I have installed is 280.13. the most recent from the repos.

the screen resolution on both OS's is 1440x900 75hz.

any other info needed?

---

### Post by sudodus on 2012-02-04
How does it start: 'always' after a while or when you use a particular program? What happens if you select another graphics mode: screen resolution and/or screen refresh rate?

Maybe it is the graphics driver. ***I suggest that you try another version of nvidia's proprietary driver***. I haven't got Mint 12 (but I have Ubuntu 11.10 and Mint 11), so I don't know what is available to choose without starting to download drivers from nvidia's site.

---

### Post by HappyLinux on 2012-02-04
It only really starts when I first load the computer. GRUB by default boots into Mint.

Basically, I press the power button and leave it to run its course and load straight into Mint. That's when it starts. so i log out and then back in and it's gone.

I've never successfully installed the proprietary drivers from nVidia's website. However, before I moved too Mint, I was using Ubuntu which I used a popular repo for the drivers. Perhaps I'll give that a try and see what happens.

Also I'll see what happens with changing the resolution etc, however, a refresh rate below 75hz for me is not advisable, and it's the fastest my monitor can handle.

---

### Post by mips on 2012-02-04
> **HappyLinux said:**
> 
**I've never successfully installed the proprietary drivers from nVidia's website.** However, before I moved too Mint, I was using Ubuntu which I used a popular repo for the drivers. Perhaps I'll give that a try and see what happens.

If you are using Linux Mint 12 (Based on Ubuntu 11.10) and not the LMDE version then try using the X-SWAT PPA.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=oneiric](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=oneiric)

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
```

---

### Post by HappyLinux on 2012-02-04
That's the repo that I was referring too. showing, forgot to mention it. I've now updated the drivers from that repo. So far, so good.

---

### Post by HappyLinux on 2012-02-09
UPDATE - After the driver update from the x-swat repo, I've not had a single graphical problem. So I will take it as problem solved and close this thread.

---

