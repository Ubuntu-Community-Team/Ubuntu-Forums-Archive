---
title: "Running .sh files"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by Zoxc on 2006-04-30
I made this file build.sh:
```
#!/bin/sh

mcs -pkg:gtk-sharp "/root/Mono/test.cs"

```

When I run it from Nautilus, nothing happens. If I run the file from Terminal, it works. What am I doing wrong?

---

### Post by mostwanted on 2006-04-30
[QUOTE=Zoxc]I made this file build.sh:
```
#!/bin/sh

mcs -pkg:gtk-sharp "/root/Mono/test.cs"

```

When I run it from Nautilus, nothing happens. If I run the file from Terminal, it works. What am I doing wrong?[/QUOTE]

It works from Nautilus as well, it just doesn't launch a terminal to show its output.

---

### Post by Zoxc on 2006-04-30
How come a tricky little "test.exe" pops up if I run the script from terminal? This don't happen in Nautilus. When double-click the script and press "Run in terminal" from Nautilus, Terminal just popups with a black background (normally white) then it closes instantly.

---

