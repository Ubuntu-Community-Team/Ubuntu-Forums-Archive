---
title: "How to do a           &quot;dpkg -c *.deb&quot;     in my folder ?? Not possible with *"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-02-27
How to do a           "dpkg -c *.deb"     in my folder ?? Not possible with *
===================
  
I am trying to know in which deb is a specific file.
  
How can I get the listing of several debs of my folder ..? 

 Thank you 

Pat'

====================
[http://www.cyberciti.biz/nixcraft/vivek/blogger/2005/05/linux-debian-package-management-cheat.php](http://www.cyberciti.biz/nixcraft/vivek/blogger/2005/05/linux-debian-package-management-cheat.php)

---

### Post by paulmilliken on 2006-02-27
You could write a for loop in bash.  See [http://www.faqs.org/docs/Linux-HOWTO/Bash-Prog-Intro-HOWTO.html#s7](http://www.faqs.org/docs/Linux-HOWTO/Bash-Prog-Intro-HOWTO.html#s7) for an example.

---

### Post by patrick295767 on 2006-02-27
Thx for your fast reply !

I tried 
  
```
cd /foldercontainningplentyofdebfile
dpkg -S fileseeked* *
```
   
I am not so sure it's workign okay...

---

### Post by patrick295767 on 2006-02-27
or could it work :

```
ls | xargs grep mysearchedfile
```
  
for instance :
```

ls | xargs grep tamad
```

??

---

### Post by patrick295767 on 2006-02-27
```
#!/bin/bash
cd /myfolderwithdeb
for i in $( ls ); do
     dpkg -c $i >> ~/mydebcontentsresults.txt
done
```

 
Cos i am looking for a specific file in all these deb ... in my /var/cache/apt/archives ...

Thank you

---

