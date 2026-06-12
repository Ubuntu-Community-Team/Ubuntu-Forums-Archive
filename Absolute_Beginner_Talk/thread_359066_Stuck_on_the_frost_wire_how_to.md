---
title: "Stuck on the frost wire how to"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by timmins on 2007-02-11
as seen here: [http://www.ubuntuforums.org/showthread.php?t=305337&highlight=frostwire](http://www.ubuntuforums.org/showthread.php?t=305337&highlight=frostwire)

I'm on step 3, I've downloaded the second java file on the page to my desktop, I have a directory called /usr/java. when I type in the first command in step 3, I get this:

kyle@kyle-desktop:~$ sudo mkdir /usr/java
mkdir: cannot create directory `/usr/java': File exists
kyle@kyle-desktop:~$ sudo cp jre-1_5_0_10-linux-i586.bin /usr/java
cp: cannot stat `jre-1_5_0_10-linux-i586.bin': No such file or directory
kyle@kyle-desktop:~$ sudo cp jre-1_5_0_10-linux-i586.bin /usr/java
cp: cannot stat `jre-1_5_0_10-linux-i586.bin': No such file or directory
kyle@kyle-desktop:~$ 

I am unable to drag the file in the /usr/jave flder because I don't have permission to do so.


Thanks

---

### Post by taurus on 2007-02-11
If you want to drag 'n drop, run this command from a terminal and you will have root's privilege.

```
gksudo nautilus
```

---

### Post by timmins on 2007-02-11
Hi, I'm assuming that mkdir means make directory, I already have a /usr/java directory, the next command is sudo cp jre-1_5_0_10-linux-i586.bin /usr/java when I type it in I get this

kyle@kyle-desktop:~$ sudo cp jre-1_5_0_10-linux-i586.bin /usr/java
cp: cannot stat `jre-1_5_0_10-linux-i586.bin': No such file or directory

what does this mean, do I have to extract the downloaded file first?

---

### Post by timmins on 2007-02-11
NM, its a .11 file hold on let me try something.

---

### Post by taurus on 2007-02-11
Be sure you are in the directory where jre-1_5_0_10-linux-i586.bin is located.

```
cd ~/Desktop
sudo cp jre-1_5_0_10-linux-i586.bin /usr/java
```

---

### Post by timmins on 2007-02-11
It didn't work, does the java file have to be in a specific place for it to work, on the desktop/

Thanks

---

### Post by timmins on 2007-02-11
kyle@kyle-desktop:~$ /usr/java/jre-1_5_0_11-linux-i586.bin
bash: /usr/java/jre-1_5_0_11-linux-i586.bin: Permission denied
kyle@kyle-desktop:~$ cd ~/Desktop
kyle@kyle-desktop:~/Desktop$ sudo cp jre-1_5_0_11-linux-i586.bin /usr/java
kyle@kyle-desktop:~/Desktop$  sudo cp jre-1_5_0_11-linux-i586.bin /usr/java
kyle@kyle-desktop:~/Desktop$ 


My last few attempts

---

### Post by timmins on 2007-02-11
I really have absolutely no idea what is going wrong, I have the java file on my desktop and in the /usr/java folder, what could be going wrong?

pls help

Thanks

---

### Post by taurus on 2007-02-11
```
cd /usr/java
sudo chmod 755 jre-1_5_0_11-linux-i586.bin
sudo ./jre-1_5_0_11-linux-i586.bin
```

---

### Post by timmins on 2007-02-11
Thanks very much, you're the best.:)

---

### Post by Olli on 2007-02-11
> **timmins said:**
> I really have absolutely no idea what is going wrong, I have the java file on my desktop and in the /usr/java folder, what could be going wrong?

pls help

Thanks

I think you have no rights to run jre-etc. What says ls -la jre* ? If the answer is not r-x r-x r-x, yoy may command sudo chmod a+x jre-*

---

