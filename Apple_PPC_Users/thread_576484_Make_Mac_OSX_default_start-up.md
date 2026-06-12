---
title: "Make Mac OSX default start-up"
date: 2007-10-15
forum: Apple PPC Users
---

### Post by Kotos11 on 2007-10-15
WHERE do I look and what do I do, change or add to make Mac OSX the default start-up system after   
Feisty has been installed? I am very impressed by Ubuntu and want to learn more about it but have way too much on the Mac side of things and would like to switch back and forth the two systems.

Also, my kids are only familiar with Mac and for the present I would like it to be that way until I know Ubuntu a little more.

---

### Post by chimaera on 2007-10-15
add 
```
defaultos=macosx
```

to the file */etc/yaboot.conf*. 

then run ```
sudo ybin -v
``` on a console/terminal.

takes two seconds to google the same solution, though..

---

