---
title: "1680x1050 Screen Rez..."
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by alecwh on 2007-06-14
Hey Ubuntu!

I've got a quick question...

I love this OS so far, but one of the problems, is that I have a pretty big screen, and I don't see a screen resolution option for my screen size.

1680x1050 

It's a SCEPTRE 20.1 Black screen.

Can anyone shed some light? I just started using Ubuntu hours ago...

---

### Post by Tux Aubrey on 2007-06-14
What graphics card are you using (newer nVidia cards operating with the restricted driver can use nvidia-settings but it has to be run with sudo to get it to save settings - boy, did that send me round the bend at first!).  Otherwise you will probably need to edit xorg.conf and will need a step-by-step guide if you haven't done it before.

---

### Post by alecwh on 2007-06-14
GIGABYTE GV-NX73G128D-RH GeForce 7300GS 512MB(128MB on board) GDDR2 PCI Express x16 Video Card

Is that what you're looking for?

---

### Post by Tux Aubrey on 2007-06-14
yep.  If you are using feisty (version 7.10) and haven't yet enabled the restricted drivers (in the menu System>Preferences - or System>Admin - I can't remember, I'm currently at work on Windows), you should do it.  That may give you the res options you want.

If not, you can install nvidia-settings (from the repos, I think) and set it there (it will be under the Applications menu - in Tools, I think)

I'm heading home soon so I will check back once I'm on my "real" computer (The Ubuntu one).

Others may chime in and help if this isn't what you need.

---

### Post by alecwh on 2007-06-14
Thanks!

I HAVE installed the restricted drivers, but it doesn't give me the rez option I need. I'm not quite sure what your other idea was.. can someone expand a little?

---

### Post by Tux Aubrey on 2007-06-14
Back at my Ubuntu machine...

Do you have the Nvidia Settings tool under the Applications>System Tools menu?
[B]
IF YOU DON'T...[/B]

Open Synaptic (System>Administration>Synaptic Package Manager) and use the search for "nvidia".  Amongst the things that will show up will be "nvidia-settings".  Select it and "apply"

Note: if it doesn't appear in Synaptic, you will need to select Settings>Repositories and enable all except "source" - I think nVidia stuff is in the restricted repositories, but it may be in universe)

Once installed it should appear in the Application>System Tools menu.  Proceed as below

**IF YOU DO....**

open it and select "X server display configuration" from the lefthand list and you should be able to select a new resolution.  Try it.  If it works that's good, but its not permanent.

You need to open nVidia-settings with sudo priviliges:

Applications>Accessories>Terminal and type/copy the following:

```
sudo nvidia-settings
```

Set the resolution again and this time click on the "Save to X configuration file" button at the bottom.  You should probably close all windows and restart the X-server (Ctrl+Backspace) and log in again.  Hopefully you will have the res you need now.

I hope this is clear!  (and I hope it works!)

If it doesn't, the next step is editing the xorg.conf manually to insert the desired resolution.  But let's cross that bridge if we come to it.  I hate xorg.conf.

---

### Post by alecwh on 2007-06-14
Thanks a lot for your help. I'm just reinstalling Ubuntu as we speak, I screwed it up. It's ok though, it was bound to happen. :)

I'll update back here when I've completed it.

---

### Post by alecwh on 2007-06-14
Ok, I DID NOT have it, so I downloaded and installed it. It doesn't appear in the Applications menu though...

---

