---
title: "Path doesn't seem to work?"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by Redptc on 2007-12-29
I have been trying to load an application through 'wine'. It has been loaded but when I try to run it I can't change the directory in order to run the executable file.

There are ways around it I suppose but it should be straight forward .  I enter

    cd ~/.wine/drive_c/Program Files/"app"

The reply is that it is not a directory ~/.wine/drive_c/Program:

Which suggests it finds problems with the "Program Files" or the space between

What I'm I doing wrong? I am a beginner stumbling but would appreciate help on this one.:confused:

---

### Post by taurus on 2007-12-29
```
cd ~/.wine/drive_c/Program\ Files/"app"
```

or

```
cd ~/.wine/drive_c/"Program Files"/"app"
```

---

### Post by Redptc on 2007-12-29
Thanks, Taurus, it works like a dream, appreciate your help
:)

---

