---
title: "Line for fstab - correct syntax?"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-20
Hi,

I am wondering how I can add this line into fstab.

```
sudo mount 10.1.2.3:/media/storage /media/storage/xyz
```

Thanks.

---

### Post by %hMa@?b&lt;C on 2006-06-20
sudo gedit /etc/fstab

add that line at the end

---

### Post by u.b.u.n.t.u on 2006-06-20
My mistake, sorry.

That is the terminal command line that I want to automate by fstab. I am unsure of the correct syntax.

How do I rewrite the following, so I can add it into fstab?
```
sudo mount 10.1.2.3:/media/storage /media/storage/xyz
```

Thanks.

---

### Post by dvarsam on 2006-06-20
Read the following thread:

[http://ubuntuforums.org/showthread.php?t=186063](http://ubuntuforums.org/showthread.php?t=186063)

Read it up to the end!

Have fun!

---

### Post by u.b.u.n.t.u on 2006-06-20
I added this line and rebooted.

```
10.1.2.3:/media/storage /mnt/media/storage/xyz nfs rw 0 0
```

It doesn't work.

Source = 10.1.2.3:/media/storage

Target = /mnt/media/storage/xyz

---

### Post by anaconda on 2006-06-20
I cant remember the exact syntax, but is it something like this:

//10.1.2.3/media/storage /mnt/media/storage/xyz nfs rw 0 0
or:
//10.1.2.3:/media/storage /mnt/media/storage/xyz nfs rw 0 0


Hmm just did this in my work computer couple of weeks ago..

---

### Post by rccharles on 2006-06-20
[QUOTE=u.b.u.n.t.u]I added this line and rebooted.

```
10.1.2.3:/media/storage /mnt/media/storage/xyz nfs rw 0 0
```

It doesn't work.

Source = 10.1.2.3:/media/storage

Target = /mnt/media/storage/xyz[/QUOTE]

I do not see a syntax error.

To check things out:

1) sudo mount
    To see what is mounted.
2) sudo showmount -e 10.1.2.3
    To see what directories have been exported.
3) cd /mnt/media/storage/xyz
     To verify that the directory exits. 
     I simplify things by creating a /test directory.
4) Perhaps the export is read only.
    try ro
5) ping 10.1.2.3

The command:
sudo mount -a 
will mount unmounted filesystems in fstab and should give you an error message.

contain information on fstab and nfs...
[http://www.humbug.org.au/talks/fstab/fstab_nfs.txt](http://www.humbug.org.au/talks/fstab/fstab_nfs.txt)
  seems to be missing some options...

[http://www.humbug.org.au/talks/fstab/fstab.html](http://www.humbug.org.au/talks/fstab/fstab.html)

Robert
:-)

---

### Post by u.b.u.n.t.u on 2006-06-20
```
1) sudo mount
To see what is mounted.
```

The HDD is mounted only when I use the terminal.

```
2) sudo showmount -e 10.1.2.3
To see what directories have been exported.
```

"sudo: showmount: command not found"

```
3) cd /mnt/media/storage/xyz
To verify that the directory exits.
I simplify things by creating a /test directory.
```

It does exist. I can mount it using the terminal every time.

```
4) Perhaps the export is read only.
try ro
5) ping 10.1.2.3
```

No problem with the ping.

After I use the terminal I can read and write no problem.

```
The command:
sudo mount -a
will mount unmounted filesystems in fstab and should give you an error message.
```

```
abc@abc-desktop:~$ sudo mount -a
mount: mount point /mnt/media/storage/xyz does not exist
```

Here is my setup.

Box 1
ubuntu
#1 HDD ubuntu
#2 HDD storage

Box 2
ubuntu
#3 HDD ubuntu
#4 HDD storage


Source = 10.1.2.3:/media/storage = #2 HDD storage

Target = /mnt/media/storage/xyz = #4 HDD storage

```
10.1.2.3:/media/storage /mnt/media/storage/xyz nfs rw 0 0
```
that doesn't work

```
sudo mount 10.1.2.3:/media/storage /media/storage/xyz
```
that works

Thanks.

---

### Post by rccharles on 2006-06-22
[QUOTE=u.b.u.n.t.u]


```
abc@abc-desktop:~$ sudo mount -a
mount: mount point /mnt/media/storage/xyz does not exist
```

In Linux, you must define the target directory before you attempt to mount a file system.  This error message says that the system could not find the directory "/mnt/media/storage/xyz". 


```
10.1.2.3:/media/storage /mnt/media/storage/xyz nfs rw 0 0
```
that doesn't work

```
sudo mount 10.1.2.3:/media/storage /media/storage/xyz
```
that works

Thanks.[/QUOTE]
The parameters supplied in the mount command do not match what is in the fstab file. Notice, that /mnt isn't on the mount command.  While somepeople suggest you should mount remote filesystem in the /mnt directory, this is only a convention and you do not have too. There is no magic happening.  You have to define all the directories.

Try this:
```
10.1.2.3:/media/storage /media/storage/xyz nfs rw 0 0
```

Robert

---

