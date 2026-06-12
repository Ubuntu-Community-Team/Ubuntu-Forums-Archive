---
title: "Converting .rpms to .debs"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by hypersoar on 2006-06-07
I just installed ubuntu, and I'm trying to install some rpms. I'm aware of the "sudo alien" command, but when I attempt it I am told "command not found." Thus far I haven't found anything on what tod do if you encounter this error.

Thanks in advance for any help you can give me.

---

### Post by caldevil on 2006-06-07
Do:
sudo apt-get install alien

first to install alien.

---

### Post by hypersoar on 2006-06-07
It worked. Thanks again.

---

### Post by patrick295767 on 2006-06-07
It's always better to use the sources tar.gz
then you can do ./compile ; make ; make install 

Greetz

(alien will not always work)

---

### Post by manicka on 2006-06-07
or use checkinstall to compile a deb for you from source

sudo apt-get install checkinstall
./configure
make 
sudo checkinstall

---

### Post by Kimm on 2006-06-07
why do you write ./compile??

Its supose to be:

./configure (--any config here (--prefix=/usr --build=i686-linux is what i use))

---

### Post by manicka on 2006-06-07
woops.... half asleep :)

---

### Post by Kimm on 2006-06-07
Haha, no worries, happens to all of uss (I'm close to missing my stop Every morning on the bus... :-\" )

---

