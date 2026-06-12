---
title: "Moving a file"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by goldenbough on 2008-04-06
I am attempting to move a file into /var/www/phpweb20  The file is a Zend Framework library file.  Which I cannot seem to move through the command prompt.  The unzipped folder is at /home/sean/Desktop/ZendFramework-1.5.1/library/Zend.  I am not sure how to move it into phpweb20

---

### Post by Rocket2DMn on 2008-04-06
If it says you do not have privileges, you need to start the command with "sudo" which will temporarily give you root privileges.  So like
```
sudo mv /path/to/original/file /path/to/destination
```
You may also consider changing ownership of the file with
```
sudo chown yourusername:yourusername /path/to/file/filename
```

---

### Post by goldenbough on 2008-04-06
So I have this at the command prompt:  /var/www/phpweb20$

I want to move zendframework-1.5.1/library/zend into it.  

I tried:
/var/www/phpweb20$ mv zendframework-1.5.1/library/zend 

The returned message then:
mv: missing destination file operand after `zendframework-1.5.1/library/zend'

I also tried to drag the file into phpweb20, but it says I don't have permission to write the folder.

---

### Post by Rocket2DMn on 2008-04-06
Do
```
sudo mv zendframework-1.5.1/library/zend /var/www/phpweb20
```
From the folder that zendframework-1.5.1 is in, or
```
/absolute/path/to/zendframework-1.5.1/library/zend /var/www/phpweb20
```
The path /var/www/phpweb20 is probably owned by root, so you need to use sudo to move the file.

---

### Post by apostate on 2008-04-07
> **Rocket2DMn said:**
> Do
```
sudo mv zendframework-1.5.1/library/zend /var/www/phpweb20
```
From the folder that zendframework-1.5.1 is in, or
```
/absolute/path/to/zendframework-1.5.1/library/zend /var/www/phpweb20
```
The path /var/www/phpweb20 is probably owned by root, so you need to use sudo to move the file.

Hi!

Just a quick gut-check: May I ask why you are trying to manually install a Zend framework library in this day and age? It seems like you want php running, and if I misunderstand then please forgive me, but why don't you just use Synaptic to install php5?

---

