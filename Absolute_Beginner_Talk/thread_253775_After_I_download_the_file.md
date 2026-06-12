---
title: "After I download the file"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by barton.jones on 2006-09-08
I think I have to save it to a disk then run it, but I'm not a 100% on that ... then what do I need to do as far as downloading programs and such

---

### Post by jperez on 2006-09-08
You'll have to be a little more specific as to what you're talking about.  What file?

Also, some or most linux files that are not DEB packages are source code that needs to be compiled.  To compile, do a search on the forums.

Jesse~

---

### Post by barton.jones on 2006-09-08
[http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/)

the file to install Ubuntu on my computer

---

### Post by catlett on 2006-09-08
That's some file :-D  I assume you know that is the entire Ubuntu operating system you are trying to download and install.
This is your best place to go [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
It has instructions for downloading and installing Ubuntu.
Just go to the left and select the links under "Just beginning"

---

### Post by barton.jones on 2006-09-08
yeah, it's at 9% done ... I should be able to install it tomorrow morning

---

### Post by catlett on 2006-09-08
When you finally install there are 2 ways to get your system equipped with the basic web and multimedia packages. One is easy. It is a script that instals everything automatically. It is called Automatix and you can get it here [http://www.getautomatix.com/](http://www.getautomatix.com/)
Actually here are the instructions. Open up a terminal. It is located in the menu under Applications<Accessories<Terminal. Then just copy and paste these commands in one at a time, hitting enter after each command.
```
wget http://www.getautomatix.com/files/automatix-installer
```
```
chmod 755 ~/automatix-installer
```
```
./automatix-installer

```
To runj automatix, just enter it's name in the terminal
```
automatix
```
If you feel a bit ambituos, you can install it all yourself with the instructions from the Dapper Guide [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)
Have fun.

---

### Post by barton.jones on 2006-09-08
the file stopped downloading, so I'm trying to use the BitTorrent to do it faster, but I'm having trouble getting a place to download the BitTorrent from

---

### Post by barton.jones on 2006-09-08
I got the BitTorrent downloaded but I could use some help on how to use it

---

### Post by bodhi.zazen on 2006-09-08
> **barton.jones said:**
> yeah, it's at 9% done ... I should be able to install it tomorrow morning

Steps:

1. Download iso.

2. Check md5sum.

3. Burn (not copy) to CD.

4. Defragment you windows partition.

5. Boot you computer to CD (Ubuntu NOT Windows).

6. Partition -> shrink size of windows ntfs, make "free space" for ubuntu.

7. Install Ubuntu (click "install me").

8. Boot Ubuntu.

9. He he.... Delete windows (it may take a while for you to want to do this one).

---

