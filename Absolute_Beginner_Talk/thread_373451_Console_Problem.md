---
title: "Console Problem"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by Steel Bovine on 2007-03-01
I do all my command-line stuff in the "terminal."  So its like I'm married to the GUI, but it was a shotgun wedding because when I try to access any of the consoles (ctrl-alt-fx) the screen is a bunch of garbled colors and nonsense.  This is the case whether I use ATI's proprietary driver or the open driver.  It happens whether I have one or both of my monitor plugged in.

I have an ATI Radeon X1900GT.  It is DVI-only with 2 connections.

Ideas?

---

### Post by taurus on 2007-03-01
Can you do all your run, running your commands, from a terminal, Applications -> Accessories -> Terminal?

---

### Post by Steel Bovine on 2007-03-01
Yes, everything works from Terminal.

This is not a life or death issue, I just wish I could use the consoles.

---

### Post by confused57 on 2007-03-01
> **Steel Bovine said:**
> Yes, everything works from Terminal.

This is not a life or death issue, I just wish I could use the consoles.
What you could try temporarily is reboot, highlight your Ubuntu entry in grub, press "e" to edit, then in your kernel line, remove the word "splash", then press "b" to boot.   Once you're booted into Ubuntu, then try ctrl+alt+F(1-6) to access a console...may or may not work.  If actually does work, you'd need to make it permanent in your /boot/grub/menu.lst

---

### Post by Steel Bovine on 2007-03-01
> **confused57 said:**
> What you could try temporarily is reboot, highlight your Ubuntu entry in grub, press "e" to edit, then in your kernel line, remove the word "splash", then press "b" to boot.   Once you're booted into Ubuntu, then try ctrl+alt+F(1-6) to access a console...may or may not work.  If actually does work, you'd need to make it permanent in your /boot/grub/menu.lst

This did not work.  What was it intended to do?

---

### Post by confused57 on 2007-03-01
> **Steel Bovine said:**
> This did not work.  What was it intended to do?

I think it's related to framebuffer support in the kernel or video driver?  See this thread, starting with reply #6:
[http://www.ubuntuforums.org/showthread.php?t=352484](http://www.ubuntuforums.org/showthread.php?t=352484)

---

### Post by Steel Bovine on 2007-03-01
I apologize.  This method **does** work and my issue is now solved.  Thank you.

---

### Post by confused57 on 2007-03-01
> **Steel Bovine said:**
> I apologize.  This method **does** work and my issue is now solved.  Thank you.
No apology needed...glad it worked for you.

---

