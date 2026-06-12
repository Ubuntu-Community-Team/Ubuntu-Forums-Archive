---
title: "netcat help"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by Doorslammer on 2008-03-14
ok my problem is I cann't seem to get this to work 

I have a help.txt file I'd like to copy over to another computer  

target system
```
nc -l -p 1234 > help.txt 
```

on the source computer 
```
cat help.txt > nc 192.168.1.103 1234 -q 10
```

here is the output I get 
```
doorslammer@ubuntuslammer:~$ cat help.txt > nc 192.168.1.103 -q 10
cat: 192.168.1.120: No such file or directory
cat: 7000: No such file or directory
cat: &#8211;q: No such file or directory
cat: 10: No such file or directory 
```

if I leave off the -q 10 
```
doorslammer@ubuntuslammer:~$ cat help.txt > nc 192.168.1.103 1234
cat: 192.168.1.103: No such file or directory
cat: 1234: No such file or directory
```

what am i doing wrong I don't seem to get it

---

### Post by handydan918 on 2008-03-15
> **Doorslammer said:**
> ok my problem is I cann't seem to get this to work 

I have a help.txt file I'd like to copy over to another computer  

target system
```
nc -l -p 1234 > help.txt 
```

on the source computer 
```
cat help.txt > nc 192.168.1.103 1234 -q 10
```

here is the output I get 
```
doorslammer@ubuntuslammer:~$ cat help.txt > nc 192.168.1.103 -q 10
cat: 192.168.1.120: No such file or directory
cat: 7000: No such file or directory
cat: –q: No such file or directory
cat: 10: No such file or directory 
```

if I leave off the -q 10 
```
doorslammer@ubuntuslammer:~$ cat help.txt > nc 192.168.1.103 1234
cat: 192.168.1.103: No such file or directory
cat: 1234: No such file or directory
```

what am i doing wrong I don't seem to get it

I don't use netcat for this type of operation, so I can't answer the question directly. But I can tell you how to use ssh to do it...
Assuming the target machine has openssh-server installed and sshd is running, do ```
scp help.txt 192.168.1.103:/home/username/targetdirectory/filname
```
Hope this helps!

---

