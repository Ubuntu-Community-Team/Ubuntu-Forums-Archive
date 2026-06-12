---
title: "ok I installed PlanetShift now how to start it"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Shadowmeph on 2008-02-26
I installed planet shift now I am not sure how to start it when I try to use the desktop starters I get "Failed to execute child process "/opt/PlaneShift/updater" (Permission denied)"  I am the only one that uses this computer and I am wondering how do I get permission to start this game?

---

### Post by herbster on 2008-02-26
How did you install it exactly?

---

### Post by Crooksey on 2008-02-26
Edit the launcher, and prefix it with "sudo".

It needs root privlages to download and install game updates.

---

### Post by Shadowmeph on 2008-02-26
to install I used $ sudo ./PlaneShift_CBV0.3.020-x86.bin

---

### Post by herbster on 2008-02-26
Is it a command-line game or a GUI game? If GUI, you probably should prefix the launcher with "gksudo"

---

### Post by Shadowmeph on 2008-02-26
I don't know if its command line or not how do I tell?

---

### Post by herbster on 2008-02-27
Yeah do what Crooksey said. Right-click the launcher and in the command field put "sudo" at the beginning. If that opens it up, you're good, if not, try "gksudo" instead of sudo. One surely will work as it just needs root priveleges. Of course, you'll be prompted for your password when you run the launcher now.

---

### Post by dtgolder on 2008-03-08
I had to put a symbolic link in my home directory to get this to work:

ln -s /opt ./opt

---

