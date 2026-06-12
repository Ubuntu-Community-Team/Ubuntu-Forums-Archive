---
title: "Onboard Sound"
date: 2005-05-27
forum: Absolute Beginner Talk
---

### Post by statto on 2005-05-27
Hiya

I just installed Ubuntu (Warty Warthog to be precise) a couple of days ago, but I seem to be having a bit of a problem.

I don't seem to be getting any sound at all. I've looked in the device manager and there are two sound blaster live! devices listed, an 'input device controller', and a 'EMU10K1X'. I now my sound chipset is on my motherboard, but i have no idea of the make or model, and i don't have any driver disks or anything.

If anyone has any ideas I'd be very grateful

ta!

p.s. a really dumb question here: i've got my webcam installed and working as far as i can tell, but what software should i use if i just wanna take a simple photo with it? Xsane doesn't seem to detect it, but i suspect that it is just for scanners.

---

### Post by apollyonis on 2005-05-28
That's normal for the SB Live! to show up as an input controller and sound card since it has a joystick port. You might try right clicking volume control -> open volume control -> File -> Change Device -> and change it to the Sound Blaster Live! and alter the volume from there.

In response to your second question, search in Synaptic for a program called Camorama - that allows you to use your webcam to save snapshots, etc. If the search pulls up nothing, make sure to go [Here - Extra Repositories](http://ubuntuguide.org/#extrarepositories) to make sure the GNOME Desktop Environment (Universe) repository is installed.

---

