---
title: "Compiz in Ubuntu 7.10 ?"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by baysl on 2007-10-02
I'm wondering is Compiz in Ubuntu 7.10 already installed?

How do I turn it on?
And how do I use it to make my windows transparent?

---

### Post by LowSky on 2007-10-02
its under themes now... its one of the tabs

---

### Post by mysticmatrix on 2007-10-02
> **baysl said:**
> I'm wondering is Compiz in Ubuntu 7.10 already installed?

How do I turn it on?
And how do I use it to make my windows transparent?

It's turned on by default if your hardware supports it. 
Use general options to make any window transparent

---

### Post by baysl on 2007-10-02
Ok i got it I only have to set effects to EXTRA.

But I still cant find command to make my windows transperent?

---

### Post by Perfex on 2007-10-02
You need compizconfig-settings-manager it's in the synaptic

---

### Post by lava on 2007-10-02
I have kubuntu installed and I did the upgrade to 7.10. I'm not sure how to turn on compiz. I tried compiz --replace and all I got was:

Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1400x1050) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity
no /usr/bin/metacity found, exiting

I'm not even sure what I need to do. Can anyone point me in the right direction?

---

### Post by mysticmatrix on 2007-10-02
> **lava said:**
> I have kubuntu installed and I did the upgrade to 7.10. I'm not sure how to turn on compiz. I tried compiz --replace and all I got was:

Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1400x1050) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity
no /usr/bin/metacity found, exiting

I'm not even sure what I need to do. Can anyone point me in the right direction?

Which graphics card are you using?
TRy decreasing the resolution.

---

### Post by lava on 2007-10-02
> **mysticmatrix said:**
> Which graphics card are you using?
TRy decreasing the resolution.

forgot to mention that. This is what I'm on:

Thinkpad T41
KUbuntu 7.10 
ATI Radeon R250 [Mobility FireGL 9000]

I can't decrease the resolution since 1400x1050 is the native resolution of my laptop. I've heard somewhere about decreasing the color-bits but I don't know how to do that.

I tried running 
SKIP_CHECKS=yes compiz --replace

all my window bar icons were gone. I guess I need to specify window decoration somehow, and only the 70% of my screen on the left side displayed anything. The right side was garbage.

---

### Post by Perfex on 2007-10-02
1. Install the restricted Ati driver ...reboot

2. sudo apt-get install xserver-xgl ...reboot

3. sudo apt-get install compizconfig-settings-manager

you can configure compiz in the appearance menu

---

