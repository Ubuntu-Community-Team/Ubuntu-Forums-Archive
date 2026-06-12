---
title: "RT61 wireless setup"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by pshnfry on 2006-05-07
How do I save an edited binary file from the following command:
sudo vi -b rt61sta.dat

---

### Post by Stone123 on 2006-05-07
use dos2linux (search on synaptic) tool to convert that file to linux type.
then use gedit to edit it

But correct answer would me:

:wq
and then enter .  man vi in cli for more info

---

### Post by sophtpaw on 2006-05-07
[QUOTE=pshnfry]How do I save an edited binary file from the following command:
sudo vi -b rt61sta.dat[/QUOTE]

Is that a Ralink pci device you're using. It's what i'm using

--
sophtpaw

---

### Post by pshnfry on 2006-05-08
man vi. Why didn't I try that?  Looking through man vi though I still don't see the command listed by Stone123 (:wq) and so can't retain it in context.  Common problem with all of the Linux answers and tutorials (type this ....).

I'll now go looking for dos2linux (had tried that command, but the context given didn't indicate it was a downloadable option and the errors didn't make sense).

Sothpaw - yes, a Repotec pci WP0854A.

Thank you.

---

### Post by pshnfry on 2006-05-08
This gets better every night.  Where do I find dos2linux? I've enabled all the repositories listed under Add Applications and searched in advanced mode, I've searched this forum, I've tried apt-get. Zip. Just in case I also tried man dos2linux - nothing.

Where would this be?

---

### Post by tenshu on 2006-05-08
[QUOTE=pshnfry]This gets better every night.  Where do I find dos2linux? I've enabled all the repositories listed under Add Applications and searched in advanced mode, I've searched this forum, I've tried apt-get. Zip. Just in case I also tried man dos2linux - nothing.

Where would this be?[/QUOTE]

use the search function of synaptic 
(try this first for every problem you reach)

did you get your rt61 working under dapper?

---

### Post by pshnfry on 2006-05-09
In my post above perhaps I should have used the term "..searched the Synaptic Package Manager, (which can be run by clicking "Advanced" in the "File" menu of Applications, Add applications)?

I have searched synaptic.  No dos2linux. I have enabled all repositories listed in Breezy.

No, I didn't get rt61 working in dapper, I'm a Breezy user.  Yes, I had some succes last night with rt61 in breezy, I'm reviewing the steps taken to find the key step and then will research how to make that "stick".

---

### Post by Stone123 on 2006-05-09
rambo3@ubuntu:~$ apt-cache search dos2unix

sysutils - Miscellaneous small system utilities - dummy package
tofrodos - Converts DOS <-> Unix text files, alias tofromdos

rambo3@ubuntu:~$ apt-cache  policy tofrodos
tofrodos:
  Installerad: 1.7.6-1
  Kandidat: 1.7.6-1
  Versionstabell:
 *** 1.7.6-1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
        100 /var/lib/dpkg/status

i guess you did write there , but it depends how/what  you search. Change to search "filnames and description" so maby you get more results.

Just install tofrodos
So this command is in both these program packs.
/ Btw this is an old utility pack so it should be in breezy too

---

### Post by pshnfry on 2006-05-09
peter@ubuntu:~$ apt-cache search dos2unix
peter@ubuntu:~$ apt-cache search tofrodos
peter@ubuntu:~$ apt-cache search tofromdos
sysutils - Miscellaneous small system utilities.
peter@ubuntu:~$

My search of Synaptic Package Manager (GUI) was "Description and Name" looking for dos2unix.

Is there a particular repository I can check is enabled on my pc?

---

