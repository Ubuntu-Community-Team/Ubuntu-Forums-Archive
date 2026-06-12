---
title: "Help Got a problem. :-("
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by sevenofnine on 2007-09-26
i'm running 7.0.4 and i just got an error on log on. 

here is the error message.

your session only lasted less than 10 seconds. if you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. try logging in with one of the failsafe sessions to see if you can fix this problem.

i have been doing some of my own research on the problem and i had found that some other people have had the same problem cause it is dealing with the permissions with the file .ICEauthority and the other forums that i have been in have said about changing the filename. so i do that and then i still get the same error message but now it is saying that it can't find or open the libcrypt.so.11 file. so i have no idea what to do about this one now. so for any help or suggestions i would greatly appricate it.

sevenofnine:confused:

---

### Post by HermanAB on 2007-09-26
Press Ctrl-Alt-F2, log into the text console, then look at the system log file:
$ sudo tail -n 5000 /var/log/messages | less

You may be able to get a clue from that.

---

### Post by KIAaze on 2007-09-26
> this could mean that there is some installation problem or that you may be out of diskspace.
1)Did you check that you have enough diskspace left?
If you can't log in as normal user, log into failsafe mode (command-line) and run ```
df -h
``` to see the disk usage.
(ctrl+alt+(F1-F6) also works to bring up a console mode as suggested by previous poster.)

2)Have you tried searching for the libcrypt.so file on your system?

Here is a list of the possible locations where it should be, along with the packages through which it is installed:
```
locations                                                            packages
/usr/i386-uclibc-linux/lib/libcrypt.so			    libdevel/libuclibc-dev [universe]
/usr/lib/libcrypt.so					    libdevel/libc6-dev
/usr/lib/lsb2/libcrypt.so				    devel/lsb-build-base2 [universe]
/usr/lib/lsb3/libcrypt.so				    devel/lsb-build-base3 [universe]
/usr/lib64/libcrypt.so					    libdevel/libc6-dev-amd64

```
Source: [packages.ubuntu.com]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libcrypt.so&searchmode=searchfiles&case=insensitive&version=feisty&arch=i386")

To see if a file exists, do ```
ls /usr/lib64/libcrypt.so
``` for example, or to search for it:
```
sudo updatedb
locate libcrypt.so

```
or
```
find / -name  libcrypt.so 2>/dev/null
```

If libcrypt.so is missing, install or reinstall libc6-dev:
```
sudo apt-get install libc6-dev
```

edit:
I forgot that it is searching for **libcrypt.so.11**.
This could mean that you have libcrypt.so, but that it's only a link to libcrypt.so.11, which is missing.
In this case, you could maybe solve the problem by relinking it to an available libcrypt.so.xx in /usr/lib, but I wouldn't do this right away.
First try to solve the problem by reinstalling packages or freeing space.

But if you do find libcrypt.so on your system do ```
ls -l libcrypt.so
``` to see if it is a link and where it links to. ;)

---

