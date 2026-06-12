---
title: "hal-applesmc (Mactel PPA)/MBP 4,1: Minimum backlight level?"
date: 2008-11-24
forum: Apple Hardware Users
---

### Post by __david on 2008-11-24
Hello everybody,

is it possible to set a minimum level for backlight brightness?
I like to work with backlights level set to 1 in the evening. Sometimes gnome-power-daemon decreases the level, actually turning the display off. Is there a way to prevent that behaviour?

---

### Post by kosumi68 on 2008-11-24
> **__david said:**
> Hello everybody,

is it possible to set a minimum level for backlight brightness?
I like to work with backlights level set to 1 in the evening. Sometimes gnome-power-daemon decreases the level, actually turning the display off. Is there a way to prevent that behaviour?

Have you tried the mactel version of gnome-power-manager? It fixes a bug in g-p-m which yields precisely the behavior you describe.

[https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)

---

### Post by __david on 2008-11-24
Hi kosumi68,

thank you for your reply.

I think I am using the Mactel-PPA version of g-p-m, but will double-check that as soon as I’m back home (at work right now).

---

### Post by __david on 2008-11-24
I'm using the Mactel version of gnome-power-manager.

I have installed the following Mactel packages:
[LIST]
[*]gnome-power-manager
[*]hal-applesmc
[*]hid-dkms
[*]mbp-nvidia-bl-dkms
[*]xserver-xorg-input-synaptics
[/LIST]

Is there a way to fix that issue?

---

### Post by kosumi68 on 2008-11-24
> **__david said:**
> I'm using the Mactel version of gnome-power-manager.

I have installed the following Mactel packages:
[LIST]
[*]gnome-power-manager
[*]hal-applesmc
[*]hid-dkms
[*]mbp-nvidia-bl-dkms
[*]xserver-xorg-input-synaptics
[/LIST]

Is there a way to fix that issue?

This post to disable ambient auto-adjust:

[http://ubuntuforums.org/showpost.php?p=6240712&postcount=57](http://ubuntuforums.org/showpost.php?p=6240712&postcount=57)

Otherwise, I am puzzled as to what the problem is. The mactel patch prevents zero brightness, but allows very low values. The g-p-m auto-adjust has a design flaw in that it adjusts the brightness based on the current control level, which in turn gets updated to the actual brightness when updating the brightness manually. Thus, when adjusting manually and using ambient auto-adjust, one needs to set the brigtness higher than the indended value, so that when the adjuster kicks in (once every half minute or so), the brightness ends at a reasonable level.

---

### Post by __david on 2008-11-24
Thank you for your help. I will disable auto-adjust and set low default values. I like dark screens better anyway :)

---

