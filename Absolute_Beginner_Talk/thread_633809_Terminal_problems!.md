---
title: "Terminal problems!"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by puterboy on 2007-12-06
I'm using gnome-terminal. However, it stopped working awhile ago. Doesn't work from the Applications menu, and doesn't work from the Alt-F2 menu. While in xterm, I tried to run it, and got this:

The program 'gnome-terminal' received and X Window System error
This probably reflects a bug in the program
The error was 'BadValue (integer parameter out of range for operation)'
(Details: serial 142 error_code 2 request_code 78 minor_code 0)

There's a note to the programmer, but it's too long to type by hand for me. I Googled the details, to no avail. Any ideas?

I've tried reinstalling and stuff, no dice

---

### Post by FakeOutdoorsman on 2007-12-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Probably to do with a buggy nvidia driver.  More info:
[gnome-terminal won't start]("http://ubuntuforums.org/showthread.php?t=462613")

[[nvidia-glx] gnome-terminal does not start when using Xinerama on the nvidia driver if COMPOSITE is on]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232")

---

