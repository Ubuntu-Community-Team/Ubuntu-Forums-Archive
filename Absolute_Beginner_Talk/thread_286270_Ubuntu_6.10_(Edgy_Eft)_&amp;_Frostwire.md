---
title: "Ubuntu 6.10 (Edgy Eft) &amp; Frostwire"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by snoman1980 on 2006-10-27
Installed 6.10, and after that I go to [www.ubuntuguide.org](www.ubuntuguide.org).  I add repositories, and update.  Download and install java, when I set the download as default I notice there are only two options (6.06 Dapper there were three) after the download.  Then I d/l Frostwire.  Everything is done through terminal.  All commands are cut straight from the guide, but when I run Frostwire nothing happens.  I'm guessing java is at fault, but I'm not sure.  I'm a newB.

---

### Post by barbarian on 2006-10-28
same here:(

---

### Post by ThrobbingBrain66 on 2006-10-28
If you are sure that Java is installed correctly, try this:

```
sudo gedit /usr/bin/frostwire
```

then change (i think its the first line) from "sh runFrost.sh" to "bash runFrost.sh".  all should work well then.

if this doesn't fix your problem, you may not actually have the correct default java set.

---

### Post by barbarian on 2006-10-29
Thank you, it worked!:)

---

### Post by thrillhouse on 2006-10-29
Yup worked.  Any particular reason this doesnt work using sh?

---

### Post by snoman1980 on 2006-10-29
That, did it for me to.  Thanks alot.

---

### Post by blendmaster on 2006-10-29
Just don't do this:

```
sudo ln -sf /bin/bash /bin/sh
```

It really screws you up!

---

