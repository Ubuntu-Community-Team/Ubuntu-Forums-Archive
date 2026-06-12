---
title: "xhost + / export DISPLAY=10.x.x.x not working ?"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-09
I tried :

"Edit the file /etc/gdm/gdm.conf. Find the line that says "DisallowTCP=true" and change it to read "DisallowTCP=false".

If it doesn't work immediately, restart the xserver, then you'll be fine."

for exporting app window to my pc ... 
but still not workign ...


is there someone who konws how to make sending app to another pc workign ??

thank you very much

---

### Post by patrick295767 on 2005-10-09
[http://www.wlug.org.nz/XFree86Notes](http://www.wlug.org.nz/XFree86Notes)

is there a way to use ssh ??? and xauth 
How ??

thank you very much

---

### Post by simon.schmidt on 2005-10-09
I'm not sure on what you are doing but you should try to set X11Forwarding to yes in the servers /etc/ssh/sshd_config 
the line should look like this:
```
X11Forwarding yes
```

and then connect with:

```
ssh -X ip.to.server
```

and then start a app:
```
xeyes
```

---

### Post by patrick295767 on 2005-10-10
The idea is as follows:

on the PC1 : xhost + IP_PC2

then:
rlogin IP_PC2
export DISPLAY=IP_PC2:0.0
xclock &

and xclock should appear on the PC1's screen...


-------------
but ssh is more secured than xhost ... 

Is there someone who has idea how it works ?

---

### Post by patrick295767 on 2005-10-10
What is the use with ssh +X ... ?
How to make it ?

thank you !

---

### Post by patrick295767 on 2005-10-12
[QUOTE=patrick295767]What is the use with ssh +X ... ?
How to make it ?

thank you ![/QUOTE]

Is there someone who could help me to make progress to export the application window from the remote PC to my screen ?

use of xauth maybe or ssh ??

I still dont know how to do it: display not found error

Thank you very much !

---

