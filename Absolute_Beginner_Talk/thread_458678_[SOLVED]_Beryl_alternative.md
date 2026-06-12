---
title: "[SOLVED] Beryl alternative?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by kernel tom on 2007-05-29
Basically the only thing I want is for my workspaces to zoom out into the cube so i can look at them "in space" and none of the other options that beryl comes with.

Are there any other applications out there containing only this feature? or little more?

thanks,
tom

---

### Post by Clay_Banger on 2007-05-29
i think compiz is what your after, does similar things to beryl, just not as customizeable.

It comes pre-installed on 7.04 machines..

---

### Post by testube_babies on 2007-05-29
Or you could just use beryl and deactivate all of the plugins you don't want.  But compiz is probably the way to go.

---

### Post by kernel tom on 2007-05-29
thanks for the fast response

I'm using Xubuntu 7.04 and it does not come pre installed... so I installed it then got this message

/usr/bin/compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
/usr/bin/compiz.real: No manageable screens found on display :0.0
/usr/bin/compiz: 47: metacity: not found

any ideas? or is there somethign taht will do the workspace cube thats already installed?

---

### Post by Clay_Banger on 2007-05-29
Try this:
```
compiz -replace
```

---

### Post by Ateo on 2007-05-29
The command that you use should be:```
$ compiz --replace&
```

---

### Post by kernel tom on 2007-05-29
ok so it works, however i have some questions

first off, i don't have it in any menu... and i have to run it from a terminal, and leave the terminal open...

anywhere i can adjust the effects and close the terminal and keep compiz running?

---

### Post by Clay_Banger on 2007-05-29
on google there are a few tools to configure compiz (google: "configure compiz")
the only one in the repos is gnome-compiz-manager

---

### Post by kernel tom on 2007-05-29
thanks a lot!

i'll play around with it

---

