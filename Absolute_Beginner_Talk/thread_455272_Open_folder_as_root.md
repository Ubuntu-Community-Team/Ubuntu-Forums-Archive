---
title: "Open folder as root"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by JordanII on 2007-05-26
How can I open a folder as if I was logged in as root? Thanks!

~Jordan

---

### Post by Bachstelze on 2007-05-26
You mean, using the GUI ? I wouldn't really recommend it but do as you wish...

```
gksudo nautilus
```

---

### Post by JordanII on 2007-05-26
> **HymnToLife said:**
> You mean, using the GUI ? I wouldn't really recommend it but do as you wish...

```
gksudo nautilus
```

I mean that I need to be able to copy a file to the gnome-applet folder but it won't let me. Thanks!

~Jordan

---

### Post by JordanII on 2007-05-26
It worked, thanks!

~Jordan

---

### Post by Sparkster185 on 2007-05-26
> I mean that I need to be able to copy a file to the gnome-applet folder but it won't let me. Thanks!

Just FYI, you can copy files via the command line.  I find it safer to execute commands as root one at a time.  You could just execute a cp command with "sudo" in front of it.

```

sudo cp <source> <destination>
```

For more info on how cp works, check the man page via "man cp".

---

