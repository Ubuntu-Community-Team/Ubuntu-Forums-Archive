---
title: "Nvidia Drivers Ubuntu"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by nnagflar on 2008-01-24
I'm having an awful first time Linux experience.  Here's what's happening:  I installed Ubuntu 7.10 and downloaded the latest Nvidia drivers for my 8800 GTS card.  I finally got the drivers installed through a series of command I don't understand, and I set up my monitors to the desired resolution.  This worked just fine, but it said I needed to restart X, and sudo /etc/init.d/gdm restart didn't do anything, so I decided to restart the system.  When it came back, I got a message that said my screen was running at a very low resolution.  I was given 640x480 or 800x600 as options.  I chose 800x600 so I could try and troubleshoot the problem, but it applied a resolution I cannot display instead.  Now I can't get to my desktop.  Please help.  :(

---

### Post by Kingsley on 2008-01-24
Try
```
sudo apt-get install nvidia-glx
```

Then, restart X with ctrl+alt+backspace.

---

### Post by nnagflar on 2008-01-24
Thanks, how do I get to the command line before loading the desktop?

---

### Post by Kingsley on 2008-01-24
Pressing ctrl+alt+F1 should do the trick.

---

### Post by mdpalow on 2008-01-25
Why did you have to install separate nVidia drivers? What was wrong with the Restricted drivers that are there by default. All you had to do was enable them and you should have been fine.

Am I missing something?

I stopped trying to install video drivers when it occurred to me the restricted ones were just fine..

---

### Post by nnagflar on 2008-01-25
The restricted drivers won't allow me to run my display at 1920 x 1080.  Attempts to edit my xorg.conf have produced no results.  It's ok, I'm back with Windows where stuff works.  I love the idea of Linux but hate the implementation.  I need a computer that works consistently.

---

### Post by kpkeerthi on 2008-01-25
Just enable nvidia restricted drivers. Then, Applications -> System Tools -> Nvidia Settings. Change the resolution here.

---

### Post by Zack McCool on 2008-01-25
> **nnagflar said:**
>  I need a computer that works consistently.

Interesting.  That's the very reason I use Ubuntu instead of Windows...

---

### Post by nnagflar on 2008-01-25
> **kpkeerthi said:**
> Just enable nvidia restricted drivers. Then, Applications -> System Tools -> Nvidia Settings. Change the resolution here.

I did.  I got a message to restart X.  When I did that, I got a black screen, and my system froze.  I was never able to successfully restart after that.  The system would just hang at the ubuntu logo at startup.

---

### Post by nnagflar on 2008-01-25
> **Zack McCool said:**
> Interesting.  That's the very reason I use Ubuntu instead of Windows...

Well, gosh.  Perhaps I got the broken version of ubuntu then.  I hear great things about Linux, but this experience has been full of problems.  Maybe better hardware support and stability will come with time.  I'll be back to give it another go, perhaps when this semester is over.

---

### Post by kpkeerthi on 2008-01-25
> **nnagflar said:**
> I did.  I got a message to restart X.  When I did that, I got a black screen, and my system froze.  I was never able to successfully restart after that.  The system would just hang at the ubuntu logo at startup.

> Then, Applications -> System Tools -> Nvidia Settings.
Really? Thats will never ask you to restart (as no config changes will be done at that point). You must have done something else.

---

### Post by kpkeerthi on 2008-01-25
> Attempts to edit my xorg.conf have produced no results. It's ok, I'm back with Windows where stuff works. I love the idea of Linux but hate the implementation. I need a computer that works consistently.
If you are (still) willing to try ubuntu... here is what you need to do:

You've got an 8800 card and the driver ubuntu installs with restricted drivers manager does not support this card. You need 169 version of the driver that needs to be installed manually. 

> Cleanup/uninstall whatever driver you installed thus far. 
> Restore your xorg.conf back to the version you had prior to the installation of nvidia driver. I hope you backed it up.
> Reboot and make sure your desktop is all OK as it was before.
> Install the driver manually by following the instructions [here]("https://help.ubuntu.com/community/NvidiaManual"). Get your drivers from [here]("http://www.nvidia.com/object/unix.html")
> Reboot. 
> If the resolution did not auto-configure, its OK for now. Login to your desktop as usual.

**How to fix resolution:**
1. Open a terminal and type **nvidia-settings**
2. Change the resolution and make sure your desktop looks OK. It will not ask you to reboot as the changes were not made permanent yet. See below.
3. When all is fine, let's make the change permanent. Close nvidia-settings.
3.a. Type **gksudo nvidia-settings** in the terminal window
3.b. Choose the resolution you chose above and click on "Save to Xorg.conf" button.
4. Reboot.

---

