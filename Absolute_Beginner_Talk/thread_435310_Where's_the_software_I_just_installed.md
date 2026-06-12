---
title: "Where's the software I just installed?"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by RedViking on 2007-05-06
So I've been installing a bunch of software in ubuntu, but I can't figure out how to use it once it's installed.  I'm used to just finding the *.exe file.  What's the ubuntu equivalent?  

Another thing.  I installed Wine, but when I try to open something with it, nothing happens.  The computer just sits there.  No error messages, no nothing.  How can I fix that?  

Thanks!

---

### Post by taurus on 2007-05-06
Most if not all the apps that you install will be in /usr/bin.  So if you want to run something, you can look in Applications menu first or just open a terminal, Applications -> Accessories -> Terminal, and type in the name of the program.

```
firefox
```

---

### Post by igknighted on 2007-05-06
> **RedViking said:**
> So I've been installing a bunch of software in ubuntu, but I can't figure out how to use it once it's installed.  I'm used to just finding the *.exe file.  What's the ubuntu equivalent?  

Another thing.  I installed Wine, but when I try to open something with it, nothing happens.  The computer just sits there.  No error messages, no nothing.  How can I fix that?  

Thanks!

There is no ".exe" extension, in theory any file extension could be executed in linux.  If you installed through synaptic, try looking in the "Applications" menu.  If no entry was added, try typing the name of the program into the terminal and hitting enter (or the first few letters and hitting tab for auto-complete to give you some options if that doesn't work).

To run a .exe with wine, open a terminal and cd to the directory the .exe is in, then run "wine application.exe"

---

### Post by RedViking on 2007-05-06
I typed the name of the program in the terminal and it said it wasn't installed (which would explain why I couldn't find it), but I just installed it.  I didn't use synaptic to install it.  I compiled it in the terminal with no errors (./configure, make, sudo make install, make clean).  Suggestions?

As for Wine, how do you access the cd rom from the terminal?  

Thanks again

---

### Post by taurus on 2007-05-06
And what is the name of the problem that you built from source?  If you build something from source, it will probably be in /usr/local/bin so look in there first.

```
ls -la /usr/local/bin
```

---

