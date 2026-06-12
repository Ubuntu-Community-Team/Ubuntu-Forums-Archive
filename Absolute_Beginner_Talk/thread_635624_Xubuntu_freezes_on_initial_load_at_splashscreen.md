---
title: "Xubuntu freezes on initial load at splashscreen"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by toucans on 2007-12-08
Hi,

When I boot the computer, it goes to the splash screen but hangs at about 15%.

I'm new to linux, and there's been a few problems so far. The live cd wouldn't initially run, when I added vga=771 noapic nolapic it worked. Then during installation when I chose guided partition, it locked up at 15%. I fixed this by choosing manual and formatting the drives.

I tried adding vga=771 noapic nolapic to the boot, but nothing changed. 

I've looked around on different forums and through documentation, but can't quite find an answer.
I'm using an hp tx1000
amd turion64 x2
nvidia 6150
xubuntu 7.10

Any help would be greatly appreciated!

---

### Post by PmDematagoda on 2007-12-08
Try adding nosplash to the GRUB entry.

---

### Post by toucans on 2007-12-08
That did it, Thank you!

---

### Post by PmDematagoda on 2007-12-08
No problem:), how is Xubuntu working out by the way?

---

### Post by toucans on 2007-12-08
Well, it only just started working:) Now I have to figure out how to get it to connect to the wireless network. Wired works at least!

---

