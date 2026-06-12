---
title: "Av Clamscan"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by lynx2cross on 2006-01-29
I did a clamscan and the results came back with one infected file, but I don't know which file it is or how to fix this.  I looked through the results and everything said ok so I don't see what's infected.  Any help please.  

By the way is there another virus program I can use that has a gui interface instead of AV which is command line only.

---

### Post by Perfect Storm on 2006-01-29
[http://ubuntuforums.org/showthread.php?t=88357](http://ubuntuforums.org/showthread.php?t=88357)

---

### Post by hen3rz on 2006-01-29
you can install clamTK? Its a gui front end for clamav

```
sudo apt-get install clamtk
```

or you can go via synaptic.

---

### Post by lynx2cross on 2006-01-29
Thanks I'll try the gui version.  Not quite sure I understand the first response, I went to the link and there is a lot information to install programs but doesn't explain what it's all for.

---

### Post by lynx2cross on 2006-01-29
I just installed clamtk but I don't see the program listed in the applications menu.  How do I access the program?

---

### Post by Perfect Storm on 2006-01-29
[QUOTE=lynx2cross]Thanks I'll try the gui version.  Not quite sure I understand the first response, I went to the link and there is a lot information to install programs but doesn't explain what it's all for.[/QUOTE]

It's for compiling. The program which is shown in the thread comes as a source.

---

### Post by hen3rz on 2006-01-29
To run clamtk simply type clamtk in the terminal or you can create a launcher by right clicking on the dekstop and selecting create launcher... and filling out the boxes typing clamtk in the command field box.

---

### Post by lynx2cross on 2006-01-29
I installed xfprot and everything went great, I'm new to Linux so I was nervous about using the command line but it installed with no problem my next question is should I leave the default setting as they are or should I change anything before I do a scan.

---

### Post by Perfect Storm on 2006-01-30
It really depends what you want and what to scan.

First thing you want to change is **Path to scan** and change it to where you want to scan.

You may also select **Scan for other various malware[b] and [b]enable neural network virus detection**.

---

