---
title: "frostwire installation issues"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by darknesschaos on 2007-10-02
every time i go to install frostwire from the debian gdebi package installer i get this error, "Failed to run gdebi-gtk '--non-interactive' '/home/laura/Desktop/frostwire-4.13.3.i586.deb" as user root. what does that mean

---

### Post by tgalati4 on 2007-10-02
Try in a terminal:

>sudo dpkg -i /home/laura/Desktop/frostwire-4.13.3.i586.deb

---

### Post by darknesschaos on 2007-10-02
that didn't work because it just goes back to saying laura@laura-laptop:~$

---

### Post by Billy_McBong on 2007-10-02
[COLOR="Blue"]that means it installed
but its in the repos so you could also install it by doing ```
sudo apt-get install frostwire
```[/COLOR]

---

### Post by tgalati4 on 2007-10-02
In a terminal:

>frostwire

I have 4.13.1beta from the Dapper repositories.  Not sure what differences are in 4.13.3.

---

