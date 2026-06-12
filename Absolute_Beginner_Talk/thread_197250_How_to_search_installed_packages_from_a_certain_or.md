---
title: "How to search installed packages from a certain origin"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by juah on 2006-06-15
How can I easily search installed (only those) packages from a certain source. I wan't to list all packages installed from 'ubuntu.moshen.de' and 'raof.dyndns.org'

apt-cache dump | grep -B 2 ubuntu.moshen.de 

would do it but it shows all the possible packages; not only the installed ones...

---

### Post by juah on 2006-06-16
since there were none to help me I had to try something: this was so far the best I could think of:

$ apt-cache dump | grep -B 2 ubuntu.moshen.de | grep Package:

T'gives me a nice list of packages available from this source, but doesn't tell me whether they're installed or not

---

