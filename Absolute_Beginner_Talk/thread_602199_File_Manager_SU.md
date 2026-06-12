---
title: "File Manager SU ???"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Certified Angus Beef ® on 2007-11-04
How does one get su/sudo privileges while in the graphical file manager??
I need to delete files and do stuff .... 

Anyone help would be great.
--
Angus ®

---

### Post by FuturePilot on 2007-11-04
Assuming you're using Ubuntu (Gnome) launch Nautilus from a terminal like so
```
gksudo nautilus
```
That should do it:)

---

### Post by HereInOz on 2007-11-04
Open a terminal and type:

gksudo nautilus

Enter your password when asked and nautilus will open in root.  Be careful there as anything is possible.

You will need to leave the terminal open to maintain that session of Nautilus.

---

### Post by -grubby on 2007-11-04
open a terminal and type:

```
gksudo nautilus 
```

---

### Post by Hayden on 2007-11-04
> **nathangrubb said:**
> open a terminal and type:

```
gksudo nautilus 
```
Why is 'gksudo' recommended, when 'sudo' works also?

---

### Post by Certified Angus Beef ® on 2007-11-04
Thank You

??
What does the "gk" indicate?
Do I get the same thing using just "sudo"?

---

### Post by Hayden on 2007-11-04
I don't know what the "gk" stands for, but I did find this - [_** Running Sudo Graphically**_]("http://psychocats.net/ubuntu/graphicalsudo.php")

---

### Post by TeaSwigger on 2007-11-04
sudo for running commands as root such as in a terminal

gksu for running GUI apps as root in ubuntu and Xubuntu

OR

kdesu for running GUI apps as root in Kubuntu.

The distinctions are calculated to test our capabilities at processing unexpected inputs in a repetitive pattern under a set number of variable conditions ;)

---

