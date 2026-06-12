---
title: "How to instal jre-6u5-linux-i586.bin from terminal from Desktop"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by gecko113 on 2008-03-17
how would i install this from my desktop the directory is /home/dj/Desktop

---

### Post by forrestcupp on 2008-03-17
> **gecko113 said:**
> how would i install this from my desktop the directory is /home/dj/Desktop

```
cd ~/Desktop
chmod +x ./jre-6u5-linux-i586.bin
./jre-6u5-linux-i586.bin

```

But if you're trying to install java, a much easier way is from the repos.
```
sudo apt-get install sun-java6-plugin
```

---

### Post by mali2297 on 2008-03-17
You've got instructions here:
[http://jmtdstoc.blogspot.com/2008/03/ubuntu-710-sun-java-16005-manual.html](http://jmtdstoc.blogspot.com/2008/03/ubuntu-710-sun-java-16005-manual.html)

---

### Post by gecko113 on 2008-03-17
Its giving me and error of permission denied if i go sudo sh jre-6u5-linux-i586.bin

---

### Post by Ub1476 on 2008-03-17
Just search for Java in add/remove and install it from there. The reason it gives a permission error is because you don't have root privileges. Add "sudo" in front of the command.

---

### Post by gecko113 on 2008-03-17
Well i tried looking in both add and remove and the other way through the terminal and i can't get both of them to work.... and i used the Sudo  command infront to

---

### Post by forrestcupp on 2008-03-17
Try this.  Go to System->Administration->Software Sources.  In the Ubuntu Software tab, make sure all boxes are checked.  Close that and try again.
```
sudo apt-get update
sudo apt-get install sun-java6-plugin
```

---

