---
title: "Java Errors"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by linux2007 on 2006-12-12
I'm trying to install Java applet plug-ins but I'm getting this error. Please help. 

Could not open the file /home/admin/
Desktop/jre-1_5_0_09-linux-i586.bin

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

Character Coding: Current Locale (UTF-8)

---

### Post by tszanon on 2006-12-12
Have you set the Execute permission for this file? It's necessary to do so in order to run the installer:

```
cd ~/Desktop
chmod 755 jre-1_5_0_09-linux-i586.bin
./jre-1_5_0_09-linux-i586.bin
```

Write the above code in Terminal (Applications > Accessories > Terminal).
Does it help you?

---

### Post by linux2007 on 2006-12-12
Sorry, but I'm so new at this... This is what I get when I type in the second line...
admin@admin-desktop:~/Desktop$ chmod 755 jre-1_5_09-linux-i586.bin
chmod: cannot access `jre-1_5_09-linux-i586.bin': No such file or directory

---

### Post by taurus on 2006-12-12
What's the output of this command from a terminal?

```
ls -la ~/Desktop
```

---

### Post by linux2007 on 2006-12-12
lsadmin@admin-desktop:~$ ls -la ~/Desktop
total 16700
drwxr-xr-x  2 admin admin     4096 2006-12-12 12:58 .
drwxr-xr-x 21 admin admin     4096 2006-12-12 12:53 ..
-rw-r--r--  1 admin admin     4163 2006-06-15 10:25 hammer-00dffd451d.desktop
-rw-r--r--  1 admin admin 17059194 2006-12-12 07:33 jre-1_5_0_09-linux-i586.bin

---

### Post by taurus on 2006-12-12
```
cd ~/Desktop
chmod 755 jre-1_5_0_09-linux-i586.bin
```
Looks like you need to log in as lsadmin, not admin since jre-1_5_0_09-linux-i586.bin is in /home/lsadmin/Desktop...

---

### Post by linux2007 on 2006-12-12
lsadmin? confused? this was the account I set up during the installation process. How do I find the other account?

---

### Post by HokeyFry on 2006-12-12
try this:

chmod 755 ./jre-1_5_0_09-linux-i586.bin


this is the same as you had before except the ./ tells it to look in the directory you are currently in

---

### Post by taurus on 2006-12-12
I saw it from your post above!!!

```
**_lsadmin_**@admin-desktop:~$ ls -la ~/Desktop
```

So, log in to whatever account you logged in to get the output that I asked above then...

---

### Post by linux2007 on 2006-12-12
Oh, hmmm, I redid it and this is what I have now..

admin@admin-desktop:~/Desktop$ ls -la ~/Desktop
total 16700
drwxr-xr-x  2 admin admin     4096 2006-12-12 12:58 .
drwxr-xr-x 21 admin admin     4096 2006-12-12 12:53 ..
-rw-r--r--  1 admin admin     4163 2006-06-15 10:25 hammer-00dffd451d.desktop
-rwxr-xr-x  1 admin admin 17059194 2006-12-12 07:33 jre-1_5_0_09-linux-i586.bi

---

### Post by igknighted on 2006-12-12
If you start typing before the prompt appears it will put the text you type in front of the prompt as well as after it, thats probably where that came from.

---

### Post by linux2007 on 2006-12-12
okay, not sure what i did but it appears it's loading. now I have a folder on my desktop  jre1.5.0._09 . Is there something else I needed to do? I tried a gaming website and it still asks me installed java pluggins.

---

### Post by HokeyFry on 2006-12-12
oh

umm you should link the '[java folder]/bin/java' file to a file named 'java' and move that to /bin. you have to have root access when you write to /bin though so i suggest doing that part in the terminal

EDIT: if i were you i would first move the java folder from your desktop just because it looks not cool ;)

---

### Post by linux2007 on 2006-12-12
Thanks,

Would you be able to show me the steps? I'm really really new at this.

---

### Post by taurus on 2006-12-12
```
cd ~/Desktop
sudo mv jre-1_5_0_09-linux-i586.bin /opt
cd /opt
sudo ./jre-1_5_0_09-linux-i586.bin
sudo update-alternatives --update java
(and pick the new version from the list...)
```

---

