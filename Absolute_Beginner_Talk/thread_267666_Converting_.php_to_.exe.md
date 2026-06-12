---
title: "Converting .php to .exe ?"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by dez_cole on 2006-09-28
I just accidentally  downloaded the demo version of Prey as a .php, and when i go to open it with wine it cant open it . Is there any way i can convert a .php to an .exe?    Thanks alot!

---

### Post by sbergman27 on 2006-09-28
> **dez_cole said:**
> I just accidentally  downloaded the demo version of Prey as a .php, and when i go to open it with wine it cant open it . Is there any way i can convert a .php to an .exe?    Thanks alot!

Well, I'm not sure if what you got is what you thought you got.

In a terminal window, in the directory where the file exists, type:

```
file prey.php
```

or whatever the filename is.  The file command will identify most files and tell you what kind of file it is.

It might say it's html, or a php script, or a windows executable.

If it's a windows executable, you can just rename it to prey.exe or whatever.  Otherwise, what got downloaded was not what you expected.

---

### Post by dez_cole on 2006-09-28
ok i did what you said and this poped up 

> prey_demo_sp_mp.php: Zip archive data, at least v2.0 to extract


Should i just give up and dl it again or can i fix this.

---

### Post by sbergman27 on 2006-09-29
> **dez_cole said:**
> ok i did what you said and this poped up 



Should i just give up and dl it again or can i fix this.

Sounds like you got the right thing. It's a zip archive.

Rename it to prey_demo_sp_mp.zip

Open it with archive manager and extract.

I'll warn you, though, I would be surprised if Wine ran this.

Running windows apps under wine can be a tricky and agravating affair when it works at all.

You might have a look at [http://www.cedega.com](http://www.cedega.com) for a wine version that is especially for gaming, as well as a list of games officially supported.  Cedega is commercial, but you can get the code and compile it yourself, I believe, if you are up to it.

Also check out [http://www.tuxgames.com/](http://www.tuxgames.com/) for native Linux games.

---

