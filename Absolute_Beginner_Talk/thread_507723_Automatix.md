---
title: "Automatix"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by Fire-Eyes on 2007-07-23
Help please.
My husband thought this would be cool. Well, it is not. and now I can not uninstall the stupid thing. Can anyone help me?
I see there are other threads, but no one seemed to be helping then either.
Thank you in advance

---

### Post by laidback on 2007-07-23
Mine appears in the Synaptic package manager, which I think would also allow me to remove it. System>Administration>Synaptic package manager. You'll need to enter your regular password when asked.

---

### Post by Seisen on 2007-07-23
In the terminal put this. To open up the terminal go to Application>Accessories>Terminal

```
sudo apt-get remove automatix2
```

---

### Post by Fire-Eyes on 2007-07-23
ok...I get this message
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

please be gental with me..I am new to this stuff

---

### Post by aysiu on 2007-07-23
Close Synaptic completely.

Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo dpkg --configure -a
``` Enter your password when prompted.

---

