---
title: "How to run Mercurial on MobaXterm"
date: 2021-02-20
forum: Any Other OS
---

### Post by susja on 2021-02-20
[COLOR=#242729][FONT=Arial]I'm using Windows 10 and have Cygwin and MobaXterm installed. I need to use Mercurial. It works fine from Cygwin but I want to run it from MobaXterm. I just installed Mercurial plugin for MobaXterm and it claimed that it should run with Python 2.7 In my case I have both Python 3 and Python 2. MobaXterm does not see Python 2. Here's my environment:[/FONT][/COLOR]
 MobaXterm:
 ~/Desktop @ BOS-LTIRM181511 
| => which hg
hg is aliased to `/bin/hg'
hg is /bin/hg
hg is /drives/c/MobaXterm/slash/bin/hg
                                                                                                                                                                                                &#10004;
________________________________________________________________________________
| ~/Desktop @ BOS-LTIRM181511 
| => which python
python is aliased to `ToolNotIncluded python'
                                                                                                                                                                                                &#10004;
________________________________________________________________________________
| ~/Desktop @ BOS-LTIRM181511 
| => which python3
python3 is /bin/python3
python3 is /drives/c/MobaXterm/slash/bin/python3
                                                                                                                                                                                                &#10004;
________________________________________________________________________________
| ~/Desktop @ BOS-LTIRM181511 
| => /cygdrive/c/Python27/python --version
Python 2.7.15
                                                                                                                                                                                                &#10004;
________________________________________________________________________________
| ~/Desktop @ BOS-LTIRM181511 
| =>
----
Cygwin:
$  hg --version
Mercurial Distributed SCM (version 5.0.2)
(see [https://mercurial-scm.org](https://mercurial-scm.org) for more information)

Copyright (C) 2005-2019 Matt Mackall and others
This is free software; see the source for copying conditions. There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

user@BOS-LTIRM181511 /usr/bin
$ which hg
hg is /usr/bin/hg
hg is /usr/bin/hg

user@BOS-LTIRM181511 /usr/bin
$ which python
python is /usr/bin/python
python is /cygdrive/c/Python27/python
python is /usr/bin/python

user@BOS-LTIRM181511 /usr/bin
$ which python3
-bash: type: python3: not found

user@BOS-LTIRM181511 /usr/bin
$ /cygdrive/c/Python27/python --version
Python 2.7.15

---
[COLOR=#242729][FONT=Arial]How could I fix it and make Mercurial run from MobaXterm[/FONT][/COLOR]

---

### Post by howefield on 2021-02-20
THread moved to the "*Any Other OS*" forum.

---

