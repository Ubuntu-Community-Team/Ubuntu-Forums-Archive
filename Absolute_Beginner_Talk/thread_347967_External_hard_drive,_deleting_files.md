---
title: "External hard drive, deleting files"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Riceboy004 on 2007-01-28
I used ntfs-config to mount my external hard drive, and everything works with reading and writing.  However, when did "move to trash" with about 8 gb of data, the data disappeared, my trash can was still empty, and the amount of free space is the same.  Does the data just get moved somewhere else?

---

### Post by petteriIII on 2007-01-28
Maybe. There are two trashcans. First in your homedirectory and second in directory: /root. They both go by the name: .Trash  . You can access then with nautilus when you press knobs: CTRL and h  .

---

### Post by Riceboy004 on 2007-01-28
> **petteriIII said:**
> Maybe. There are two trashcans. First in your homedirectory and second in directory: /root. They both go by the name: .Trash  . You can access then with nautilus when you press knobs: CTRL and h  .

I can't seem to find these .Trash folders.  I did ctrl + h and they weren't there..

---

### Post by taurus on 2007-01-28
Applications -> Accessories -> Terminal
```
cd  ~/.Trash
rm *
sudo rm /root/.Trash/*
```

---

### Post by Riceboy004 on 2007-01-28
> **taurus said:**
> Applications -> Accessories -> Terminal
```
cd  ~/.Trash
rm *
sudo rm /root/.Trash/*
```


Ok i tried but it didn't work..

[email]chris@chris-laptop:~/.Tras[/email]h$ rm *
rm: cannot remove `*': No such file or directory
chris@chris-laptop:~$ sudo rm /root/.Trash
rm: cannot remove `/root/.Trash': No such file or directory

---

### Post by taurus on 2007-01-28
```
ls -la ~/.Trash
sudo ls -la /root/.Trash
```

---

### Post by Riceboy004 on 2007-01-28
chris@chris-laptop:~$ ls -la ~/.Trash
total 8
drwx------  2 chris chris 4096 2007-01-28 00:19 .
drwxr-xr-x 27 chris chris 4096 2007-01-28 03:31 ..
chris@chris-laptop:~$ sudo ls -la /root/.Trash
ls: /root/.Trash: No such file or directory

---

### Post by givré on 2007-01-29
Go in the root **of** your usbdisk, something like /media/usbdisk
and press <ctrl>H to see hidden files.
You'll see a folder with name .Trash-<username> that you can delete with <shift><del>
or via the terminal with
```
cd /medi/<the name of your usb disk>
ls -l #show you the hidden trash
rm <the hidden trash>
```

---

### Post by Riceboy004 on 2007-01-29
got it! thanks.  i found the trash in the actual external hard drive and deleted it...free space!

---

### Post by black_magician on 2007-02-12
thanks Givre,  I was having the same problem.

---

### Post by Spike-X on 2007-02-14
> **Riceboy004 said:**
> I used ntfs-config to mount my external hard drive, and everything works with reading and writing.  

Can you talk me through how you do this, please? I cannot for the life of me get my external HD to mount as anything except read-only.

---

### Post by Spike-X on 2007-02-14
Gah! I found the ntfs-config page and tried to download and install it, but it seems to only work on Ubuntu i386. Of course, I'm running AMD64. Help?

(I'm also going to keep searching for a solution on my own, but any help would be greatly appreciated)

---

### Post by Spike-X on 2007-02-14
Another update:

I learned how to compile from source, and got ntfs-config up and running, with some help from the program's author, givré  (thank you, sir!).

BUT!

To work on my external HD, I need to use a modified version of pmount. Which is only available for the i386 architecture. And the source code doesn't seem to be available on the web page.

I'm *this* close!!

---

### Post by givré on 2007-02-14
> **Spike-X said:**
> Another update:

I learned how to compile from source, and got ntfs-config up and running, with some help from the program's author, givré  (thank you, sir!).

BUT!

To work on my external HD, I need to use a modified version of pmount. Which is only available for the i386 architecture. And the source code doesn't seem to be available on the web page.

I'm *this* close!!
I suggest you reading this : [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009) especially the AMD64 section.
I'm sorry if i can't give better support for amd64, that's the best i can do.

---

### Post by Spike-X on 2007-02-14
No worries, I appreciate what you've done so far.

*choke* that thread is 135 pages long...

Ah, well. Something do do over the weekend. Thanks again!

---

### Post by Spike-X on 2007-02-15
I tried installing givré's modified pmount using ```
sudo dpkg -i --force-architecture *packagename*_i386.deb
```

It seemed to install ok, but it seemed to break some packages in the process, which I had to reinstall.

I ain't giving up on this, though!

---

### Post by Spike-X on 2007-02-15
Okay, I've done what I should have done in the first place, and followed givré's instructions for building an AMD64-compatible version of his modified pmount. It seems to have worked!

I've been able to add write to the Folder Permissions on the drive using the GUI tool, and I've clicked on Apply Permissions To Enclosed Files (I hope that was both correct and necessary). I'm waiting for that to finish, then I'll eject the drive, re-mount it, and see if it works.

---

### Post by Spike-X on 2007-02-15
It works! It works It works It works It works It works!!!

---

