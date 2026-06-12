---
title: "MS to Ubuntu in Samba"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by telegramsam on 2006-09-22
I read on here how to assign a password to a windows machine to read files on the Ubuntu system, but I CANNOT find it no more...

Can somebody direct show me some instructions for that.  

I got Samba going the other direction, which was surprisingly easy!  But now I'm stuck :oops:

---

### Post by bigken on 2006-09-22
in a terminal type 
sudo aptitude install samba
sudo smbpasswd -e (your name)
sudo smbpasswd -a (your name)
sudo /etc/init.d/samba restart ;)

---

