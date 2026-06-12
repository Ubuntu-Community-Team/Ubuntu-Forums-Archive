---
title: "Connect to another computer on my network"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by firebirdworks on 2006-10-12
I have this network of three computers.  If I want to run a linux command, aka "sudo eject -t /dev/cdrom" on my windows, is this possible?

Thanks again for the user friendly fourms.

---

### Post by gosh on 2006-10-12
> **firebirdworks said:**
> I have this network of three computers.  If I want to run a linux command, aka "sudo eject -t /dev/cdrom" on my windows, is this possible?

Thanks again for the user friendly fourms.

Can you explain a bit more?
Are these all three Linux computers of do the run Windows?
Or why would you want to run a Linux command in Windows?
Or do you just want to open a terminal and type the command?
:-k

---

### Post by seuaniu on 2006-10-12
If you mean "open up a terminal on my linux box, type something similar to `sudo eject -t cdrom', and have the cdrom on my windows box open", I doubt there is an easy way to do that.

If you have your windows box set up with vnc/nx/remote desktop, you should be able to use a client on your linux box to connect, and eject the windows cdrom from there.

A quick google search turns up different "eject" commands for the windows terminal, which leads me to believe that you can get a telnet* or (preferably) ssh server running on your windows box and create a quick script to login, run your eject command, and logout.

Good luck!

* Default telnet warning: BEWARE TELNET!  If you are running a telnet server, all of your communications are in plain text, including your password. On unixy systems, ssh is the only way to go these days.:)

---

