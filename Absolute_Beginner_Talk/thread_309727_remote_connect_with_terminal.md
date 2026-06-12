---
title: "remote connect with terminal?"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by Y4CcduyctJL3 on 2006-11-30
is it possible to use terminal like a dumb terminal emulator to connect to a remote machine with vt100/ansi support and ssh?

---

### Post by bodhi.zazen on 2006-11-30
> **coffeejoe said:**
> is it possible to use terminal like a dumb terminal emulator to connect to a remote machine with color support?

Yes. ssh

[introduction to ssh](http://www.suso.org/docs/shell/ssh.sdf)

Start here: [Ubuntu how to ssh](https://help.ubuntu.com/community/SSHHowto)

---

### Post by Y4CcduyctJL3 on 2006-11-30
well, that works to an extent, but it doesn't seem to accommodate the server being able to move the cursor around or set the color of the text.  is there a way to turn that on that i'm overlooking?

---

### Post by bodhi.zazen on 2006-11-30
> **coffeejoe said:**
> well, that works to an extent, but it doesn't seem to accommodate the server being able to move the cursor around or set the color of the text.  is there a way to turn that on that i'm overlooking?

Could you be more specific. What type of color? Last time I used ssh ls and the CLI was in color. Is you server configured for color ? Or are you asking about X forwarding ?

---

### Post by Y4CcduyctJL3 on 2006-11-30
no, there's no x forwarding.  just text.  i'm trying to access a practice management system for a dr's office.  the software all runs server-side, and creates menus with ascii text and it uses different colors to make the screen legible and uses cursor movement to update individual feilds on the screen.  when i access it with ssh it's all monochrome and the screen isn't drawn correctly.  that is to say that things are in the wrong place.  it workes in acuterm (w2k) with vt100 emulation.

---

### Post by Y4CcduyctJL3 on 2006-12-01
i just looked on one of the local terminals at the office and it looks like they're setup to use "vt420pc"  those machines use kde so they're using konsole to connect so i can't just use the command from that one unfortunately, but here's what's in the launcher file.

```
root@pc_1_14:/home/mfx014/Desktop# cat Medformix.desktop
[Desktop Entry]
Comment=
Comment[en_US]=
Encoding=UTF-8
Exec=**/opt/kde/bin/konsole -schema WhiteOnBlack -keytab vt420pc -miniicon mfx -T Medformix -e ssh 10.1.10.1**
GenericName=
GenericName[en_US]=
Icon=mfx
MimeType=
Name=Medformix
Name[en_US]=Medformix
Path=
StartupNotify=true
Terminal=false
TerminalOptions=
Type=Application
X-DCOP-ServiceType=
X-KDE-SubstituteUID=false
X-KDE-Username=
```does anyone know what a comparable gnome-terminal command line would be?

---

