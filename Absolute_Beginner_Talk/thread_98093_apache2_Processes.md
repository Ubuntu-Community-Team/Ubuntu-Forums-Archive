---
title: "apache2 Processes"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by Freddie on 2005-12-02
I currently run apache2 on my ubuntu iMac. Today I looked at system monitor only to see 10+ copies of apache2 running (all called with the same arguments) and taking up about 20.1mb each. If I view my website then it seems to create another instance of the process. I am not sure what is causing this but it does not seem to be taking up any more 'real' memory as far as I can tell. Can anyone tell me if this is normal and if not what I can do about it.

---

### Post by Kvark on 2005-12-02
Those proccesses probably all take up the same 20mb memory, not a separate 20mb for each proccess.

You can edit /etc/apache2/apache2.conf and change the values in there for how many servers to start and so on to better suit the number of apache server proccesses needed to cope with the web page requests you get.

---

