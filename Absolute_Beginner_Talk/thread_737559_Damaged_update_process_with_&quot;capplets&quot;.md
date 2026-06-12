---
title: "Damaged update process with &quot;capplets&quot;"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by milesbh on 2008-03-27
I was updating my Ubuntu 7.10 when it came to "capplets" (i can't quite remember) and basically, the progress bar wasn't moving and it was stuck on this package, so i killed the update process and restarted the computer, and now when I try to install the updates, it says:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

so i run ```
sudo dpkg --configure -a
``` and it stays on this:

```
Setting up capplets-data (1:2.20.1-0ubuntu1) ...
```

anyone have any idea?

---

### Post by saj0577 on 2008-03-27
How long you leave it for before killing?

Saj

---

### Post by milesbh on 2008-03-27
a long time

---

### Post by saj0577 on 2008-03-27
Okay just some of the processes take a long time.
When you say along time i presume you been a good period of time (30mins)

You tried running the update again?

---

### Post by milesbh on 2008-03-27
han gon, do you mean before i killed the "sudo dpkg --configure -a" command? cos i haven't killed that

---

### Post by saj0577 on 2008-03-27
Yes thats what i mean. Okay its still running established. Il try to look into it if no one else posts a reply before i find an answer.

Saj

---

### Post by milesbh on 2008-03-27
dont worry, it turns out i didn't give it enough time, i wasnt patient enough. thank you however for posting as i probably wouldnt have thought of giving it more time to work had you not posted

---

