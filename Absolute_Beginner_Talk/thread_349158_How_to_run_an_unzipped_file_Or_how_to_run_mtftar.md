---
title: "How to run an unzipped file? Or how to run mtftar?"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by Aktrop on 2007-01-29
Hi,

I'm a new and somewhat traumatized user of Ubuntu. I started out thinking it would be nice to have Ubuntu along with my windows XP pro. So I installed it - that was the beginning of the end. The long and short of it is that I had to wipe my drive clean, and now I only run Ubuntu.

Luckily I backed up all my work before my little experiment, which went quite so awry. Now I have found a utility, mtftar that will convert my windows .bkf to .tar:
[http://gpl.internetconnection.net/files/mtftar.tar.gz](http://gpl.internetconnection.net/files/mtftar.tar.gz)
I've downloaded it, and unzipped it with archive manager. 

But now what? How do I proceed? I tried 
sudo aptitude
but no luck. I tried add/remove, but no luck.

Please help - with as many detailed instructions as possible! The Ubuntu community has been AWESOME - I'm counting on you guys...

-Aktrop

---

### Post by sardion on 2007-01-29
Well, this is what is known as "building from source".  Don't get scared, for mtftar this is easy, I just did it myself to check.

Open a terminal and cd to where you have untarred the files from the tar.gz.
In mycase, I downloaded the tar.gz file to /home/d/Downloads so (i will preface with % anythng to type in the terminal):

% cd /home/d/Downloads
% tar xzf mtftar.tar.gz
% cd mtftar

if you already untarred the archive you can skip the tar xzf command (that just extracts it).
Once you are in the mtftar folder (check by doing)

% ls

you should see anomng other things mtftar.c
Then:

% make

This will build the mtftar file from the source code (you will see a lot of output that means nothing to you, don't worry about it).
Once its dont (you have a prompt again)

% sudo cp mtftar /usr/local/bin/

That will copy mtftar into your directory of programs.  Then you can run mtftar as any other command:

% mtftar

Not having the problem you had, I don't know how to use mtftar but I assume you can figure that out.

---

### Post by Aktrop on 2007-01-29
Thanks for a wonderful post!

Here's what I'm getting:

aktrop@aktrop-laptop:~$ cd mtftar
aktrop@aktrop-laptop:~/mtftar$ ls
CHANGELOG    mtf.h        mtftar.c  util.c
DESCRIPTION  mtfheader.c  README    util.h
LICENSE      mtfscan.c    tar.h
Makefile     mtfstream.c  tarout.c
aktrop@aktrop-laptop:~/mtftar$ make
cc -Wall -O9 -s -D_GNU_SOURCE   -c -o mtftar.o mtftar.c
mtftar.c:1:22: error: features.h: No such file or directory
In file included from mtftar.c:3:
mtf.h:6:23: error: sys/types.h: No such file or directory
mtf.h:7:20: error: unistd.h: No such file or directory
mtf.h:10:18: error: time.h: No such file or directory
In file included from mtftar.c:3:
mtf.h:23: error: expected specifier-qualifier-list before ‘off64_t’
mtf.h:34:20: error: string.h: No such file or directory
mtf.h:200: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘mtf_header_datetime’
In file included from mtftar.c:4:
tar.h:23: error: expected declaration specifiers or ‘...’ before ‘time_t’
tar.h:28: error: expected declaration specifiers or ‘...’ before ‘time_t’
tar.h:30: error: expected declaration specifiers or ‘...’ before ‘time_t’
mtftar.c:7:22: error: sys/stat.h: No such file or directory
mtftar.c:9:19: error: stdio.h: No such file or directory
mtftar.c:10:19: error: fcntl.h: No such file or directory
mtftar.c:12:20: error: stdlib.h: No such file or directory
mtftar.c:13:19: error: ctype.h: No such file or directory
mtftar.c: In function ‘usage’:
mtftar.c:17: warning: implicit declaration of function ‘fprintf’
mtftar.c:17: warning: incompatible implicit declaration of built-in function ‘fprintf’
mtftar.c:17: error: ‘stderr’ undeclared (first use in this function)
mtftar.c:17: error: (Each undeclared identifier is reported only once
mtftar.c:17: error: for each function it appears in.)
mtftar.c:25: warning: implicit declaration of function ‘exit’
mtftar.c:25: warning: incompatible implicit declaration of built-in function ‘exit’
mtftar.c: In function ‘check_1arg’:
mtftar.c:47: warning: implicit declaration of function ‘tolower’
mtftar.c: In function ‘main’:
mtftar.c:83: error: ‘off64_t’ undeclared (first use in this function)
mtftar.c:83: error: expected ‘;’ before ‘idxpos’
mtftar.c:95: error: ‘time_t’ undeclared (first use in this function)
mtftar.c:95: error: expected ‘;’ before ‘mtime’
mtftar.c:105: warning: implicit declaration of function ‘getopt’
mtftar.c:111: warning: implicit declaration of function ‘open’
mtftar.c:111: error: ‘optarg’ undeclared (first use in this function)
mtftar.c:111: error: ‘O_RDONLY’ undeclared (first use in this function)
mtftar.c:111: error: ‘O_NOCTTY’ undeclared (first use in this function)
mtftar.c:112: error: ‘O_LARGEFILE’ undeclared (first use in this function)
mtftar.c:115: warning: implicit declaration of function ‘perror’
mtftar.c:116: warning: incompatible implicit declaration of built-in function ‘exit’
mtftar.c:120: error: ‘O_WRONLY’ undeclared (first use in this function)
mtftar.c:120: error: ‘O_CREAT’ undeclared (first use in this function)
mtftar.c:123: warning: incompatible implicit declaration of built-in function ‘exit’
mtftar.c:142: error: ‘idxpos’ undeclared (first use in this function)
mtftar.c:143: warning: implicit declaration of function ‘sscanf’
mtftar.c:143: warning: incompatible implicit declaration of built-in function ‘sscanf’
mtftar.c:145: error: ‘mtime’ undeclared (first use in this function)
mtftar.c:147: warning: incompatible implicit declaration of built-in function ‘sscanf’
mtftar.c:151: warning: incompatible implicit declaration of built-in function ‘sscanf’
mtftar.c:155: warning: implicit declaration of function ‘strchr’
mtftar.c:155: warning: incompatible implicit declaration of built-in function ‘strchr’
mtftar.c:159: warning: implicit declaration of function ‘fputs’
mtftar.c:159: error: ‘stderr’ undeclared (first use in this function)
mtftar.c:164: warning: implicit declaration of function ‘strdup’
mtftar.c:164: warning: incompatible implicit declaration of built-in function ‘strdup’
mtftar.c:167: warning: incompatible implicit declaration of built-in function ‘exit’
mtftar.c:171: warning: implicit declaration of function ‘atoi’
mtftar.c:179: warning: implicit declaration of function ‘isatty’
mtftar.c:188: warning: incompatible implicit declaration of built-in function ‘exit’
mtftar.c:192: warning: incompatible implicit declaration of built-in function ‘exit’
mtftar.c:194: warning: implicit declaration of function ‘lseek64’
mtftar.c:194: error: ‘SEEK_SET’ undeclared (first use in this function)
mtftar.c:196: warning: incompatible implicit declaration of built-in function ‘exit’
mtftar.c:202: warning: incompatible implicit declaration of built-in function ‘exit’
mtftar.c:204: warning: implicit declaration of function ‘memcmp’
mtftar.c:205: warning: incompatible implicit declaration of built-in function ‘fprintf’
mtftar.c:209: error: ‘struct mtf_stream’ has no member named ‘stringtype’
mtftar.c:212: warning: incompatible implicit declaration of built-in function ‘exit’
mtftar.c:226: error: ‘optind’ undeclared (first use in this function)
mtftar.c:229: error: too many arguments to function ‘tarout_file’
mtftar.c:241: warning: incompatible implicit declaration of built-in function ‘exit’
mtftar.c:252: warning: pointer targets in assignment differ in signedness
mtftar.c:253: warning: incompatible implicit declaration of built-in function ‘fprintf’
mtftar.c:254: warning: implicit declaration of function ‘free’
mtftar.c:256: warning: pointer targets in assignment differ in signedness
mtftar.c:260: warning: pointer targets in assignment differ in signedness
mtftar.c:281: warning: incompatible implicit declaration of built-in function ‘fprintf’
mtftar.c:283: warning: pointer targets in assignment differ in signedness
mtftar.c:287: warning: pointer targets in assignment differ in signedness
mtftar.c:291: warning: pointer targets in assignment differ in signedness
mtftar.c:300: warning: pointer targets in assignment differ in signedness
mtftar.c:302: warning: implicit declaration of function ‘mtf_header_datetime’
mtftar.c:304: error: too many arguments to function ‘tarout_dir’
mtftar.c:324: warning: pointer targets in assignment differ in signedness
mtftar.c:327: warning: implicit declaration of function ‘malloc’
mtftar.c:327: warning: incompatible implicit declaration of built-in function ‘malloc’
mtftar.c:327: warning: implicit declaration of function ‘strlen’
mtftar.c:327: warning: incompatible implicit declaration of built-in function ‘strlen’
mtftar.c:330: warning: incompatible implicit declaration of built-in function ‘exit’
mtftar.c:332: warning: implicit declaration of function ‘sprintf’
mtftar.c:332: warning: incompatible implicit declaration of built-in function ‘sprintf’
mtftar.c:334: error: too many arguments to function ‘tarout_dir’
mtftar.c:341: error: ‘struct mtf_stream’ has no member named ‘abspos’
mtftar.c:341: error: ‘struct mtf_stream’ has no member named ‘ready’
mtftar.c:342: warning: pointer targets in assignment differ in signedness
mtftar.c:345: warning: incompatible implicit declaration of built-in function ‘fprintf’
mtftar.c:348: warning: incompatible implicit declaration of built-in function ‘malloc’
mtftar.c:348: warning: incompatible implicit declaration of built-in function ‘strlen’
mtftar.c:351: warning: incompatible implicit declaration of built-in function ‘exit’
mtftar.c:353: warning: incompatible implicit declaration of built-in function ‘sprintf’
mtftar.c:359: warning: implicit declaration of function ‘printf’
mtftar.c:359: warning: incompatible implicit declaration of built-in function ‘printf’
mtftar.c:370: warning: incompatible implicit declaration of built-in function ‘fprintf’
mtftar.c:373: warning: implicit declaration of function ‘puts’
mtftar.c:389: error: too many arguments to function ‘tarout_file’
mtftar.c:418: warning: implicit declaration of function ‘isalpha’
mtftar.c:444: warning: implicit declaration of function ‘fflush’
mtftar.c:447: warning: incompatible implicit declaration of built-in function ‘exit’
mtftar.c:451: warning: incompatible implicit declaration of built-in function ‘exit’
make: *** [mtftar.o] Error 1
aktrop@aktrop-laptop:~/mtftar$ sudo cp mtftar /usr/local/bin/
cp: cannot stat `mtftar': No such file or directory
aktrop@aktrop-laptop:~/mtftar$ 

So I'm not sure where to go from here.

-Aktrop

---

### Post by punx45 on 2007-01-29
any chance you read README?

on the rare occasion where i attempt a source compile and install I usually check README or other docs before i do anything.   most of the time they are useless but sometimes there are instructions.

---

### Post by adam.funk on 2007-02-01
I didn't have any problems building mtftar, but I can't get it to run correctly.

For example, if the .bkf really contains

C:\Documents and Settings\alice\My Documents\foo.doc
C:\Documents and Settings\bob\My Documents\bar.doc
C:\Documents and Settings\bob\My Documents\fubar.doc
...

(and I know it does have the full directory structure, because I unpacked it on a Windows machine to check) the tar file produced by mtftar flattens the tree down to one directory below the drive letter:

C:/Documents and Settings/foo.doc
C:/Documents and Settings/bar.doc
C:/Documents and Settings/fubar.doc
...

Has anyone  figured out how to get the full directory tree out?  Or can anyone recommend another utility for unpacking *.bkf files?

---

### Post by adam.funk on 2007-02-06
I contacted internetconnection.net and the developer very helpfully
looked into this.  The program had been tested on backup files from
Windows NT and 2000 Advanced Server but he discovered a discrepancy
with the files I had (from 2000 not "server"), and fixed it.  The
current version (now on that website) correctly handles the backup
files I'm working with.

---

### Post by ubtutu on 2008-01-14
To Aktrop who was having compile problems, I had the same problem as you but fixed it by instllaing the build-essential package:

```
sudo apt-get install build-essential
```

After that, mtftar compiled fine

---

