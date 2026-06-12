---
title: "Move files from laptop to server via ssh"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by Bjerrum on 2008-03-20
Hi

I try to move files from my laptop to my server on the local network using ssh. 

```
name@name-laptop:~$ cp somefile.txt ssh server_name@xxx.xxx.x.x:/test
cp: target 'name@xxx.xxx.x.x:/test' is not a directory
```

This dos not work. Is it possibly using cp? Or do I need to use some ftp thing?

:confused:

---

### Post by ruy_lopez on 2008-03-20
> **Bjerrum said:**
> 
This dos not work. Is it possibly using cp? Or do I need to use some ftp thing?
:confused:

```
scp file user@server:~/

or, for directories

scp -r folder user@server:~/

```

You can supply a different path after user@server:

To copy from the server (file from user@server's home dir):
```

scp user@server:~/file .

```

---

### Post by handydan918 on 2008-03-20
> **Bjerrum said:**
> Hi

I try to move files from my laptop to my server on the local network using ssh. 

```
name@name-laptop:~$ cp somefile.txt ssh server_name@xxx.xxx.x.x:/test
cp: target 'name@xxx.xxx.x.x:/test' is not a directory
```

This dos not work. Is it possibly using cp? Or do I need to use some ftp thing?

:confused:

Try scp with ssh.

```
scp somefile.txt xxx.xxx.x.x:/test
```

At least, that's how I do it.

---

### Post by Bjerrum on 2008-03-20
Thangs both

This worked:
```

name@name-laptop:~$ scp some.txt name@192.168.1.2:~/
name@192.168.1.2's password: 
some.txt                                              100% 4606     4.5KB/s   00:00 

```

;-)

---

### Post by handydan918 on 2008-03-20
> **Bjerrum said:**
> Thangs both

This worked:
```

name@name-laptop:~$ scp some.txt name@192.168.1.2:~/
name@192.168.1.2's password: 
some.txt                                              100% 4606     4.5KB/s   00:00 

```

;-)

heh, forgot to mention you'd be prompted for the password...
Check out man scp. It is a neat tool, you can "push" or "pull" with it.

---

