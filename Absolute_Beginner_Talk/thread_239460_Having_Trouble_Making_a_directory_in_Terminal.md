---
title: "Having Trouble Making a directory in Terminal"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by kittie2171 on 2006-08-19
I type 
mkdir directoryname

and I get 

mkdir: cannot create directory `/usr/java': Permission denied

Do I need to type SU first?

is the password for it different then my account password

If it is differnt is there a way to find out what the password is?

---

### Post by statue on 2006-08-19
try "sudo mkdir <path>"


always use sudo for things that will require superuser(root)access....like making new directories or deleting system files/programs etc

---

### Post by Klaidas on 2006-08-19
In that directory you have to be root.
To be root on ubuntu, see my signature :)
Ubuntu uses sudo instead of su, but that's explained there :)

---

