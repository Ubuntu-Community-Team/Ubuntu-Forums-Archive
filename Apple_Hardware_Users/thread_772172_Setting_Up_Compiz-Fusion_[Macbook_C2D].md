---
title: "Setting Up Compiz-Fusion [Macbook C2D]"
date: 2008-04-28
forum: Apple Hardware Users
---

### Post by jatoskep on 2008-04-28
I recently installed Ubuntu on my Macbook and would really like to set up the compiz-fusion features. I have seen that the crappy graphics chip in this thing has been black-listed, but apparently there is a way to get around that and make it run. If anyone could help 'twould be much appreciated.

EDIT: Forgot to mention, it is one of the newer Macbooks with the Intel GMA X3100.

---

### Post by cyberdork33 on 2008-04-28
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

---

### Post by gatlin on 2008-11-24
> **cyberdork33 said:**
> [https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

I followed those instructions but neither the Appearances pane under System works, nor does the terminal command.  Here is what I get when performing the command "sudo compiz --replace &" : 

```
gatlin@esther:~$ sudo compiz --replace &
[1] 10576
Checking for Xgl: gatlin@esther:~$ not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


```

I did a fresh install of Xubuntu, but then I installed ubuntu-desktop and performed a widely known command to completely wipe out Xubuntu.  I have a sneaking suspicion that was it, but maybe it's possible to re-enable everything.  I have a black MacBook from December 2006. Thanks!

---

