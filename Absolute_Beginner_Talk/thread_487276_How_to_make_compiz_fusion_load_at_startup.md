---
title: "How to make compiz fusion load at startup?"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by vjstar on 2007-06-28
How do I make compiz fusion load at startup without the need of typing *compiz --replace -c emerald* every time I log in?

---

### Post by VirtualTiger on 2007-06-28
Go to Preferences / Session.

Under Startup Program, choose the New button

enter in the command line:
```
compiz --replace -c emerald &
```

---

### Post by vjstar on 2007-06-29
I have a problem with that, it look likes it "blocks" the terminal:
[I]
Initializing fade options...done
Initializing trailfocus options...done
Initializing cube options...done
Initializing switcher options...done
Initializing expo options...done
Initializing scale options...done
Initializing rotate options...done
Initializing cubereflex options...done[/I]

like... I can't enter any new commands... it does show the *username$*

---

### Post by lepz on 2007-06-29
I had my compiz-fusion set to run from startup, everything worked ok. but my processors were running at 33% when idle compared to 3% when I started it from the terminal? so what the hell was going on there? I just start from terminal now.

---

