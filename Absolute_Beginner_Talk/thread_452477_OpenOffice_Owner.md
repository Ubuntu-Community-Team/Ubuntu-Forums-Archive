---
title: "OpenOffice Owner"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Takayakon on 2007-05-23
This isn't much of a problem I'm just wondering why when I create a Writer or Calc file in Open Office and save it. The permissions go to root and it shows the file in Nautilus as locked and the owner as root. Also it shows me the user as read only. Is this normal? Just curious how this works. Just thought it was odd I can't change permission of a file I created. Only thing I guess is Open Office is running as root when I open it in gnome menu.  It only seems to do this with Open Office files. However for some reason I can create and save files and open them later and still edit them. That's why I was curious. Thanks.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=33234&stc=1&d=1179933264[/IMG]

---

### Post by youthforlinux on 2007-05-23
I've never had that problem before but there is a way to make sure that you can write to that file.

```
sudo chown -R <your username> <path to the file>
```

or

```
gksudo nautilus <path to folder that the file is in>
```

then go to the file and change its permissions!!!!:popcorn::popcorn:

---

### Post by steve.horsley on 2007-05-23
I've never heard of anything like it. How do you launch OpenOffice?

Can you launch OpenOffice, then switch to a terminal and use the command
**ps -ef | grep office**
and see who it is running as.

---

### Post by lopagof on 2007-05-23
sudo nautilus then browse click properties and allow yourself read and write access

---

### Post by Takayakon on 2007-05-24
While changing the individual permission would work why should I have to do that with every file I create?

Also it appears office is running as me but there is another file running as root

luebckdj 17328     1  0 08:51 ?        00:00:00 /bin/sh /usr/lib/openoffice/program/soffice -writer -splash-pipe=5
root     17347 17328  4 08:51 ?        00:00:01 /usr/lib/openoffice/program/soffice.bin.bin -writer -splash-pipe=5

I've tried changing some permissions of those files but it didn't make any difference.

This is the command on the gnome menu to make writer to run: ooffice -writer

EDIT: 
I just tried running writer through the terminal as me: 
/usr/bin/ooffice: 3: /usr/lib/openoffice/program/ooqstart: Permission denied

It works for sudo though.

---

### Post by steve.horsley on 2007-05-24
That's scary. Something is elevating a launched process to root privilege. Mine looks like this:
```
steve     7236     1  0 19:05 pts/0    00:00:00 /bin/sh /usr/lib/openoffice/program/soffice -writer -splash-pipe=5
steve     7251  7236 11 19:05 pts/0    00:00:01 /usr/lib/openoffice/program/soffice.bin -writer -splash-pipe=5

```

And I'm launching mine with this command (from a terminal window):
**ooffice -writer**

Something must be setuid root in the ooffice program directory, which is very scary if true. Can you post the output of:
**ls -l /usr/lib/openoffice/program/**

If you look at the process numbering, yours is spawning four more processes than mine in between the first and second process. The output from **pstree -pu** might be interesting as well

---

### Post by bkristan on 2007-05-31
Did you find the solution for this? I had the same problem, and found that my Samsung printer driver was doing it. The solution came from this link:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg327279.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg327279.html)

I deleted my soffice.bin, renamed soffice.bin.bin to soffice.bin, and everything's back to normal (aside from anything else the stupid driver did to my system that I haven't discovered yet).

Hope that helps.

Bill

---

