---
title: "Should I autoremove?"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-03-20
Should I apt-get autoremove the packages? What type of packages would be removed?

---

### Post by NightwishFan on 2008-03-20
autoclean
           Like clean, autoclean clears out the local repository of retrieved
           package files. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being
           erased if it is set to off.

I have always autocleaned. No problems yet.

autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no
           more needed.

Very useful. Gets rid of all those dependencies that you no longer need.

---

### Post by philinux on 2008-03-20
Try 

man apt-get. :)

---

### Post by Dr Small on 2008-03-20
If you run:
```
sudo apt-get autoremove
```

It will tell you a list of applications (usually dependancies) that will be removed because they are no longer necessary.

Dr Small

---

### Post by daning on 2008-03-20
very helpful

---

### Post by sayakb on 2008-03-20
Thank you all for your feedback. I would therefore be proceeding w/ autoremove and autoclean.

---

