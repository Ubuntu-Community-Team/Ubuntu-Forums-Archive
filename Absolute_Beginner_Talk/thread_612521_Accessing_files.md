---
title: "Accessing files"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by jbguev on 2007-11-14
Hello All!

I am extremely new to Ubuntu/Linux/Unix, and I would really like to learn how to set things up correctly, which leads me to my issue: I just wanted to edit the index.html file that resides in the apache2 default folder, and I get a message saying that I do not have access privileges.  All of the folders in the main directory are assigned to the root user.  I did manage to change permissions on several folders (changing them to both read and write for all users).  This seemed to help, so then I got the idea to change the owner of the directories to my username.  All of this allowed me to edit and save the file, but then I tried to access the page in Firefox, and I got the message that the page was forbidden.

Anyway, I would really like to be able to create web-based documents and modify configuration files without ruining my system.  If someone could please give me a few pointers on changing file/folder permissions and direct me to some additional resources for the truly command-line moron, I would greatly appreciate it.

Thanks,

Jerry

P.S.: I already re-installed the 7.10 OS ( I love being able to do this in under an hour!)

---

### Post by SpiritIsReality on 2007-11-14
howdy
3or4links
Unified documentation site - I need your input [http://ubuntuforums.org/showthread.php?t=579726](http://ubuntuforums.org/showthread.php?t=579726)
Documentation of Ubuntu [http://ubuntuforums.org/showthread.php?t=602668](http://ubuntuforums.org/showthread.php?t=602668)
Networking And Wireless Documentation Links [http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation)
LTSP Documentation Links [http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation)

a good place to start would probably be here
[http://linuxcommand.org/](http://linuxcommand.org/)
when you get to [http://linuxcommand.org/wss0020.php](http://linuxcommand.org/wss0020.php)  
chapter 2 Aliases, [http://linuxcommand.org/wss0020.php#aliases](http://linuxcommand.org/wss0020.php#aliases) he will talk about opening the .bash_profile file. please see 
chapter 5 .bashrc [http://linuxcommand.org/wss0020.php#bashrc](http://linuxcommand.org/wss0020.php#bashrc) and what I did is use the .bashrc file in chapter 2 also. Hey, it's good form! haha!  ...Sometimes tutorials don't get updated, and I think Ubuntu quit using the .bash_profile file. 
cd ~/
ls -la
it won't be there.

then you might like to have a look at
[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)

if you have any questions, holler.
trails

---

### Post by mikewhatever on 2007-11-14
Opening your system for read and write access is not a good idea, especially on a server. To edit any file in the system, precede the command with sudo.
[https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29](https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29)

---

### Post by CatKiller on 2007-11-14
Also, there are some files that need to be owned by root, otherwise they don't work and your computer stops working, so changing the ownership of random files is a bad plan too. Using sudo for root access when you need it is a good thing.

---

### Post by jbguev on 2007-11-14
Thanks for the replies.  I found out about changing folder ownership the hard way.

---

### Post by SpiritIsReality on 2007-11-15
blessing in disguise.?

---

