---
title: "No accelerated video on HP 6910p with Intel 965GM"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by EdwinF on 2007-12-02
I am a newbie to Ubuntu 7.10 and installed it next to Vista on some of my computers:[LIST]
[*]HP NC4000 with ATI Integrated graphics
[*]Mobile On Desktop PC (MSI 945GT SpeedsterA4R) with Intel 945GM graphics
[*]HP 6910p with Intel 965 Express graphics
[/LIST]
On the NC4000 and the 945GM bases system, graphics on Ubuntu look fancy as soon as I change visual effects from 'None' to 'Extra'. This is even possible on that old NC4000 with very poor graphics capabilities. On the brand new Intel 965, there is no way I can select 'Extra' or even 'Normal'.

Googling around, and I see people compiling their gernel to get this working - not really what I was looking for. Is there a much simpler solution for this?

I found this as a workaround, and it seems to work. However - what is it exactly that I now miss?

[I]Description: The PCI ID (8086:2a02) for the Intel 965GM video controller has been black-listed by Compiz-Fusion Manager in Ubuntu Linux 7.10. Reason for this is that the 965GM chip doesn't support the necessary pieces for video to work without using EXA accelerated architecture, which is something Ubuntu Linux 7.10 does not support.
Systems Affected: Inspiron 1420n
Impact: Metacity will be used by default instead of Compiz-Fusion. Due to this, one will be unable to turn 3D effects on the desktop.
Workaround: Edit the file (or create if does not already exist) /etc/xdg/compiz/compiz-manager and add the line:

SKIP_CHECKS="yes"

And restart the Gnome Display Manager by pressing Ctrl+Alt+Del at the same time.

NOTE: Enabling Compiz Fusion on this video chipset will disable video playback. [/I]

---

### Post by Peryl on 2007-12-05
o.O vista...

which did install first anyways?

---

