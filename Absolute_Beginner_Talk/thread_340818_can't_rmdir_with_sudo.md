---
title: "can't rmdir with sudo"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by Jive Turkey on 2007-01-17
I'm new to linux, and I've only been using Ubuntu for less than 24 hours.  I've done a good bit of searching before posting this question.  I encountered this problem while trying to follow the Howto: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")  to get dual monitor support on my ATI card.  I'm running v6.10

I accidentally put the directory '/ATI' in my user home folder (ie /home/ck/ATI ) instead of well... I'm not sure where I should really put it, but I know its not there.  so Its locked, this is what I get when I try to get rid of it (its empty) in the Terminal:

ck@ck-desktop:~$ ls
ATI  Desktop  Examples

ck@ck-desktop:~$ sudo rm /ATI
Password:
rm: cannot remove `/ATI': No such file or directory

ck@ck-desktop:~$ sudo rmdir /ATI
rmdir: /ATI: No such file or directory

---

### Post by meng on 2007-01-17
sudo rmdir ATI
no slash

---

### Post by taurus on 2007-01-17
```
cd ~
sudo rm -rf ATI
```

---

### Post by Jive Turkey on 2007-01-17
> **taurus said:**
> ```
cd ~
sudo rm -rf ATI
```

wow, that was fast!  Thanks.
I guess it doesn't help that I'm working from an ancient tutorial (1998)
[http://www.tldp.org/LDP/gs/node5.html](http://www.tldp.org/LDP/gs/node5.html)

---

### Post by Albi on 2007-01-17
Get one from 2004 or higher...or just go to ubuntuguide.org for basic stuff like that

---

