---
title: "Thunderbird not upgrading"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by Virtuous on 2006-04-20
I'm using Thunderbird 1.0.7 and I have downloaded the thunderbird-1.5.tar.gz upgrade. I have followed the steps of extracting it and installing, the problem I have is that It seems that it won't upgrade 1.0.7 but instead it would be a seperate program of it's own. How can I fix this so that it can upgrade 1.0.7?:(

---

### Post by trent dillman on 2006-04-20
Well, you could uninstall Thunderbird via Synaptic, then symlink the new Thunderbird executable to somewhere in your path.

Let's say you installed the new version in /opt....

```
sudo ln -s /opt/thunderbird/thunderbird /usr/bin
```

Be sure the path to Thunderbird in the preceding command is correct!

If you have problems, delete the symlink in /usr/bin and instead make a script in /usr/bin with something like

```
#!/bin/bash
cd /opt/thunderbird
./thunderbird
```

If you go this route, be sure to chmod +x the new script.

---

### Post by OffHand on 2006-04-20
Don't uninstall 1.0.7. It's part of Ubuntu and should NOT be removed.
Instead just use 1.5.0.x and leave 1.0.7 alone.

---

### Post by openmind on 2006-04-20
[quote=subsonic_shadow]Don't uninstall 1.0.7. It's part of Ubuntu and should NOT be removed.
Instead just use 1.5.0.x and leave 1.0.7 alone.[/quote]

Thunderbird wasn't included at all with my version of Ubuntu. I installed it from the Repos.

---

