---
title: "How to Disable X server and change the default run level"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by D_frag on 2006-09-12
I need to install the nvidia graphics driver for the 64 bit architecture 
and in the manual i read i have to disable X server and set the default run level on my  system such that it will boot to a VGA console. I dunno how ?
any help Also it said i have to kill all OpenGL applications

---

### Post by steve.horsley on 2006-09-12
Forget changing the default runlevel - all runlevels are identical in Debian. I really don't know why, but there it is.

You can prevent the X server from starting on boot with this command (Changes the first character of the file from upper to lower case):
**sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/s13gdm**
Correct it later by changing the name back to upper case.

You then need to stop the running X server with this command:
**/etc/init.d/gdm stop**
(you can use /etc/init.d/gdm start to restart it by hand if req'd).

---

