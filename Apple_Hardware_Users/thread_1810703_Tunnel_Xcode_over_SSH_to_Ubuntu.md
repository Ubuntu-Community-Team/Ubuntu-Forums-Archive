---
title: "Tunnel Xcode over SSH to Ubuntu"
date: 2011-07-23
forum: Apple Hardware Users
---

### Post by cipherboy_loc on 2011-07-23
Is it possible to tunnel Xcode over SSH (or another protocol) to an Ubuntu box? I have successfully launched xterm from a Mac OS X box (and had it spawn xeyes, xcalc, etc) and had it display on the Ubuntu box, but upon launching Xcode, it displays on the Mac's display, not Ubuntu's display. I believe Mac OS X uses a different display manger (though they do include X), so SSH might not work. 


Cipherboy

---

### Post by nevius on 2011-07-23
I think you will need a full remote desktop session (i.e. VNC / Screenshare) to run the native mac apps. You should be able to tunnel GUI apps that you install through macports (because they use X11).

> **cipherboy_loc said:**
> Is it possible to tunnel Xcode over SSH (or another protocol) to an Ubuntu box? I have successfully launched xterm from a Mac OS X box (and had it spawn xeyes, xcalc, etc) and had it display on the Ubuntu box, but upon launching Xcode, it displays on the Mac's display, not Ubuntu's display. I believe Mac OS X uses a different display manger (though they do include X), so SSH might not work. 


Cipherboy

---

### Post by scorp123 on 2011-07-25
> **cipherboy_loc said:**
> Is it possible to tunnel Xcode over SSH (or another protocol) to an Ubuntu box? I don't think so. Native Mac OS X applications such as XCode use Apple's own framework called "Cocoa" and not the more traditional X11 protocol. You won't be able to tunnel that through SSH using e.g. the "-X" flag.

What you could do is to use e.g. TeamViewer:

[www.teamviewer.com](www.teamviewer.com)

They have packages for Linux, Mac and Windows and it's totally easy to use. Non-commercial / hobbyist use is free.

---

