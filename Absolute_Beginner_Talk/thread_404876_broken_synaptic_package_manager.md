---
title: "broken synaptic package manager"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by grekei on 2007-04-09
I have a broken package (taskjuggler) in synaptics which will not install or uninstall.I have used several command lines that I have retrieved from various sources.
for eg. 'dpkg --configure -a' and 'apt-get install -f'.All methods so far have failed ,as a newbie I dont know where to go next .Can any one offer another suggestion?

---

### Post by Bachstelze on 2007-04-09
What do those commands give you ?

---

### Post by tonyr1988 on 2007-04-09
Make sure you use sudo in front of them, such as:

> sudo dpkg --configure -a
sudo apt-get install -f

If you try something and it gives you a permissions error, it's a good idea to try it again with "sudo" in front.

---

### Post by grekei on 2007-04-09
Get the following:
 sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/1179kB of archives.
After unpacking 0B of additional disk space will be used.
Selecting previously deselected package taskjuggler.
(Reading database ... 86163 files and directories currently installed.)
Preparing to replace taskjuggler 2.2.0-1ubuntu1 (using .../taskjuggler_2.2.0-1ubuntu1_i386.deb) ...
Unpacking replacement taskjuggler ...
touch: missing file operand
Try `touch --help' for more information.
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
touch: missing file operand
Try `touch --help' for more information.
dpkg: error processing /var/cache/apt/archives/taskjuggler_2.2.0-1ubuntu1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
touch: missing file operand
Try `touch --help' for more information.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/taskjuggler_2.2.0-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
and also get
laptop:~$ dpk --configure -a
bash: dpk: command not found
Hope this gives someone a clue ,thanks for input

---

### Post by Nythain on 2007-04-09
try
sudo aptitude clean
might help
also you left the g off dpkg... and remember to sudo it... sudo dpkg --configure -a

---

### Post by grekei on 2007-04-09
Thanks for reply,got same answer after 'clean' command.When I corrected spelling on 
'configure' command, the terminal returns nothing except to start another line asking for another command

---

### Post by zvacet on 2007-04-09
**synaptic>edit>fix broken packages**

If that doesn´t help

```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by grekei on 2007-04-09
thank you for the input!Still not working.your first suggestion ran the synaptic graphic environment which showed no packages broken but still would not install or remove 'taskjuggler'.Your second suggestion gave the following:
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1179kB of archives. After unpacking 0B will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe taskjuggler 2.2.0-1ubuntu1 [1179kB]
Fetched 1179kB in 9s (119kB/s)
(Reading database ... 86163 files and directories currently installed.)
Preparing to replace taskjuggler 2.2.0-1ubuntu1 (using .../taskjuggler_2.2.0-1ubuntu1_i386.deb) ...
Unpacking replacement taskjuggler ...
touch: missing file operand
Try `touch --help' for more information.
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
touch: missing file operand
Try `touch --help' for more information.
dpkg: error processing /var/cache/apt/archives/taskjuggler_2.2.0-1ubuntu1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
touch: missing file operand
Try `touch --help' for more information.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/taskjuggler_2.2.0-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

Dose the above help ?

---

### Post by zvacet on 2007-04-09
Did you ry to install it from source? If I´m right go to the same folder in wich you compiled and
```
sudo make uninstall
```

If you realy need that program you can download it´s rpm file and after that

```
sudo alien program_name rpm
```

Be sure that you have alien program installed.It is in synaptic.

---

### Post by grekei on 2007-04-10
Thanks again for the response.The install attempt was originally done with synaptic from the repositories.I dont care about the programme,wish I had never touched it.The problem now ,is that it has stopped any update or use of synaptic working as it should because it keeps trying to install it, even though synaptic lists it as installed.

---

### Post by ramjet_1953 on 2007-04-10
OK, it is obvious that [COLOR="Red"]taskjuggler[/COLOR] is the problem and all of the above help was fruitless.

Open a console and type in the following:

Code:

[COLOR="Blue"]sudo gedit /var/lib/dpkg/status
[/COLOR]

Search through the file for any reference to taskjuggler and CAREFULLY delete all of that entry.

Save the file

Code:

[COLOR="Blue"]sudo apt-get update[/COLOR]

Your problem should now be solved, as Synaptic can no longer see this errant package and as disk space is taken up, it will be over-written.

Regards,
Roger :cool:

---

### Post by msak007 on 2007-04-10
There's a bug for this problem:

[https://bugs.launchpad.net/ubuntu/+source/taskjuggler/+bug/48721](https://bugs.launchpad.net/ubuntu/+source/taskjuggler/+bug/48721)

Hasn't been updated or touched since June, so not sure how relevant it is but it's the same exact version number / filename giving you the error. Try the suggested solution in there and see if it works for you.

---

### Post by grekei on 2007-04-10
Roger,my hero, many thanks worked a treat.Has been a great learning experience.
By deleting windows I appear to have started on a bit of an adventure and this problem has actually made me more committed than ever to become proficient.Thanks again to any one who contributed

---

