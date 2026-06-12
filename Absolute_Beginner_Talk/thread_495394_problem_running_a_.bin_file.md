---
title: "problem running a .bin file"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by blastthisinferno on 2007-07-08
I'm trying to execute a .bin file, and if you must know the file is hldsupdatetool.bin. I've tried this several ways first by```
chmod +x hldsupdatetool.bin
./hldsupdatetool.bin
``` which gave me ```
-bash: ~/scds/hldsupdatetool.bin: No such file or directory
```Then I tried ```
hldsupdatetool.bin
```because I saw on another forum to try that, but got ```
-bash: hldsupdatetool.bin: command not found
```.  Then I tried```
sh hldsupdatetool.bin
```which returned an error```
hldsupdatetool.bin: 1: Syntax error: "(" unexpected
```Am I doing something wrong?

---

### Post by Stephen Howard on 2007-07-08
Go into the directory containing the program, then:

Type this command to make the program executable:
```
chmod +x hldsupdatetool.bin
```

Then type this to execute it:
```
./hldsupdatetool.bin
```

---

### Post by blastthisinferno on 2007-07-08
that is exactly what I did, and i got the following```
-bash: ./hldsupdatetool.bin: No such file or directory
```

---

### Post by forrestcupp on 2007-07-08
Are you absolutely sure you're in the right directory?  Go to the directory you think it is and type```
ls
```for the directory listing to make sure that file is where you think it is.

Are you sure it actually has the .bin suffix, or is it just hldsupdatetool?  Also, Linux is case sensitive.  If there are any capital letters, that could be the problem too.

---

### Post by blastthisinferno on 2007-07-08
I'm guessing the .bin file is corrupted or something then, I'll try redownloading it.  This is what comes up
[IMG]http://img.photobucket.com/albums/v288/blastthisinferno/binfilelocation.jpg[/IMG]

---

### Post by blastthisinferno on 2007-07-08
The redownloaded file did not work, so the change that the original file is corrupted is unlikely

---

### Post by Stephen Howard on 2007-07-09
maybe the error isn't quite right - try installing it as root.

---

### Post by blastthisinferno on 2007-07-09
Ok, if you guys didn't know I'm trying to install a Counter-Strike server, and I'm following this tutorial [http://www.cstrike-planet.com/tutorial/1-Linux-Install-CS-Source/5](http://www.cstrike-planet.com/tutorial/1-Linux-Install-CS-Source/5) .  There was a step to get past the execution of the hldsupdatetool.bin file and to just download the next file which was steam.  The problem now is that I can't execute the steam file.  Do you think I just don't have the correct program to run these files.  I'm not sure what type of file steam is cause when I ls it just says steam.  I do have uncompress and gunzip and I thought those were needed.

[IMG]http://img.photobucket.com/albums/v288/blastthisinferno/steamproblem.jpg[/IMG]

---

### Post by Stephen Howard on 2007-07-10
There does appear to be something really screwy going on.  I downloaded the same file and it installed without a problem.

I have two theories left - first, that there's something wrong with ld.so, so linux loader that actually runs executables;  second, that there's something missing in your path.

I note that your booting into a terminal (presumably your running a server) - can you boot into a full desktop environment and run it from a terminal emulator screen.  If that succeeds, then there's likely a path problem.  

Also, do:
```

ldd ./hldsupdatetool.bin
```

The above command will display the libraries the program needs to run.  For each library, type the following and see if each library is available:
```

