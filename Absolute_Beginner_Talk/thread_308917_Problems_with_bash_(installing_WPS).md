---
title: "Problems with bash (installing WPS)"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by AiBo on 2006-11-28
I am trying to install a Chinese program called WPS (it is a Chinese remake of the M$ Office suite, that our company uses and I need to be using the same software).  They do have a Linux install on their professional version (which we are using).  But when I try to "bash" the setup this is what i get:

/media/cdrom0/WPS Office 2005 For Linux# ./setup
bash: ./setup: /bin/sh: bad interpreter: Permission denied

Is there a problem with bash?  Is it a problem with the install disk.  I am logged in under "sudo su" so I should have full permission, right?


I am still quite a novice.  I would love to get this working as I am trying to push or company away from Micro$oft and into more affordable and long term solutions.  Openoffice still is not strong enough on its Chinese version to move them this way (though I tried, and still hear about it).  WPS is a baby step in the right direction.  If I can get WPS up on Ubuntu then we will install it on a couple test systems!  Any help would be wonderful!

---

### Post by flugh on 2006-11-28
The first line of the setup script should look something like:
#!/bin/sh
So you should check to see if /bin/sh indeed exists. Now /bin/sh is about as standard as /dev/null. It's pretty much there on every system. So I'd suspect some foulness in the first line of the setup script, or possibly check the permissions on /bin/sh. Try calling the script with:
/bin/sh ./setup
Or copy setup to /tmp and try running from there (maybe it's trying to make a tmp dir in it's current working directory and can't since it's a read-only cdrom).

That'd be my first string of things to look into. You can also try 'strace -o output.log ./setup' then dig through the million lines of the output looking for ERRORs (but try the other stuff first!).

---

### Post by AiBo on 2006-11-28
Ok here are the results (THANKS for the help):

/media/cdrom0/WPS Office 2005 For Linux# /bin/sh ./setup
localhost being added to access control list
./setup: 11: installData/vm/jre/bin/java: Permission denied

Then after copying it into /tmp:

/tmp/WPS# /bin/sh ./setup
localhost being added to access control list
./setup: 11: installData/vm/jre/bin/java: Permission denied

I tried with out /bin/sh:

/tmp/WPS# ./setup
bash: ./setup: Permission denied

On to the strace?

---

### Post by AiBo on 2006-11-28
results of strace:

/tmp/WPS# strace -o output.log ./setup
strace: exec: Permission denied

Am I doing something wrong that I keep getting "Permission denied"?

---

### Post by anokun7 on 2006-11-28
It seems ./setup is a script and it is using java to run some class.

Try this:
Copy your entire cd contents to your local folder (probably /tmp) and give it -R 777 permissions.

Then run .setup

If it still doesnt work, then change the line 11 to read just java and install java on the system. Once you do this run ./setup again - Let us know how it goes..

HTH,
Anoop

---

### Post by po0f on 2006-11-28
AiBo,

```
[FONT="Courier New"]$ sudo /bin/sh ./setup[/FONT]
```

---

### Post by AiBo on 2006-11-29
po0f,

Sorry still a bit of a beginning how do I give "-R 777" permissions?

I ran the code you left and got: 

tmp/WPS# sudo /bin/sh ./setup
localhost being added to access control list
./setup: 11: installData/vm/jre/bin/java: Permission denied

Taking a look at line 11 now ...

---

### Post by AiBo on 2006-11-29
Here is the setup file in the text editor:

#! /bin/sh

# should only be run local to the install directory
cd `dirname $0`


export JAVA_HOME="installData/vm/jre"
JAVA_FONTS="installData/vm/fonts"
export JAVA_FONTS
xhost +localhost
installData/vm/jre/bin/java -jar setup.data

How do I make it just "read" instead of installing?

Also here are the contents of the "output.log" if that is helpful:

execve("./setup", ["./setup"], [/* 37 vars */]) = -1 EACCES (Permission denied)
dup(2)                                  = 3
fcntl64(3, F_GETFL)                     = 0x2 (flags O_RDWR)
fstat64(3, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fb0000
_llseek(3, 0, 0xbfba2f44, SEEK_CUR)     = -1 ESPIPE (Illegal seek)
write(3, "strace: exec: Permission denied\n", 32) = 32
close(3)                                = 0
munmap(0xb7fb0000, 4096)                = 0
exit_group(1)

---

### Post by po0f on 2006-11-29
AiBo,

Can you post the output of:
```
[FONT="Courier New"]$ ls -l installData/vm/jre/bin/java[/FONT]
```
from the directory that you extracted WPS to?

---

### Post by AiBo on 2006-11-29
/tmp/WPS# ls -l installData/vm/jre/bin/java
-rw-rw-rw- 1 ai ai 24596 2006-03-01 08:00 installData/vm/jre/bin/java


Here is just ls -l by itself:


/tmp/WPS# ls -l
total 1036
drwxr-xr-x 4 ai   ai      4096 2006-05-31 09:33 installData
-rw-r--r-- 1 root root     595 2006-11-29 11:06 output.log
-rw-r--r-- 1 ai   ai       234 2006-03-01 08:00 setup
-rw-r--r-- 1 ai   ai   1040816 2006-03-01 08:00 setup.data

---

### Post by flugh on 2006-12-02
Do a 'chmod +x /tmp/WPS/installData/vm/jre/bin/java' and try again.  The permissions need to at least be -rwx------ (user can execute).

Maybe /media (and even /tmp if it is on it's own partition) with a NOEXEC option (not sure if this would cause the problem, been a while since I've dealt with that). Maybe remount the CD with explicit option setting umask to 000 (making everything +rwx).

---

