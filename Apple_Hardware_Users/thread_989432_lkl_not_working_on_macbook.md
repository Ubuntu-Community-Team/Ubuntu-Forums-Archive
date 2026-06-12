---
title: "lkl not working on macbook"
date: 2008-11-21
forum: Apple Hardware Users
---

### Post by kbgabt on 2008-11-21
Hello people.. I was wondering if anyone could give me a hand with this. I installed lkl and then i tried to make it work using:

sudo lkl -l -k /usr/share/lkl/keymaps/us_km -o log.txt

and it looks as if it were working, but then i went to check log.txt and it wasn't even created :S.. If anyone can help me with this i'll be really thankful.

---

### Post by SeaJayEmm on 2009-04-28
you have to put the log.file in a directory, for example:
sudo lkl -l -k /usr/share/lkl/keymaps/us_km -o /home/log.txt

---

