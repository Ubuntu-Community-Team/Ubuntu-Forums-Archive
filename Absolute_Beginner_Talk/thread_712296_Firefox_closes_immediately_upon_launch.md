---
title: "Firefox closes immediately upon launch"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by jnorris235 on 2008-03-01
Recently reloaded Ubuntu and everything is fine.
Now suddenly when clicking the Firefox icon, Firefox opens and immediately closes.

Yesterday I opened Terminal and typed Firefox.
Opened fine, and then more copies would open from the desktop icon.

Today - again had to go to Terminal but this time I got this>>
jon@chi:~$ firefox
Segmentation fault (core dumped)
jon@chi:~$ 

Second time it opened OK so I went to 'Help' report a problem. The page stayed blank but Terminal had a whole problem listed - but then closed too!

Wassappenin??

---

### Post by herbster on 2008-03-01
Try

```
killall firefox-bin
```

Then try starting firefox again.

---

### Post by disturbedite on 2008-03-01
if what herbster said doesn't work (that is assuming that another instance of ff is running), then try launching ff from command line and posting the output.

---

### Post by jnorris235 on 2008-03-02
Thank you.
Of course after 3 days of this, today it opened fine!
Will hold onto the KillAll idea as it does occasionally seem to keep an instance running.

---

