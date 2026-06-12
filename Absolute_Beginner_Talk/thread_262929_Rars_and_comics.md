---
title: "Rars and comics"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by DiJEH on 2006-09-22
I can't seem to open rars even after installing unrar (I still get the same bloody error of an unreconised file type), is there Any proggy I can just get from apt-get and be damned with it?

Also how do you read image archives in a comic format? Google doesn't seem to be helping much and I'd rather not open each image in firefox.

---

### Post by whizbaby on 2006-09-22
Search vor *comic* in synaptic (don't know what's your rar-problem,though).

---

### Post by Druidor on 2006-09-22
install unrar to be able to unpack rar files

sudo apt-get install unrar


You have the multiverse repository enabled

---

### Post by DiJEH on 2006-09-22
Comix works great. Thanks for the help.

I should note I've got Unrar-free installed but archive manager still doesn't reconise the file.

---

### Post by MWAAAHAAA on 2006-09-22
If you installed unrar using your package manager, there's a chance it won't work, at least sometimes did not work out for me, but that was way back. Anyway to make sure that you are not misusing the program, you should unpack a rar archive using the following command:

unrar -x a_rar_file.rar

IF on the other hand you downloaded the binary version from rarlabs, the command is slightly different:

unrar x a_rar_file.rar

It might also be helpful to post the exact command you executed, and the exact output it gave you.

---

### Post by DiJEH on 2006-09-22
stephen@Stephen:~$ unrar x XYZ.rar
bash: unrar: command not found

Thats what terminal gives me (XYZ isn't the file name, changed it obviously(.

I used synaptic to install unrar, didn't use aptget or anything.

---

### Post by bodhi.zazen on 2006-09-22
**urar** xyz.rar

(no n)

---

### Post by MWAAAHAAA on 2006-09-22
'command not found' means it cannot find the command, i.e. unrar, you executed

---

### Post by DiJEH on 2006-09-22
So how do I deal with this?

---

### Post by MWAAAHAAA on 2006-09-22
As I am not using the unrar from the ubuntu repository, you might try what bodhi.zazen suggested. If that doesn't work, try updating your slocate database:

sudo updatedb

And then try locating the unrar:

locate unrar

It should give you the location where unrar is installed. It should be in /usr/bin. If it's not in your PATH, then you get the message that the command could not be found.

Tell me how it worked out.

---

### Post by DiJEH on 2006-09-22
Did it and got the following.

stephen@Stephen:~$ locate unrar
/var/cache/apt/archives/unrar-free_1%3a0.0.1-2_i386.deb
/var/lib/dpkg/info/unrar-free.md5sums
/var/lib/dpkg/info/unrar-free.list
/home/stephen/Desktop/rar/unrar
/usr/bin/unrar-free
/usr/share/doc/bash/completion-contrib/unrar
/usr/share/doc/unrar-free
/usr/share/doc/unrar-free/README.Debian
/usr/share/doc/unrar-free/AUTHORS
/usr/share/doc/unrar-free/todo
/usr/share/doc/unrar-free/changelog.Debian.gz
/usr/share/doc/unrar-free/copyright
/usr/share/man/man1/unrar-free.1.gz

---

### Post by whizbaby on 2006-09-22
So I guess your command is *unrar-free* instead of *unrar*. Ever tried typing *unrar-free* in terminal, just to see?
(because it exists in /usr/bin)

---

### Post by DiJEH on 2006-09-22
Getting much closer but still no dice.

stephen@Stephen:~$ unrar-free unrar-free XYZ.rar
unrar-free: invalid archive 'unrar-free': Bad address
Usage: unrar-free [OPTION...] ARCHIVE [FILE...] [DESTINATION]
Try `unrar-free --help' or `unrar-free --usage' for more information.

Isn't it possible to set it so rars are opened as easy as zips?

---

### Post by whizbaby on 2006-09-22
> **DiJEH said:**
> stephen@Stephen:~$ ***unrar-free unrar-free*** XYZ.rar

Perhaps try with not typing the command twice (you tried to unrar the command itself, one should not expect this to make much sense). BTW it printed you a nice howto use it (arguments in square brackets [] are *optional* in every command description. So try it the easy way with
*unrar-free XYZ.rar*).

---

### Post by bodhi.zazen on 2006-09-22
hmmmm....

[size=2]**unrar -e xyz.rar**[/size]

---

### Post by whizbaby on 2006-09-22
EDIT:removed because bodhi edited his last post. (so you too didn't find *urar*?)

---

### Post by DiJEH on 2006-09-22
I tried it several times and got it right 4 out of 5 I'm sure, just copied the one I got wrong, same output from all though.

---

### Post by MWAAAHAAA on 2006-09-22
DO NOT USE the 'e' or '-e' option on unrar, it will dump all contents to the same directory without any regard for the directory structure of the archive.
ALWAYS USE 'x' or '-x' unless you know what you're doing.

So it worked out allright now?

---

### Post by n0dl on 2006-09-22
you have to get unrar-nonfree from the multiverse repo. edit your /etc/apt/sources.list and add "multiverse" without quotes to where the line says universe

---

### Post by redDEADresolve on 2006-09-22
An easier way to make sure your system can read rars is to go to [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/) click on the download page and copy and paste the directions. This will allow you to easily download some cool features for Ubuntu. Like playing mp3, watching dvds, flash and unrar. 

Then just go to [http://comix.sourceforge.net/](http://comix.sourceforge.net/) and download comix 3.5.1 unarchive it and follow the very easy instructions in the read me.

---

