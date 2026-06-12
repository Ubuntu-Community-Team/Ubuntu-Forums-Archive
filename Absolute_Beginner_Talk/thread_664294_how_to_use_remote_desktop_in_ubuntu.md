---
title: "how to use remote desktop in ubuntu"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by saurabh srivastava on 2008-01-11
hi sir
        I m using ubuntu .i want to use other desktop via remote desktop.Actually i live in hostel nd here ip connection is given..
plz help me..:mad:

---

### Post by Rocket2DMn on 2008-01-11
Are you trying to connect to a windows machine or another linux machine?
You should be able to use Application->Internet->Terminal Server Client as it supports a bunch of protocols.  "vncviewer" is nice for viewing other linux machines since vnc is a popular remote desktop protocol commonly used in linux.

---

### Post by saurabh srivastava on 2008-01-11
i m trying to excess a windows XP desktop..

---

### Post by Rocket2DMn on 2008-01-11
Unless that XP box is running a VNC server, you will probably connect to the box with the RDP protocol using Terminal Server Client.  That machine needs to have remote desktop enabled.  You can type in the computer's IP along with the username and password to get a desktop session on that machine.

---

### Post by ahvargas on 2008-01-11
you can try krdc and desktop share in windows.

---

### Post by beercz on 2008-01-11
gnome-rdp?

In the repos

---

