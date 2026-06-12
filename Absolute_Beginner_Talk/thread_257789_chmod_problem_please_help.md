---
title: "chmod problem please help"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by zentus on 2006-09-15
Hi

I just wrote 
sudo chmod a=rwx /mnt/desktop
in error into a terminal by accident and now nearly every file on my desktop has either disappeared or is inaccessible.

Any ideas?

---

### Post by oedipuss on 2006-09-15
Do a 'ls -l' in the parent directory of the desktop , and see what permissions it has, and who the owner is.

drwxr-xr-x  2  myname  myname      4096 2006-09-14 18:34 Desktop
^^^               ^^      ^^  
permissions      group   owner

if it's different than that, say if the owner is root , try 
sudo chown yourname:yourname ./Desktop
to set it back to you, and then if the permissions are different try 
sudo chmod a+x ./Desktop
(x is to be able to access it, since its a directory)

Hope it helps .. 
Also, why is your desktop at /mnt/ ?

---

### Post by Najand on 2006-09-15
Is it a mounted partition? Or is it a windows or any other partitions?

---

### Post by zentus on 2006-09-15
Many thanks for your kind response - no joy though

I was trying to set write permissions to a usb hard drive and typed this into a terminal:

z@zed:~$  sudo chmod a=rwx /mnt/[mountpoint]
Password:
chmod: cannot access `/mnt/[mountpoint]': No such file or directory
z@zed:~$  sudo chmod a=rwx /mnt/desktop
chmod: cannot access `/mnt/desktop': No such file or directory
z@zed:~$  sudo chmod a=rwx /unmnt/desktop
Password:
chmod: cannot access `/unmnt/desktop': No such file or directory
z@zed:~$ sudo chmod /mnt/desktop


I access all my music files, photos, documents etc through a folder on my desktop.  it appears that i have unmounted my desktop and so cannot access any of my files.  When I try to create a new folder on my desktop i get: Error "I/O error" creating new folder.  So im assuming that all i need to do is mount it again to solve the problem.

Thank you for any advice you can give.

---

### Post by Najand on 2006-09-15
Hmm, try to unmount your desktop and mount it again:
```

sudo umount /mnt/desktop
sudo mount /mnt/desktop

```

---

### Post by zentus on 2006-09-15
Thank you

z@zed:~$ sudo umount /mnt/desktop
umount: /mnt/desktop: not found
z@zed:~$ sudo mount /mnt/desktop
mount: can't find /mnt/desktop in /etc/fstab or /etc/mtab
z@zed:~$


Not nice!

---

### Post by Najand on 2006-09-15
Is the folder name "desktop"? If not change it with the folder name.

---

### Post by zentus on 2006-09-15
Thank you

No I get the same error

Desktop appears in file browser with a locked icon.  'All' was the folder where i kept all my files in Desktop, and that too appears in file browser, when i open it i get: "All" couldn't be found. Perhaps it has recently been deleted.  It hasn't been deleted so im clueless.

Thank you for your efforts

---

### Post by Najand on 2006-09-15
perhaps you  should restart your computer and let it to automount it again.

---

### Post by Jussi Kukkonen on 2006-09-15
Are you sure you have a correct mount point (/mnt/desktop):
* the directory doesn't seem to exist, 
* it doesn't seem to be found in /etc/fstab, and 
* it's not a "Ubuntu automount mount point" (those appear in /media/)

I think you should doublecheck.

---

### Post by zentus on 2006-09-15
lol

OH MI GOD IVE LOST IT ALL............

no just restart it you fool

thats where panicking gets you.

my sincere thanks for your efforts its much appreciated and its fantastic to have such a forum to turn to when you are having problems.

zentus

---

### Post by Najand on 2006-09-15
well, "sudo chmod a=rwx /mnt/desktop" does not remove files and directories, I believe.

---

### Post by zentus on 2006-09-15
quite right but im not loling anymore:

whenever i connect my external hard drive I lose my desktop folders and have to reboot to get them back.

Ideas anyone?

---

### Post by Najand on 2006-09-15
Are you mounting your USB Hard Disk to your desktop?

---

