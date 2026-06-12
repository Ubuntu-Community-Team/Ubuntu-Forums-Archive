---
title: "HELP: Compiz Fusion under Gutsy"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by takuhii on 2007-10-18
I am having some Compiz issues under Gutsy. Firstly it won't display any borders on the windows, running GTK-WINDOW-DECORATOR gives me this message in Terminal:

```
gtk-window-decorator: error while loading shared libraries: libwnck-1.so.18: cannot open shared object file: No such file or directory
```

if I run COMPIZ in terminal, it gives me this:
```
compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz (core) - Fatal: No manageable screens found on display :0.0
```

This is driving me mad. I have the latest NVIDIA drivers installed using ENVY, and NO other Decorators/Managers running except Compiz. I try COMPIZ --REPLACE, but this just runs COMPIZ as it already stands. I have a COMPIZ entry in my STARTUP SESSION that I placed there when I used COMPIZ FUSION under FEISTY, do I need to remove my own entry, or does COMPIZ --REPLACE need declaring manually when GUTSY starts???

Someone help, I am a total N00B at this...

---

### Post by mikeyphi on 2007-10-18
I installed the compiz GUI using Synaptic - that gave me plenty of decorations with very few problems!
I used this guide: [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---