whereis {librarynamegoeshere}
```

---

### Post by blastthisinferno on 2007-07-10
when I do the```
ldd ./hldsupdatetool.bin
```I get a message saying```
not a dynamic executable
```

Does this mean I have to get a new ld.so file?

---

### Post by DBStevens on 2007-07-10
How about providing the output of ls -o  and of cat .profile

That way we get to see all of the permission flags and how the base path is setup.

---

### Post by DBStevens on 2007-07-10
"Does this mean I have to get a new ld.so file?"

No that means the .bin file isn't a shared executable object and it really isn't so I'd expect that error message.

---

### Post by blastthisinferno on 2007-07-10
at work I'll post what it shows later

---

### Post by blastthisinferno on 2007-07-10
[IMG]http://img.photobucket.com/albums/v288/blastthisinferno/binproblem.jpg[/IMG]

Looks like I can execute.

---

### Post by blastthisinferno on 2007-07-10
When I tab out ```
ls /lib/ld-
```it shows that I have ```
ld-2.5.so           ld-linux-x86-64.so.2
```So I guess I don't have ld.so but a higher version of it?  I don't know if that info helps.

---

### Post by DBStevens on 2007-07-10
Lets see if this works:

cd /home/erich/counterstrike/srcds
../hldsupdatetool.bin

Just so you know I downloaded that server software and had no trouble following that article.  It decompressed  just fine:

~/srcds$ ls -o
total 11092
-rwxr-xr-x 1 dstevens 3513408 2007-07-10 09:30 hldsupdatetool.bin
-rw-r--r-- 1 dstevens    3413 2005-04-07 17:07 readme.txt
-rwxr-xr-x 1 dstevens 7822833 2005-04-07 17:04 steam


are sitting on my hard drive at this moment.

---

### Post by blastthisinferno on 2007-07-10
This is really pissing me off.  I've downloaded this file several times thinking that it was corrupted, and I've downloaded from other mirrors, including from steam itself.  For some damn reason it doesn't work on my system.  I have the Feisty Fawn 7.04 server edition too.

---

### Post by Stephen Howard on 2007-07-11
Um, the /home tree isn't mounted with noexec is it?  

To find out type:

> mount -l | grep home

the "-l" is a lower-case L

---

### Post by Stephen Howard on 2007-07-11
By the way, this is what I get using the ldd command on the same file:

```
[FONT="Fixedsys"]$ ldd hldsupdatetool.bin[/FONT]
        linux-gate.so.1 =>  (0xffffe000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7e55000)
        /lib/ld-linux.so.2 (0xb7fb4000)
```

---

### Post by blastthisinferno on 2007-07-11
Stephen this is what I get when trying the mount

[IMG]http://img.photobucket.com/albums/v288/blastthisinferno/ldd.jpg[/IMG]

---

### Post by DBStevens on 2007-07-11
Stephen,

That would do it do it as well and if he is running a server environment it is a fairly decent default setup from a security stand point. 

I was trying to determine where the OP was when he issued the command to run the program since it is location sensitve.

The mount | grep command still won't  always answer that question.  It is possible to have home as a directory in a partition and for it not to appear as a mount table entry.

Isn't all the flexibility just great, got to love it ;-) .

---

### Post by DBStevens on 2007-07-11
blastthisinferno,

Could you do a cd /
followed by

ls -o

---

### Post by blastthisinferno on 2007-07-11
[IMG]http://img.photobucket.com/albums/v288/blastthisinferno/lscd.jpg[/IMG]

---

### Post by Stephen Howard on 2007-07-12
DBStevens, Do servers not have a /home partition?  Never having used one I don't know myself, but I'd have thought it would be reasonably fundamental to a unix-like setup.

Blastthisinferno, lets try something really desperate as an experiment.  Copy the file into /bin and see if you can execute it there.  My thinking is that we know that software in /bin must be capable of being executed otherwise you wouldn't have a bootable system.  If it works in /bin then that proves that its a path / permissions / mount problem.  If it doesn't work in /bin then I have no idea!!

If you want to do the above experiment, then do this from the directory you've put the file in:

> sudo cp hldsupdatetool.bin /usr/bin

cd /usr/bin

sudo ./hldsupdatetool.bin

Did it work??

Can you also post a copy of your /etc/fstab file?

---

### Post by blastthisinferno on 2007-07-12
Damn, that sounded promising Stephen.  Still got the error```
erich@bakery:/usr/bin$ sudo ./hldsupdatetool.bin
sudo: unable to execute ./hldsupdatetool.bin: No such file or directory
```
Here is my fstab file though.```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1dba2692-6f16-48cb-b47f-7e8587a28d0f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=017d54e5-8b03-48fe-83eb-3f6c5bd83fa6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by blastthisinferno on 2007-07-12
After nearly a week with this pain in the ***, I found the problem.  Apparently with the Ubuntu Feisty Fawn Server 7.04 installation, it doesn't install a file called **lib32gcc1**.  So all I had to do was ```
sudo apt-get install lib32gcc1
``` and everthing was fine and dandy.

I want to thank all the people who found this problem before me in what seems to be a line of forum posts.

Thanks everyone for the efforts.

---

### Post by DBStevens on 2007-07-12
I'm glad you found that blastthisinferno.

They must be assuming that a 64 bit system is only going to run 64 bit software.

Stephen, you do not have to have a partitIon called home, a simple directory in any partitIon can be called home.

My system which isn't a server install has no home partition.

---

### Post by Stephen Howard on 2007-07-13
blastthisinferno, how did you figure that out?

Kind of an anti-climax!

---

### Post by Stephen Howard on 2007-07-13
DBStevens, I didn't know that.  I'd always thought that those basic /usr etc pointers had to be mounted.

I've learnt something, thanks.

---

