---
title: "How to Install 'NewsPost' via TERMINAL ??"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-09-01
I'm having some problems installing this program - can someone tell me what to do next OR what I should be doing?

Thanks :)

These are the instructions:

```


Newspost 2.1.1
http://newspost.unixcab.org/

INSTALLATION

Just type 'make' then 'make install' to install to /usr/local.
If you want it installed to a different directory, type
'make install PREFIX=/yourdir'. You can also specify BINDIR and 
MANDIR separately.

The generic Makefile should work on most systems.  However, if
you are running Solaris you should type 'make solaris', and users
of QNX should type 'make qnx'.  The Makefile uses gcc by default,
so you should edit the first 2 lines of the Makefile if you are
using another compiler.

Also see base/newspost.h for some compile-time options.

USAGE

See the man page for detailed information and examples. 
For a quick start, type "newspost -h" to see available options.

NOTE

Newspost automatically appends the name of the binary attachment 
you are posting and which part of that file your are posting.
For example, if you use the commandline

$ newspost -s "This is my favorite album" *.mp3

The subject lines posted would be:

This is my favorite album - Track01.mp3 (1/2)
This is my favorite album - Track01.mp3 (2/2)
This is my favorite album - Track02.mp3 (01/17)
This is my favorite album - Track02.mp3 (02/17)
This is my favorite album - Track02.mp3 (03/17)
etc...

Nothing is appended to the subject line when the -t option is used.

See the EXAMPLES section of the manpage for more information.

FEEDBACK

Feedback is welcome, but patches are more welcome, as well as
makefiles for different OSes.  Please report any bugs you find.

Jim Faulkner
newspost@sdf.lonestar.org


```

[IMG]http://i11.tinypic.com/5zc4lyg.jpg[/IMG]

[IMG]http://i1.tinypic.com/5z1kljs.jpg[/IMG]

[IMG]http://i17.tinypic.com/63mv09s.jpg[/IMG]

---

### Post by Kitsun on 2007-09-01
Correct me if I'm wrong, since I'm still quite new to Ubuntu, but wouldn't putting sudo in front of the command fix this?

sudo make install

Thats how I,ve always solved these problems.

---

### Post by chrome307 on 2007-09-01
Thanks for the input but in this case it doesn't make any difference :confused:

---

### Post by schorsch on 2007-09-01
Newspost 2.1.1-4 is in the repos (universe) ...... so there is no need to compile it by yourself ...

---

### Post by chrome307 on 2007-09-01
Okay thanks for letting me know :)

Without a frontend it's difficult for me to post eg

```


user@user-ubuntu:~$ newspost -h

Newspost version 2.1.1
Copyright (C) 2001 - 2003 Jim Faulkner
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

Usage: newspost [OPTIONS [ARGUMENTS]] file1 file2 file3...
Options:
  -i ARG - hostname or IP of the news server
  -z ARG - port number on the news server
  -u ARG - username on the news server
  -p ARG - password on the news server
  -f ARG - your e-mail address
  -F ARG - your full name
  -o ARG - your organization
  -n ARG - newsgroups to post to
  -s ARG - subject
  -w ARG - newsgroup to put in the Followup-To header
  -m ARG - e-mail address to put in the Reply-To header
  -r ARG - reference these message IDs
  -x     - do NOT include "X-No-Archive: yes" header
  -X ARG - a complete header line
  -q     - include "File x of y" in subject line
  -y     - yencode instead of uuencode
  -e ARG - text prefix
  -E     - write text prefix in text editor set by $EDITOR
  -c ARG - generate SFV file
  -a ARG - generate PAR files
  -A ARG - number of PAR volumes to create
  -B ARG - number of files per PAR volume
  -l ARG - number of lines per message
  -t     - post one file as plain text
  -T ARG - time to wait before posting
  -k ARG - use this directory for storing temporary files
  -d     - set current options as default
  -D ARG - disable or clear another option
  -v     - be verbose
  -V     - print version info and exit
  -h     - display this help screen and exit
Please see the newspost manpage for more information and examples.


```

```


user@user-ubuntu:~$ newspost -i unlimited.newshosting.com -z 119 -u MY USERNAME REMOVED  -p MY PASSWORD REMOVED  -f MY EMAIL ADDRESS REMOVED  -F CHRoME3o7 -n alt.binaries.test  -s "Bebel Gilberto - Tanto Tempo" *.mp3

WARNING: No such file or directory *.mp3 - SKIPPING
No files to post!



```

Unfortunately I can't seem to work out all the required parameters to begin posting :(

Also the two suggested 'frontends' 

GNewspost
KNewspost

Don't seem to be available :(

---

### Post by schorsch on 2007-09-01
You could try to mask the asterisk by using "\*.mp3" (without the quotes) as first aid. Sorry, I can just guess as I do not use this app .....

---

### Post by chrome307 on 2007-09-01
It didn't work but 'Thank You' for your input and suggestions :)

---

### Post by schorsch on 2007-09-01
I do not know if this is the actual version but I found a RPM-Package for GNewspost [here]("http://rpm.pbone.net/index.php3/stat/4/idpl/4093875/com/gnewspost-0.6-1tex.i586.rpm.html"). Perhaps you can convert it into a DEB-package via alien .....

---

### Post by chrome307 on 2007-09-01
You keep on delivering the goods !! :)

Unfortunately I don't know how to convert ....... or worse still (don't laugh!) how to download it from that page :confused:

BTW Are you using WINE ??

If so could you try this out and see if you can get it to work?

```


http://powerpost.cjb.net/


```

Reading earlier threads on this forum this is meant to work with WINE but it fails to open on my PC.

---

### Post by schorsch on 2007-09-01
... no, I do not use wine .... I managed to get every thing I need to run without wine .... and right at the moment I have some problems to run the package I converted via alien and got from the website I mentioned .....

---

### Post by MenZa on 2007-09-01
> **schorsch said:**
> ... no, I do not use wine .... I managed to get every thing I need to run without wine .... and right at the moment I have some problems to run the package I converted via alien and got from the website I mentioned .....

Alien generally isn't a good tool to use. The packages were built as RPM packages, not DEB packages.

---

### Post by schorsch on 2007-09-01
I agree .... but I have not found a DEB package yet .... ;-)

---

### Post by MenZa on 2007-09-01
> **schorsch said:**
> I agree .... but I have not found a DEB package yet .... ;-)

Build it yourself then. :)

---

### Post by schorsch on 2007-09-01
.. done ... :-) ... for knewspost ...

---

