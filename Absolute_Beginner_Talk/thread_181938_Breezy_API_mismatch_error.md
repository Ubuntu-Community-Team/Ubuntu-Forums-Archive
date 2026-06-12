---
title: "Breezy: API mismatch error"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by wog on 2006-05-25
I'm on CLI and GDM fails every time I boot up.

I get this error (paraphrased):
API mismatch: NVIDIA kernal module is 1.0.7174 but Xmodule is 1.0.7667.

History:
I'm a Linux newbie and I've only known Windows before this (I figure some things are repairable). I upgraded from Hoary to Breezy. My proc is AMD. My video card is an GeForce4 FX5200. I seem to have guessed wrong on the flavor of k7 kernal. If I didn't have my laptop I'd be pulling my hair out by now.

What do I do next?

---

### Post by nalmeth on 2006-05-25
[quote=wog]I'm on CLI and GDM fails every time I boot up.

I get this error (paraphrased):
API mismatch: NVIDIA kernal module is 1.0.7174 but Xmodule is 1.0.7667.

History:
I'm a Linux newbie and I've only known Windows before this (I figure some things are repairable). I upgraded from Hoary to Breezy. My proc is AMD. My video card is an GeForce4 FX5200. I seem to have guessed wrong on the flavor of k7 kernal. If I didn't have my laptop I'd be pulling my hair out by now.

What do I do next?[/quote]
Did this occur right after the upgrade?
If you really think it's the k7 kernel, you can boot up on your old kernel, considering you didn't remove it.
When you're booting up, and grub start's to load, immediately hit ESC to load GRUB menu, and pick a different kernel.
Any compelling reason you had to go to k7 kernel? 

Let us know what happens

---

### Post by wog on 2006-05-25
This *sort of* happened right after the upgrade. I failed to realize Linux wouldn't show true results until after I rebooted. Windows forces a reboot on any install, so I apparently got spoiled by that.

I'm enough of a newbie there are structural things about Linux I don't understand, such as: Is there a single kernal for Linux and everything in it, or does the video card have a kernal too? Is that what's complaining here?

To try a fix I attempted to reinstall Ubuntu and somehow ended up with a second copy on the drive, so now on booting the list of kernals is displayed, so that's taken care of, but will remember your advice about interrupting GRUB for later. :-D 

I read on the forums here that slow performance could be caused by having a kernal not optimized for the proc, and then later found out the video drivers were (?) incorporated into the kernal, so to get 3D I felt it necessary to change to the k7 kernal (because I have an AMD proc, which supposedly is what works with that).

Should I get rid of the offending kernal and go back to i386? Should I forget about 3D until I have a ghost of a clue about what I'm doing? 

Making mistakes is the only way I know how to learn, sorry. ;)

---

### Post by nalmeth on 2006-05-25
>  Making mistakes is the only way I know how to learn, sorry. :wink:
Very true, I am the same way. Only usually a lot of people don't have this kind of patience.

The kernel (if you system was a car) is basically your engine. It's job is to allocate  system resources to your processes. The video card driver's are incorporated into the kernel, so there is no kernel for the video.

Honestly I can't remember what the k7 kernel is for, but you may be confused with the AMD64 kernel. Do you have a 64-bit processor? In any case, the i386 kernel should be fine for you. Or do you have dual-core or hyper-threading processor? For these cases, you get better performance from the i686 kernel.

All is not lost, you can still boot in on the i386, just hit ESC when GRUB is loading and pick the old one.

---

### Post by wog on 2006-05-25
Okay, so I messed with the central part of the OS.

According to the thread I looked at, the i686 kernals are for Intel, the k7 line is for AMD, and the i386 kernals are the default that just about everyone and everything can use. I can see now I'm going to have to keep notes of what threads I get information from instead of simply writing down notes.

So the above error message means the kernal I put into place was old in comparison to the Xmodule already in place. So what is an Xmodule?

And what do I have to do to remove an Ubuntu Linux install? Remove the partition for it and its swap and add the spare space to the existing partition? Or do I need to do something more arcane than that?

---

### Post by tseliot on 2006-05-26
Can you try my script for Breezy?
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

---

### Post by wog on 2006-05-28
How do I figure out which script I need?

---

### Post by wog on 2006-06-09
Do I match up the script number with the version number for nVidia installation, or is there something else I need to pay attention to?

---

