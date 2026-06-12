---
title: "mounting windows"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by will00 on 2005-12-16
does anyone know how to access the data on a hard drive while on the live cd? i could really use some help. Please!!!!

---

### Post by will00 on 2005-12-16
i really need to access the files on the hard drive of my computer. does anyone know how to access the windows files from the live cd? PLEASE HELP!!!!!!!!:confused: :confused: :confused: :confused: :confused: :confused:](*,)

---

### Post by will00 on 2005-12-16
cmon people im seeing all these people get their answers in like three seconds. what about me? i really need some help here. ill say it for the third tome. DOES ANYONE KNOW HOW TO ACCESS THE WINDOWS FILES FROM THE LIVE CD?!?!?!:confused:

---

### Post by Mustard on 2005-12-16
Try reading over this guide.....

[http://help.ubuntu.com/starterguide/C/ch05.html](http://help.ubuntu.com/starterguide/C/ch05.html)

Have you ever used a terminal before in linux?

---

### Post by hod139 on 2005-12-16
if you did any searching first you would have found this:
[http://ubuntuforums.org/showthread.php?t=103439&highlight=livecd+windows]("http://ubuntuforums.org/showthread.php?t=103439&highlight=livecd+windows")

Edit: Took less than a minute for me to do that search too :)

---

### Post by Mustard on 2005-12-16
Patience grasshopper, patience.... ;)

---

### Post by bscbrit on 2005-12-16
Will00, I am not a live CD user and I was searching for the answer to your problem.  But you only asked the question 35 mintues ago - that is not very long to have to wait for the answer, is it?  Anyway, your problem has been solved by hod139 so you should now be OK.

---

### Post by thezerogroup on 2005-12-16
is your windows drive NTFS, or FAT. . . I dont know if the liveCD comes with NTFS write support, maybe only read. Tell us a little more of what your trying to accoplish

---

### Post by Qrk on 2005-12-16
First make a folder for windows to be mounted in.

```
sudo mkdir /media/windows
```

Then mount it. If you are running windows XP on /dev/hda1, (the first partition in the drive) use:

```
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

Adjust accordingly for Fat32 etc.

---

### Post by thezerogroup on 2005-12-16
Wil00 you just asked the same question in this thread: 
[http://www.ubuntuforums.org/showthread.php?t=104605]("http://www.ubuntuforums.org/showthread.php?t=104605")

Posting the same question twice does not mean a quicker reply -v -v

---

### Post by aysiu on 2005-12-16
See the fourth link in my sig--applies for the live CD as well.

In answer to thezerogroup: neither the live CD nor the installer CD have write support for NTFS. Write support for NTFS in all of Linux is, at this point, still experimental.

---

### Post by aysiu on 2005-12-16
See the fourth link of my sig.

---

### Post by aysiu on 2005-12-16
How many threads do you need on the same topic?

---

### Post by ubuntu_demon on 2005-12-16
I merged the three threads. Please don't start multiple threads for one problem. You won't get more help that way.

Good luck on your problem. Have fun on the forums :)

---

