---
title: "easyubuntu, not so easy"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by tenny56 on 2006-07-11
ok, i have had no problems using this at all.

the problem lies with my fathers computer.

for some reason, when you try to install the codecs for the restricted files, it comes up with a message that says

"could not apply changes, fix broken packages first"

please help, what is broken?? how do i fix??

tenny

---

### Post by simone.brunozzi on 2006-07-11
strange... please provide more informations (ubuntu version, etc.) and possibly an apt log.

Cheers,

---

### Post by tonyp1969 on 2006-07-11
I had this same problem, install the packages one at a time until you find the one that will not install.
Then you will be able to Fix the broken package.

---

### Post by tseliot on 2006-07-11
Try with:
```
sudo apt-get install -f
```

type the command exactly as I wrote it

---

