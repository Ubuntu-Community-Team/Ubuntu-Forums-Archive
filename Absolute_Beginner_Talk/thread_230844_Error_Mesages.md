---
title: "Error Mesages"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by project? on 2006-08-06
I got an error in synaptic package manager that says "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." 

First of all what does it mean?
How can i fix it?

---

### Post by wombat20 on 2006-08-06
You need to enter that command at the command line.  If you're not sure how to get a command line window up, use the main menus:

Applications -> Accessories -> Terminal

Then enter:
```

sudo dpkg --configure -a

```

You'll need to enter your password.  Hopefully someone will be able to give you a more thorough explanation of why this happened.

---

### Post by kebes on 2006-08-06
The error occured because something crashed during an installation step, so the "packaging information" is out-of-sync. You have to run the command that is mentioned in order to get everything back into working order. To put it simply the "dpkg --configure -a" will re-configure all the packages that were "half-done" when the program had an error. As the other post explains, you need to run the command:
sudo dpkg --configure -a

From a terminal (or you can go Alt+F2 to run a single command).

---

