---
title: "ati radeon fglrx problem :("
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by hammad1337 on 2007-07-25
This is the problem:
I have an ATI Radeon 7000 card which used to work perfectly with the default drivers already installed in Ubuntu.
However, I decided to install the fglrx "restricted" drivers, hoping it would give me better performance. These drivers messed up my system.

What I want to know is:
How can I remove the restricted drivers and all dependancies and return my driver configuration to default Ubuntu?

---

### Post by ajgreeny on 2007-07-25
Have you got a copy of your old /etc/X11/xorg.conf file?  If so just restore it with:-
```
sudo cp /etc/X11/xorg.conf~ /etc/X11/xorg.conf
```

Note that your backup may not be /etc/X11/xorg.conf~ but something else, so change the command accordingly.

Now restart x with Ctrl+Alt+Backspace or reboot and see if all works again.

If you have no backup then it's a case of reconfiguring x with:-
```
sudo dpkg-reconfigure xserver-xorg
```
and choosing ati or radeon when you get tom the graphics part and accepting the defaults for the rest

---

### Post by hammad1337 on 2007-07-26
I have already tried doing both.
I restored backup from xorg.conf.200716573469
AND,
I also tried using dpkg-reconfigure.
It still doesnt work.

I cannot run compiz. I get this error when I try to do so:
```

Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

```
And, I cannot run a game (dark-oberon0. I get this error if I run it:
```

 error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

```
I read in one of the threads that the libgl.so.1 error is specific for nvidia cards. I am puzzled. Please tell me what to do.

And, thanks for your reply :) .

---

