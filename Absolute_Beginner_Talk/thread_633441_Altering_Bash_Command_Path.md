---
title: "Altering Bash Command Path"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by wescrow on 2007-12-06
I have seen a few of these posts around here but none seem to address my specific problem.

For purposes of reference, I am running Ubuntu server 7.10 with the desktop installed on top of that.

I have been attempting to change my path so that I can call shell scripts I have written in my personal bin "/home/wescrow/bin" without the directory info.  I have attempted to export the path in my ".bashrc" file.  This does change my path.  

When I call "$PATH" is says:
"-bash: /home/wescrow/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/wescrow/bin:/home/wescrow/bin/: No such file or directory"

I notice that the directory has shown up 3 times in my "$PATH" call.  I can only assume that this happened while I was attempting to set it.  I don't understand why if my directory shows up in the "$PATH" call the shell script wouldn't work.

I don't have a ".bash_profile" file.

all my .bash files are like this:

     rw------- 1 wescrow wescrow 3.5K 2007-12-06 01:06 .bash_history
     rw-r--r-- 1 wescrow wescrow  220 2007-12-05 12:43 .bash_logout
     rw-r--r-- 1 wescrow wescrow 2.4K 2007-12-06 14:53 .bashrc
     rw-r--r-- 1 wescrow wescrow 2.3K 2007-12-06 00:50 .bashrc~
     rw-r--r-- 1 wescrow wescrow 2.3K 2007-12-06 14:52 .bashrcBACKUP

My test bash file is:

     #!/bin/bash
     echo "hi"

when I type "test" nothing happens.
when I type "/home/wescrow/bin/test" I get "hi"

What am I doing wrong?

---

### Post by master_kernel on 2007-12-06
> **wescrow said:**
> I have seen a few of these posts around here but none seem to address my specific problem.

For purposes of reference, I am running Ubuntu server 7.10 with the desktop installed on top of that.

I have been attempting to change my path so that I can call shell scripts I have written in my personal bin "/home/wescrow/bin" without the directory info.  I have attempted to export the path in my ".bashrc" file.  This does change my path.  

When I call "$PATH" is says:
"-bash: /home/wescrow/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/wescrow/bin:/home/wescrow/bin/: No such file or directory"

I notice that the directory has shown up 3 times in my "$PATH" call.  I can only assume that this happened while I was attempting to set it.  I don't understand why if my directory shows up in the "$PATH" call the shell script wouldn't work.

I don't have a ".bash_profile" file.

all my .bash files are like this:

     rw------- 1 wescrow wescrow 3.5K 2007-12-06 01:06 .bash_history
     rw-r--r-- 1 wescrow wescrow  220 2007-12-05 12:43 .bash_logout
     rw-r--r-- 1 wescrow wescrow 2.4K 2007-12-06 14:53 .bashrc
     rw-r--r-- 1 wescrow wescrow 2.3K 2007-12-06 00:50 .bashrc~
     rw-r--r-- 1 wescrow wescrow 2.3K 2007-12-06 14:52 .bashrcBACKUP

My test bash file is:

     #!/bin/bash
     echo "hi"

when I type "test" nothing happens.
when I type "/home/wescrow/bin/test" I get "hi"

What am I doing wrong?
You can't name the program test because "test" is an important command in Linux; test runs /usr/bin/test. Use a name like test1.

---

### Post by SpacePilot on 2007-12-06
I dont know what you have been messing around with there, but the correct way to set the path is like this.

export PATH=$PATH:/path/you/are/adding/here/

---

### Post by wescrow on 2007-12-06
> **master_kernel said:**
> You can't name the program test because "test" is an important command in Linux; test runs /usr/bin/test. Use a name like test1.

Ah.. Yes. I am new to this.  I changed the file name to test1 and it works perfectly.  Thank you.

---

