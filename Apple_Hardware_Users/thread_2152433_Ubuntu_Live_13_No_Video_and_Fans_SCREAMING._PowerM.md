---
title: "Ubuntu Live 13 No Video and Fans SCREAMING. PowerMac G5, 4GB, Late '04"
date: 2013-06-07
forum: Apple Hardware Users
---

### Post by vintagecoke on 2013-06-07
Hi all, I have a PowerMac G5 which I am trying to run Ubuntu on. I get the PPC live disk and I boot to it. It gets to a white screen with text and then it goes black. The disk tries to read after that and the fans scream. Please help.

---

### Post by vintagecoke on 2013-06-07
So I got to the initframfs prompt, but I want to actually use the live CD without actually installing first. I want to also partition my current OS X drive without erasing it, which is why I need the live cd(I don't have an installer DVD). But this shows progress for sure.  If I have enough help, I will write a HOW-TO for the powermacs. There seems to be alot of issues with installing them. I do have the NVIDIA GeForceFX 5200 Ultra, if that helps. So, the fans scream on the initramfs prompt (why?! You can play Minecraft with barely audible fans, but rendering 6 lines of text it a chore?). Actually, the whole reason for me installing linux is to get openjre7 for Minecraft. I HAVE tried Lubuntu, but I get the same issue that I did in the first post. Here is what I have tried:
Ubuntu 12.04 PPC
Lubuntu 12.10 PPC
and Ubuntu 13.10 BOTD.

---

### Post by este.el.paz on 2013-06-07
> **vintagecoke said:**
> I HAVE tried Lubuntu, but I get the same issue that I did in the first post. Here is what I have tried:
Ubuntu 12.04 PPC
Lubuntu 12.10 PPC
and Ubuntu 13.10 BOTD.

@vc:

Over here, briefly, your best bet if you haven't done a linux install before is to start with the Lubuntu 12.04 for PPC LiveDVD edition . . . it may boot without any extra boot parameters besides "live" . . . if it doesn't boot right up you may have to read through the forum to find the right boot parameters for the G5 nvidia card.  You could read through the "Testers wanted for 12.04" thread and find where str8bs gives some examples, or rsavage may have also, others.  BUt 12.04 is the most cleaned up version for PPC . . . in Lubuntu.

e.e.p.

---

### Post by vintagecoke on 2013-06-07
Okay, great. I said I would do some test builds tonight on that thread.

---

### Post by vintagecoke on 2013-06-07
Alright, I get an input signal out of range.

---

### Post by vintagecoke on 2013-06-07
Okay, the ORIGINAL Lubuntu that I downloaded decides to work. But I do not get a desktop GUI. Is that to be expected? I really need the GParted.

---

### Post by vintagecoke on 2013-06-07
Okay, LightDM gets to ERROR the object 'dev/adb' does not exist.
Starting PBButtonsd [FAIL]
stopping kernal save messages.

---

### Post by este.el.paz on 2013-06-08
> **vintagecoke said:**
> Okay, LightDM gets to ERROR the object 'dev/adb' does not exist.
Starting PBButtonsd [FAIL]
stopping kernal save messages.

What boot parameters are you using to get this far?  And is this 13 or 12 that you got to work?

e.e.p.

---

### Post by 128keaton on 2013-06-08
Its okay, I used your recommended ISO. It all works now!

---

### Post by este.el.paz on 2013-06-08
> **128keaton said:**
> Its okay, I used your recommended ISO. It all works now!

@128keT:

OK, that's great news . . . did you change your name?  Are you "talking" to me (e.e.p.)??  What ISO are you using for what computer?  All this information may help someone else with their problem, if we don't know what computer or what ISO, we can just "Be Happy" about it, but we don't know why . . . .  : - ))  But, thanks for posting and glad something worked out for you . . . .

e.e.p.

---

### Post by vintagecoke on 2013-06-10
Whoops Sorry! I used an old account. I used Lubuntu 12.04 Live ISO. I am installing today after partitioning pain! But anyway, I am using a PowerMac G5 Late 2005 with no extra boot parameters. Now my beef is with LWJGL and Minecraft. Thanks!

---

### Post by vintagecoke on 2013-06-10
Okay, another error. The installer could not remove the conflicting files. I have a swap, Ext4, and a NewWorld boot partition. I think i am not using the correct mount points. 
Ext4: Mount Point: '/'
No mount point for swap.
NewWorld: Mount Point: '/home'

---

### Post by este.el.paz on 2013-06-10
> **vintagecoke said:**
> Okay, another error. The installer could not remove the conflicting files. I have a swap, Ext4, and a NewWorld boot partition. I think i am not using the correct mount points. 
Ext4: Mount Point: '/'
No mount point for swap.
NewWorld: Mount Point: '/home'

@vc:

I think I can answer this question, as I have done quite a number of installs as various Linux systems.  First off, lately I've tried to set the area where I want the Linux install to "Free space" and then use, "Guided, use largest free space" and let the installer set up the details . . . .  BUt, from what you've listed for Ext 4 as "/" that is correct, same for swap as long as it's labeled "swap" but for "New World boot" I don't think that should be labeled as "/home" . . . it should be "boot" or "Yaboot" or something like that . . . it can be 1 MB for Yaboot partition.

e.e.p.

---

### Post by vintagecoke on 2013-06-10
The mount point of the NewWorld is /boot just to be clear?

---

### Post by vintagecoke on 2013-06-10
Okay, weird. It decides to work for now.

---

### Post by este.el.paz on 2013-06-10
> The mount point of the NewWorld is /boot just to be clear?

@vintage:

I can't be clear since I don't have the installer in front of me, but I believe the only partition that is critical for "mount point" is the Ext4 . . . and after that it's "labeling" and that would be from the drop down menu when you 2x click on your selected partition in Gparted . . . the Boot partition is labeled as "boot" or "New world Boot" . . . from whatever the choices are.  It's only the "/" mount point that seems to hold up the install if you haven't selected it.

e.e.p.

---

### Post by vintagecoke on 2013-06-10
Okay, the install is at: 'Copying Files'

---

### Post by vintagecoke on 2013-06-10
Okay, I got it installed, rebooted, at yaboot. What do i type in?

---

### Post by vintagecoke on 2013-06-10
Nevermind, just push enter.

---

### Post by pauljwells-m on 2013-07-30
Just for info. The screaming fans thing is because the fan controllers are not in the live cd kernels (not all, anyway) so the hardware resorts to maxed out cooling, to be safe. Once installed the fans are controlled by the os.

---

