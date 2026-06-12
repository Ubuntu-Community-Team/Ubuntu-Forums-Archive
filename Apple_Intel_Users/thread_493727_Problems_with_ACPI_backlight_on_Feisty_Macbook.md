---
title: "Problems with ACPI backlight on Feisty Macbook"
date: 2007-07-06
forum: Apple Intel Users
---

### Post by C0d3Runr on 2007-07-06
So, on an up-to-date Feisty install on a Macbook Core2Duo (2nd generation, I believe - purchased in April) I'm having some odd problems with the backlight.  The screen is turned off when I shut the lid, as I would expect it to be, but certain things can make it turn back on before the lid is reopened.  For instance, if I close the lid, the screen turns off.  If I then pull out the power cord without reopening the lid, the screen turns back on.  Can anyone suggest something that can be done about this?  It's driving me rather crazy, because I like to leave the machine always-on, and if the screen turns back on while the lid is closed I'm afraid it will overheat.

By the way, I see this behavior without gnome-power-manager running, so I think that the /etc/acpi scripts are the only factor, unless I'm mistaken?

Thanks in advance!
~Matt

---

### Post by ronocdh on 2007-07-07
This is one of my biggest complaints about Feisty performance on the MBP hardware. My suspend functionality is unusable (both to RAM and to disk), and so I've actually taken to shutting the machine down if I need to move it long distances. It's a pain, but I did it precisely to avoid this issue you're talking about, where the machine roasts itself if it's not sleeping.

Have you toyed around with PowerTOP? Sorry if it's off-topic, but I've heard that it's fairly sophisticated power management, and so maybe it would be better at scolding your system and keeping an off screen off. More likely, though, I think, is that the issue is related to the Mac hardware being poorly understood; I've read threads in here about the num lock key clicking on and off with the plugging in and unplugging of USB peripherals! (That was on the MBs, IIRC.)

---

### Post by C0d3Runr on 2007-07-07
Odd - Suspend, both to disk and to ram, worked fine for me out-of-the-box.  Do either of them work for you with X not running?  I'd be willing to guess that if both work on a MacBook OOTB and fail on a MacBook Pro OOTB, that the problem is related to the vid card drivers, the most significant difference between the two models.

But, PowerTop just monitors what parts of the system are causing you to use power - it doesn't try to DO anything about it, just monitor.  Besides, if all I wanted was a hacky solution I could shell script one easily enough; I'm more looking for an explanation, or at least a few people saying "me too!" so that I know this isn't just a misconfiguration on my end.

---

### Post by cyberdork33 on 2007-07-07
my guess is that the macbook is supposed to change the screen brightness when switching from AC to battery, and somehow it is not taking the fact that it is asleep into account.

---

### Post by C0d3Runr on 2007-07-08
FWIW, should anyone else stumble upon this later with the same problem - I just realized that it only happens when the system has been suspended and resumed, not on a fresh restart.  So, whatever the problem is, it relates to some piece of the system that isn't restored properly on resume from suspend... which i think makes it beyond my ability to troubleshoot.  Hopefully someone else fixes it in an upcoming kernel.  *shrug*  :)

---

