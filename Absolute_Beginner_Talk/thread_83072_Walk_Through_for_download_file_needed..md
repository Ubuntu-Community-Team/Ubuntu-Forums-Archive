---
title: "Walk Through for download file needed."
date: 2005-10-27
forum: Absolute Beginner Talk
---

### Post by Cufishing on 2005-10-27
Ok, I have downloaded the Opera file, and a driver for my printer.

I have followed to the instructions to a precise 'copy' ' paste' T. I cannot get it to work.

I have this file on my desktop "brhl2040lpr_1.1.2-3_i386.deb", it is for my printer.

Please give me a walk through from start to finish what I need to do.

I have opened a terminal, I have done the sudo dpkg -i to the file, I have given it my password, and I get this: dpkg: error processing brhl2040lpr_1.1.2-3_i386.deb (--install):
 cannot access archive: No such file or directory

Please allow me the wisdom.

---

### Post by Kapre on 2005-10-27
Where is the d/l file located? Make sure that it is in your home directory because form the error you've listed below (if cannot find the file)..

K

---

### Post by Mustard on 2005-10-27
I would say there are probably two possible issues.

1.  You entered the wrong name for the .deb (not really likely)
2.  You are running the dpkg command in terminal, but your working directory is not the actual directory the package is in. (quite likely)

To solve issue two you need to use the 'cd' command to change your current working directory in terminal.  In your case your file is on the Desktop so...

```
cd ~/Desktop/

the long form of this command would be

cd /home/your_username/Desktop/

where you substitue your username in the appropriate spot.

```

To find out what directory is your current working directory you can use the 'pwd' command.

```
pwd
```

Additionally, if you don't already know, you can use the TAB key to autocomplete the names of files or directories, for instance if you were entering dpkg in terminal you could type 'dpkg -i brh' then hit the TAB key and it will complete the file name for you (if the file is in your working directory).

---

### Post by Cufishing on 2005-10-27
Bingo, Thank You, Mustard. So, know I have learned to Change Directory to where I place my downloads. Once I did then the <tab> worked. It did not work in the wrong directory :').

Ah, minor victory.

---

### Post by Mustard on 2005-10-27
Cufishing, I have dug up this link for you.  I hope it is of some assistance with installing Opera.

[Opera Browser]("https://wiki.ubuntu.com/OperaBrowser")

---

