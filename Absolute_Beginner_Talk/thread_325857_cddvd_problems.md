---
title: "cd/dvd problems"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by prisley on 2006-12-26
I have destroyed too much and wasted too much time. 
My problem is that I am unable to burn a tgz. file. The tar file is my backup scheme and without it I am unable to develop a backup; stratgy.
the problem seems to be caused by my cd and dvd burners to allow transmission of data from the hard drive. I believe this is because the cd/dvd diskburners are not given root permissions. I am unabel to figure out how to give them root permissions.

perhaps the problem is in the nautlis software. Perhaps it is not accepting tgz. or perhaps it is not allowing data to cross over from hard drive to cdrom drive because of permissions.

Please if you have any idea of this problem let me know.

Meanwhile I must look for other distros that will allow me to use root in the cdrom drive and allow me to move data from cdrom to hard drives. I believe it is the sudo system that is the problem but can not find the commands and drive and file handles that will allow me to change those permissions.

Thanks  Peter

---

### Post by raldz on 2006-12-26
what burner app are you using? have you tried running it with root permission? To run it as root, just open a console and if you are using gnomebaker just trype this:

$ sudo gnomebaker

---

### Post by xpod on 2006-12-26
I`ve never had any permissions issues before but i`ve found that certain brands of cd/dvd wont work with certain burning apps...

In fact the only real burning issues i`ve had have been due to this reason.
Mabey you could try different burning apps and different brands of cd/dvd if needs be?

---

### Post by tagra123 on 2006-12-26
You could try installing k3b  

sudo apt-get install k3b.   It works when gnomebaker nautilus doesn't.

---

