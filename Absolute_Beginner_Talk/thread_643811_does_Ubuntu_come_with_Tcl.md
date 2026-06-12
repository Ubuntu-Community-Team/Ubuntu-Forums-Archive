---
title: "does Ubuntu come with Tcl"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Obalende on 2007-12-18
does Ubuntu come with Tcl? 

if so, how do I start it please - im an absolute beginner. 

If not, how may I download and install it - thanks a lot.

sorry if questions are too simple.

---

### Post by neotasic1 on 2007-12-18
navigate to a terminal Applications>Accessories>Terminal

type:  sudo apt-get install tclx8.3

You will be asked for your password - type this in the terminal (you will not see any password or asterisks) press enter

tcl will be downloaded and installed.

you can launch it in the terminal by command tcl

regards

---

### Post by -error on 2007-12-18
though i'm not a tcl guru, but i recall that tcl/tk is a set of libraries. so it isn't clear what you're wnated to "start". may be, tcl interpretator? then it's name is `tclsh'.
anyway you check if there is tcl/tk installed on your system by issuing `apt-get show tcl8.4', `apt-cache policy tcl8.4', `whereis tcl', etc.

---

### Post by meindian523 on 2007-12-18
> **Obalende said:**
> does Ubuntu come with Tcl? 

if so, how do I start it please - im an absolute beginner. 

If not, how may I download and install it - thanks a lot.

sorry if questions are too simple.

The only stupid questions are those which are not asked :)

---

### Post by Obalende on 2007-12-18
Thank you all very much - very helpful!

---

