---
title: "Startup and Shutdown Hangs"
date: 2011-12-27
forum: Any Other OS
---

### Post by Andy45 on 2011-12-27
Hello World! (LOL)
Recently I have encountered the problem of the computer getting stuck/hanging on shutdown. And now it doesn't even boot - also hanging. I can boot from LiveCD and choose recovery mode in grub bootloader. P.S. No GUI boot, so I can see what's happening.
Stats:
When starting, it begins loading everything like normal, then hangs on this line:
[INDENT][       2.676451] [<c010363e>] kernel_thread_helper+0x6/0x10
[/INDENT]An interesting note is that it passes the "Checking battery state" part of the boot successfully and does not get stuck until later, unlike most people who get frozen up at startup on both regular Mint and the RC.
When shutting down, it keeps going then hangs at:
[INDENT]checking for running unattended-upgrades:
[/INDENT]Computer is a Dell Dimension E520 with Linux Mint 10 LXDE (Julia). I am a Linux newbie. :( Avira Antivir is installed. I can boot a LiveCD and access my files from there. Normal booting works up to the grub bootloader. Memory test are all passed. The bug number for the shutdown problem I have is Bug #762203 [in Linux].

Now that you know everything about my problem, does anybody have even the slightest idea about what I could do to alleviate it?
Thanks in advance,
Andy45

---

### Post by Andy45 on 2011-12-28
also, is there any way to reset all startup entries from a live CD? because the startup problems began after I messed around with bum and startup manager.

---

### Post by Andy45 on 2011-12-28
If nobody can find how to solve it, I suppose I'll just have to reinstall Mint. In that case, which is better in terms of the overall usability and experience for basic emails, office, and music: Mint 12 Lisa GNOME or Mint 11 Katya LXDE? I was using LXDE before and liked it, but from what I've heard it has the same startup and shutdown bugs in the new version. I also tried Lisa GNOME on live CD, but it was considerably slower than the Julia LXDE I tried and installed previously. Maybe that's just for live CD though. Please tell me pros and cons of each or if there is a way to recover the system (though unlikely). Thanks!

---

### Post by thatguruguy on 2011-12-28
Have you considered posting your questions on the [Mint forum]("http://forums.linuxmint.com/")?

---

