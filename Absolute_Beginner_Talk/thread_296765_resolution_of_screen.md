---
title: "resolution of screen"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by suresh_ktnv on 2006-11-10
Hi, 
   My system is Ubuntu 6.06 My Screen resolution is not changing. I want to edit sudo nano etc/X11/xorg.config file. In that screen resolutions are there for different depths. In that what parameter shold I changed to get 1200x1028 ?

---

### Post by ciscosurfer on 2006-11-10
In your /etc/X11/xorg.conf file, at the bottom will be a section called **Section "Screen"**.  Look for subsections that look like this:

**SubSection     "Display"**
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
[B]     EndSubSection

[/B] And add your desired resolution to the **Modes** line and surround it with quotation marks like above.  Make your changes, save the file, and close it.  Logout and log back in.  If that doesn't take, reboot.

---

### Post by bigken on 2006-11-10
run this from a terminal ;)

sudo dpkg-reconfigure-fgnome-phigh xserver-xorg

---

### Post by ciscosurfer on 2006-11-10
I'm not familiar with the -fgnome switch...does that tell dpkg-reconfigure that the frontend to use is Gnome?  I'm aware of the rest of the line.

So, yes.  Running this is a terminal would be a sound idea as well.  The OP wanted a way to manually edit though.

---

