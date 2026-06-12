---
title: "Ubuntu root issues"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by goldenllama on 2008-04-07
I am simply trying to move some .jpg files to the usr/share/backgrounds file.  in terminal i am getting an error that there is no such file or directory.  yet when i navigate to the usr/share/backgrounds directory from either terminal or GUI i can open up the file and see that it is there.  in terminal if i navigate to the usr/share/backgrounds file and i try as root to chown the file is says that there is no such file or directory.  im just trying to move some files and am getting no where.

---

### Post by DariusS on 2008-04-07
doubt it will help, but have you tried running nautilus as root? (sudo nautilus)

---

### Post by jkeyes0 on 2008-04-07
> **goldenllama said:**
> I am simply trying to move some .jpg files to the usr/share/backgrounds file.  in terminal i am getting an error that there is no such file or directory.  yet when i navigate to the usr/share/backgrounds directory from either terminal or GUI i can open up the file and see that it is there.  in terminal if i navigate to the usr/share/backgrounds file and i try as root to chown the file is says that there is no such file or directory.  im just trying to move some files and am getting no where.

are you trying to go to usr/share/backgrounds or /usr/share/backgrounds? There is a distinct difference (/usr/share/backgrounds looks to the /usr folder, whereas usr/share/backgrounds looks for a usr folder in your current directory, which is probably /home/username).

---

### Post by aysiu on 2008-04-07
> **DariusS said:**
> doubt it will help, but have you tried running nautilus as root? (sudo nautilus)
It should be ```
gksudo nautilus
``` For the OP, read [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by DariusS on 2008-04-07
^ good point, the leading slash is important.

---

### Post by DariusS on 2008-04-07
> **aysiu said:**
> It should be ```
gksudo nautilus
``` For the OP, read [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

I use sudo nautilus all the time.. always works for me. ???

---

### Post by Joeb454 on 2008-04-07
It works, but it can sometimes mess up permissions, so it's always best to use **gksu** or **gksudo** :)

---

### Post by goldenllama on 2008-04-07
the leading fwd slash was the issue...all is well...thanks for the help

---

### Post by DariusS on 2008-04-07
just another example of the importance of syntax :)

---

### Post by Joeb454 on 2008-04-07
It took me a while to get used to that at first too :)

---

### Post by aysiu on 2008-04-07
> **DariusS said:**
> I use sudo nautilus all the time.. always works for me. ???
Some graphical applications do appear to work with no side effects using *sudo* instead of *gksudo*, but it's a good idea to get new users into the habit of using *gksudo* with graphical applications, as some do have side effects.

Read more here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

