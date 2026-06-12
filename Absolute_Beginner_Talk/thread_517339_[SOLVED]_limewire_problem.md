---
title: "[SOLVED] limewire problem"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by kinngg on 2007-08-04
i cant see anythin on my limewire.. its jus a white display everytime i open it.. wats da problem? thx

---

### Post by Brunellus on 2007-08-04
define "white display"

---

### Post by lepz on 2007-08-04
Are you running compiz/fusion?

---

### Post by kinngg on 2007-08-04
i cant see anything.. its jus white wit title bar.. n yes im runnin compiz-fusion

---

### Post by ghiocel on 2007-08-09
I have the same problem! It used to work properly, but now it's just blank and the titlebar.  Does it have a link with the fact that I have activated the desktop effects (cube workspace etc)?

---

### Post by Trab on 2007-08-09
a simple solution for frostwire when it had that issue (i believe limewire is the same way.)
> 
This is the easiest solution:
1. Open your favorite text editor. Paste the following:
```
#!/bin/bash
export AWT_TOOLKIT=MToolkit
export HOSTNAME=localhost
/usr/bin/frostwire

```
NOTE: you might need to replace the last line with "/opt/FrostWire/runFrost.sh" (without the quotes) depending on how you installed Frostwire.

2. Save the file as something, maybe "launch_frostwire"
3. Right-clcik on the file and select 'properties'; click the 'permissions' tab, then tick 'allow executing file as program'; click 'close'
4. Create a new launcher for Frostwire with the path being /path/to/launch_frostwire

Enjoy!

obviously change frostwire to limewire where applicable.

---

### Post by ghiocel on 2007-08-09
OK..how do I create a new launcher..? sorry, but I'm newbie

---

### Post by Trab on 2007-08-09
right click on your panel, click add to panel, click custom application launcher.

---

