---
title: "mouse keyboard fsck problem"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-06-07
I'm running Feisty, with WinXP and Dapper still installed. I've had intermittent mouse problems, it throws itself round the screen opening random windows, so yesterday I swapped to a USB mouse, and that seemed OK.

When I booted this morning, I couldn't log in - the cursor was flashing in the username box, but nothing happened when I typed, F10 didn't do anything. I rebooted, and got the same, but with no mouse either. Tried XP, forgot until I was half way through loading that the keyboard was OK up until the GUI loaded, otherwise I wouldn't have been able to choose an OS!

Put my old PS2 mouse on, went back to Feisty, and during boot got "Superblock last mount time is in the future. FIXED", then "FSCK died Exit Status 1". However the keyboard let me log in.

I've been looking those up here, but many of the instructions are a bit beyond me.

I didn't get the exact superblock msg - is there a way to check the log from before the GUI loads? I've looked in system log, but I can't find a log from before the GUI loads.

And is it likely that a mouse could be causing this? I don't think so, but it's the only change I've made.

TIA

---

### Post by gerscht on 2007-06-07
you can see the logfiles from theconsole (use CTRL-ALT-F3 to open a new console) with
```
sudo less /var/log/messages
```
I don't know whether a mouse can cause this problem, though. Look for USB (OHCI) related error messages in the log file, it might lead you in the right direction.

---

### Post by freesitebuilder on 2007-06-07
Very odd - I can change to the USB mice (I've tried a couple) and no problems. But as soon as I reboot, I get the same errors - superblock, FSCK error, then can't login. I'll start looking for USB mouse problems.

There's a bug here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84762/](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84762/)

---

