---
title: "pptpconfig permissions"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by neuralzen on 2007-02-08
I have just downloaded and installed pptpconfig to setup a VPN and it appears the program cannot write the files it needs to in order to save a connection. I'm certain it is a permissions problem, but I don't know how to give the program the permissions it needs to do what it needs to do. Any help would be greatly appreciated! Thanks!

---

### Post by jpeddicord on 2007-02-08
When you run pptconfig, prefix the command with 'sudo' if you are using the terminal, or 'gksu' if you are using Alt+F2.
For example, hit Alt+F2 and type this:```
gksu pptconfig
```

That should give you the necessary permissions needed to run it. :)

---

