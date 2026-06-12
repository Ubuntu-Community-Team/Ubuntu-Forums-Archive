---
title: "Password Problems"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by jeantasse on 2006-01-12
Hello People, my name is Jean-Francois and i am from Montreal, Quebec, Canada.  I have resently downloaded ubuntu 5.10 and tried to instaled.  (by the whay, my english is not perfect).  After having freeze problem during installation  i have choosen the right core, and it unfroze (wich on is recommendet).  But when i booted and tried to do my updates, it ask for my admin password, but (after many reintallation) it either always says : Password invalid or the updater just did not work.  And i tried password as stupid as 123456 and still error message occured.  Please help me because i would very much like to use ubuntu as an eventual replacement to Windows and promot it.:D

---

### Post by jimrz on 2006-01-12
Welcome,

   Just use your regular user password. By default, ubuntu does not have a /root account all admin activities are done using sudo (super user), which uses your regular user password.

---

### Post by paulmilliken on 2006-01-12
[QUOTE=jeantasse]Hello People, my name is Jean-Francois and i am from Montreal, Quebec, Canada.  I have resently downloaded ubuntu 5.10 and tried to instaled.  (by the whay, my english is not perfect).  After having freeze problem during installation  i have choosen the right core, and it unfroze (wich on is recommendet).  But when i booted and tried to do my updates, it ask for my admin password, but (after many reintallation) it either always says : Password invalid or the updater just did not work.  And i tried password as stupid as 123456 and still error message occured.  Please help me because i would very much like to use ubuntu as an eventual replacement to Windows and promot it.:D[/QUOTE]

I don't understand why it didn't work.  Perhaps some more information might help - if you open a shell and type "sudo ls" it will also ask for your password.  Does it accept it in that case?

---

### Post by Iowan on 2006-01-13
[QUOTE=jimrz]... all [COLOR="Red"]admin activities[/COLOR] are done using sudo (super user), which uses your regular user password.[/QUOTE]Whenever you "sudo", you're going to get asked for the password.  You can "ls" as a regular user without problem, but to act as root (via sudo) it'll want the password.

---

