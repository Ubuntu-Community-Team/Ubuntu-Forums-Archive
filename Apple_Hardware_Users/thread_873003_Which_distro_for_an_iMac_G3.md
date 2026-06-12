---
title: "Which distro for an iMac G3?"
date: 2008-07-28
forum: Apple Hardware Users
---

### Post by [MEH] on 2008-07-28
Hi All,

This is my first post on the forum. I am looking for a bit of advice.

I have an iMac G3, 128MB RAM, 40GB HD, 600MHz G3 processor and it is currnetly running Mac OS 10.2.8.

Can someone give me an idea of which version of Linux i would want to run on this machine? Also, is it possible to keep my current OS X system on the iMac, and then install Linux alongside it?

Thanks in advance for any help.

---

### Post by stream303 on 2008-07-28
Yes, it is possible to run many ppc distros, such as Debian, Ubuntu, Fedora, Gentoo, etc, but the big question with only 128 mb ram, is it worth it?

The G3 iMacs need manual reconfiguration of their xorg.conf file, and also at times yaboot.conf to get them to work.  See the powerpc faq, and the powerpc known-issues faq in particular.

While a 600mhz G3 is roughly equivalent to a 1.2ghz Intel machine (very roughly :), ram will be your limiting factor, unless you don't mind running very lightweight applications, and/or the commandline.

If that is ok, and you are prepared to go in and edit files without throwing the iMac through the window, then go ahead. :)  Just being honest here.

You can dual-boot Linux and OSX, but again, especially with the G3 iMacs, you may need to be comfortable with reinstalling OSX, and possibly manually configuring your yaboot bootloader.

I don't want to put you off installing it, but just be prepared to put in some time, since they aren't just drop-in installations for the most part.

That being said, and since this is an Ubuntu forum, I recommend using the "alternate" images to install from especially with only 128mb ram:

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

