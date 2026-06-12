---
title: "Booting from USB pendrive"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by riyapiko on 2008-01-13
Hello, I booted Ubuntu from USB Pendrive, but just as it gets to show the desktop, the screen shows nothing but few "shaggy" lines. It makes the start up sound thing, but the desktop doesn't show up. I have followed these steps written in this:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

I can't take a screen shot so I don't know how to explain it very well, but I think it boots up fine, (it shows some errors and file not found in the boot up, but its the same with LiveCD that I have it booted right now, and its working fine).

Thank you

---

### Post by napzilla on 2008-01-13
Can you bring up a different pseudoterminal (i.e. try <Ctrl> + <Alt> + <F1>)? If so, then you can get a look at the X server log (*tail /var/log/Xorg.0.log* or the syslog (*tail /var/log/syslog* and perhaps find out what's going wrong. Use *less* instead of *tail* to view the entire log, if need be.

---

### Post by riyapiko on 2008-01-13
Thank you for your help. i have solved the problem and it was that my casper-rw was formatted as FAT32 somehow. I don't know how that might have affected, but it is working now. One thing I want to learn is that when I change to [Ctrl] [Alt] [F1], how do i go back to GUI?

Thank you

---

### Post by napzilla on 2008-01-15
The GNOME desktop is usually run in pseudo-terminal seven, so <Ctrl> + <Alt> + <F7> should return you there. If that doesn't work, then your desktop may have accidentally been moved, so try replacing <F7> with <F8> or <F9>. TTYs 2-6 are also available to you as bash terminals, and you can access these by using the Function Key with the appropriate number (e.g. <F5> for TTY 5).

To be honest, I really don't know much about how the TTY consoles work in Linux, nor have I ever been able to find much information on them. Here is a page at linux.com I stumbled upon that discusses them briefly: [http://www.linux.com/base/ldp/howto/Text-Terminal-HOWTO-7.html](http://www.linux.com/base/ldp/howto/Text-Terminal-HOWTO-7.html)

---

