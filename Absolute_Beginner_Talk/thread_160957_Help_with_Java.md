---
title: "Help with Java"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by Virtuous on 2006-04-16
I'm new to Kubuntu, some sites when I go online need Java in order to run. The problem is that I don't know how to install Java. I have downloaded the .tar.gz file but I don't know where to go from there.:(

---

### Post by unbuntu on 2006-04-16
[QUOTE=Virtuous]I'm new to Kubuntu, some sites when I go online need Java in order to run. The problem is that I don't know how to install Java. I have downloaded the .tar.gz file but I don't know where to go from there.:([/QUOTE]

```
tar -xzvf the_downloaded_file.tar.gz
```,
it's usually a .bin file.  then ```
chmod 0755 the_bin_file.bin
```
then ```
sudo ./the_bin_file.bin
```

---

### Post by Virtuous on 2006-04-16
Thank you for the help, but I have tried the commands you gave me. I went into Konsole and this is what happened:

sydney@kubuntu:~$ chmod 0755 jre-1_5_0_06-linux-i586.bin
chmod: cannot access `jre-1_5_0_06-linux-i586.bin': No such file or directory

I don't really know what to do next. The file is on my desktop. I don't know if I have to move it somewhere else.

---

### Post by unbuntu on 2006-04-16
[QUOTE=Virtuous]Thank you for the help, but I have tried the commands you gave me. I went into Konsole and this is what happened:

sydney@kubuntu:~$ chmod 0755 jre-1_5_0_06-linux-i586.bin
chmod: cannot access `jre-1_5_0_06-linux-i586.bin': No such file or directory

I don't really know what to do next. The file is on my desktop. I don't know if I have to move it somewhere else.[/QUOTE]

If it's on your desktop, then you should 'cd' to your desktop directory first.  'cuz when you run console, you're at your home directory. (which is /home/youraccount),

you need to ```

cd Desktop

```

then do the rest

---

### Post by Virtuous on 2006-04-16
Ok, I did the commands. It seemed to install but left a folder "jre1.5.0_06" on my desktop. I don't know if it installed or just unpacked into a folder.

---

### Post by unbuntu on 2006-04-16
[QUOTE=Virtuous]Ok, I did the commands. It seemed to install but left a folder "jre1.5.0_06" on my desktop. I don't know if it installed or just unpacked into a folder.[/QUOTE]
Darn...I should've told you that you may want to install it under /usr/local, but nevertheless, here's the remedy:

First of all, It's installed.  If you don't want it to be on your desktop (and I guess you don't), move it to your /usr/local directory. (you will need root privilege).  After that, do a
```

ls -l /usr/bin/java

```
you can see the symbolic link under /usr/bin is linked to the original place on your desktop, which is broken.  So redo the symbolic link.
```

ln -s /usr/local/java_ver_whatever/bin/java /usr/bin/java

```
There are a couple of other symbolic links under /usr/bin are also broken once you moved the installation directory.  Do a 
```

ls -l /usr/bin/java*

```
and fix these links as well.


HTH

---

