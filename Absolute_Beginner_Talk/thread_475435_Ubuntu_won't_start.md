---
title: "Ubuntu won't start"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by quercusrobur on 2007-06-16
Hi Have been running Ubuntu since about a year ago (Dapper Drake). Last night I attempted to burn a DVD - without warning the laptop crashed and died on me. When I tried to restart the machine the usual start up splash screen appeared after I'd selected the default option of staring Ubuntu from the grub menu. It gets as far as the 'mounting root file system' check box appearing on the splash screen before hanging, then going back to the grub screen, and not moving past the 'loading linux kernel' message.

I've attempted to restart in 'recovery mode', but this doesn't work either. Windows XP, also on the same laptop, loads fine by the way.

My copy of the Ubuntu book advises that "grub is probably corrupted". It then goes on to say "Don't worry, you can fix this!" and explains how I can fix grub from recovery mode using a "single user command line", by "going to /boot/grub and loading "menu.lst in a text editor".

What it doesn't explain is exactly how I do this!

Any ideas anyone??

---

### Post by Jimmyfj on 2007-06-16
If you are able to get into a command line prompt you could try:

sudo dpkg-reconfigure -a

This will fix many problems for you

---

### Post by quercusrobur on 2007-06-16
Thanks for your reply -  How do I bring up the command line in recovery mode? So far when I attempt to boot into recovery mode lots of text scrolls down the page before  finally stopping (sorry I can't be more specific, but I'm using a different computer and I'm working from memeory of what happened last night...)

By the way, I've also just downloaded Feisty Fawn and am thinking of simply doing a fresh install over the top of Dapper, but don't really want to lose all my emails and address book (everything else important is already backed up on a USB drive)  - will these be wiped if I simply do a fresh install or are these files saved to a different drive?

---

