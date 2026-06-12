---
title: "Media Error"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by Topaz on 2006-04-15
What do I do, google had no answer?

---

### Post by trent dillman on 2006-04-15
The easy way:

Install Automatix on Breezy, or BUMPS on Dapper. Then install all the multimedia codecs.

---

### Post by Topaz on 2006-04-15
[QUOTE=trent dillman]The easy way:

Install Automatix on Breezy, or BUMPS on Dapper. Then install all the multimedia codecs.[/QUOTE]
Have automatix on my system desktop and ran it, and reran codecs, get same error .

---

### Post by trent dillman on 2006-04-15
check the folder /usr/lib/win32 and /usr/lib/codecs

If /usr/lib/win32 is empty, do this:

```
cd /usr/lib
sudo rmdir win32
sudo ln -s codecs win32
```

---

### Post by Topaz on 2006-04-15
[QUOTE=trent dillman]check the folder /usr/lib/win32 and /usr/lib/codecs

If /usr/lib/win32 is empty, do this:

```
cd /usr/lib
sudo rmdir win32
sudo ln -s codecs win32
```[/QUOTE]

I did a
XXXXXX@oooooo:~$ /usr/lib/win32
bash: /usr/lib/win32: No such file or directory
xxxxxx@000000:~$ /usr/lib/codecs
bash: /usr/lib/codecs: No such file or directory
xxxxxx@000000:~$ cd /usr/lib/codecs
bash: cd: /usr/lib/codecs: No such file or directory
xxxxxx@oooooo:~$ cd /usr/lib/win32
bash: cd: /usr/lib/win32: No such file or directory

ls -la |more in /usr/lib/win32 and /usr/lib/codecs and got
xxxxxx@oooooo:/usr/lib$ sudo rmdir win32
rmdir: `win32': No such file or directory
xxxxxx@oooooo:/usr/lib$ sudo ln -s codecs win32
xxxxxx@oooooo:/usr/lib$ sudo rmdir win32
rmdir: `win32': Not a directory

---

### Post by trent dillman on 2006-04-15
That's odd...

Open synaptic and search for w32codecs to see if it's installed. If so, check the properties to see where the codecs got installed. They need to be in /usr/lib/win32/

---

### Post by Topaz on 2006-04-15
[QUOTE=trent dillman]That's odd...

Open synaptic and search for w32codecs to see if it's installed. If so, check the properties to see where the codecs got installed. They need to be in /usr/lib/win32/[/QUOTE]

That was it, no w32codecs. When I did all my installs how did the mutimedia programs miss it. The one site said it was downloading and installing needed files.
Thank you very much.

---

