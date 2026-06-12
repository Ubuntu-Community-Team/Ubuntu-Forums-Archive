---
title: "Learning how to compile programs"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by Falc7 on 2008-03-28
I am following this guide to install songbird
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

I nativated to the location of the extracted file, and did this:
mj@mj-desktop:~$ cd /home/mj/Desktop/Songbird
mj@mj-desktop:~/Desktop/Songbird$ ./configure
bash: ./configure: No such file or directory

What am i doing wrong?

---

### Post by Inxsible on 2008-03-28
did you extract the tar file first ? you can extract it by```
tar xzvf filename
```after you extract it you need to go into the extracted folder and then run```
./configure
```

---

### Post by Falc7 on 2008-03-28
yep i extracted by right click, extract.
the file came up on desktop, so i did 'cd' in the terminal, then copied the location of the file on desktop, hit enter, then did the configure thing as shown below
mj@mj-desktop:~/Desktop/Songbird$ ./configure
bash: ./configure: No such file or directory

---

### Post by Average Joe on 2008-03-28
I think you need to install the development packages first:
```
sudo aptitude install build-essential
```
This installs the tools to compile your own stuff.

---

### Post by Inxsible on 2008-03-28
Check this [link]("http://ubuntuforums.org/showthread.php?t=659452&highlight=install+songbird") out. It seems that you don't need to install songbird, you can simply run it from the extracted folder.

On the other hand, you might also want to simply get a deb file for it as suggested in the last post on that link.

---

### Post by forrestcupp on 2008-03-28
> **Inxsible said:**
> Check this [link]("http://ubuntuforums.org/showthread.php?t=659452&highlight=install+songbird") out. It seems that you don't need to install songbird, you can simply run it from the extracted folder.

On the other hand, you might also want to simply get a deb file for it as suggested in the last post on that link.

Right.  Not every tar.gz is source code that needs compiling.  Some software comes with binaries that are zipped in a tar.gz.  The best thing you can do to figure out what to do with a tar.gz is just go to that directory and see what's in it.  If you look in the directory in nautilus, you can tell if it has binaries by the blue diamond icon.  Also, if there is a readme document, look at them.  They usually tell you what to do.

---

### Post by Falc7 on 2008-03-28
ah yes you were right, thanks very much

---

