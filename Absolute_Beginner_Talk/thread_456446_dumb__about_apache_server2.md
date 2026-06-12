---
title: "dumb ? about apache server2"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by sam1981 on 2007-05-27
Hi am a windows user and never worked with linux before a friend told me about ubuntu and i installed it on one of my desktop and now i am in the situation i have a windows server 2003 and and using a IIS to host my small website and now that i read so much good things about ubuntu linix i want to move my web to ubuntu desktop i already install apache but i dont know any thing about apache i am use to the IIS which is gui and easy so if some one can help me with that my ubuntu desktop i have already assign a static ip and all my web site files are rite in my memory stick and i just dont know how apache2 work and also if someone has time and willing to help me i can chat also cuz i want to find out everything about ubuntu linux i feel bad that so many years i been using windows. so please help me step by step setting up apache on my ubuntu desktop. help me plz zzzzzzzzzzzzzzzzzzzz.

---

### Post by dfreer on 2007-05-27
welcome to ubuntu!

the first thing you'll need to understand is that ubuntu & linux != windows. 
Not at all. doesn't mean one is better than the other, simply means it is a new OS and you will have to learn how to do things a different way.

Now, about the website: apache's default web root is /var/www/ so if all you have is .html files or the like you can simply dump your website in /var/www/. If you have been using Frontpage Extensions at all, they will probably not work.

If you want you can send me your pm me with your MSN IM account and I'll add you :)

---

### Post by sam1981 on 2007-05-27
How Do I Save Files In That Directory.

---

### Post by dfreer on 2007-05-27
on a desktop:
Go to Applications > Accessories > Terminal
type into terminal:
```
sudo nautilus
```
It'll open the file browser with root permissions (be careful here!). go to /var/www/
drag and drop, or copy and paste all of your webpage files into /var/www/

EDIT: This is assuming the files are either on your USB drive or on the desktop. If they are still on the windows machine you'll need to either copy them over the network or burn them to a CD or something.

---

