---
title: "Need help installing the ipw2200 driver."
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by Fragma on 2006-01-10
Hi everyone,

I installed ubuntu on my Dell 700m and tried to fix the wireless issue via this helpful guide:

[http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)


I downloaded the ipw2200 firmware and ran the code in the terminal to install it

sudo tar xvzf ipw2200-fw-2.3.tgz
sudo cp ipw-2.3-*.fw /usr/lib/hotplug/firmware/



However, I get this error after I enter the password

700m:~$ sudo tar xvzf ipw2200-fw-2.3.tgz
Password:
tar: ipw2200-fw-2.3.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors



Am I doing something wrong here? I'm a total beginner to this so this will probably be a stupid question.


Thank you for the help

---

### Post by Lambert on 2006-01-10
No stupid questions and welcome to Ubuntu.

Running the command as it is, you have to make sure you're in the same directory as the file is in. So if you downloaded it to a directory called downloads in your home folder you need to move to that directory like this.

```
cd /home/fragma/downloads
```

the command cd means change directory and the following is the path of the directory you want to change to.

See this thread for some good beginner command line help
[http://www.ubuntuforums.org/showthread.php?t=73885](http://www.ubuntuforums.org/showthread.php?t=73885)

---

### Post by Fragma on 2006-01-10
[QUOTE=Lambert]No stupid questions and welcome to Ubuntu.

Running the command as it is, you have to make sure you're in the same directory as the file is in. So if you downloaded it to a directory called downloads in your home folder you need to move to that directory like this.

```
cd /home/fragma/downloads
```

the command cd means change directory and the following is the path of the directory you want to change to.

See this thread for some good beginner command line help
[http://www.ubuntuforums.org/showthread.php?t=73885](http://www.ubuntuforums.org/showthread.php?t=73885)[/QUOTE]

Thank you for the reply.

I downloaded the file to the "desktop", I don't what it's referred to in linux. How will I change the directory to it? 



That link will definitely help me, I appreciate it! 

Allan

---

### Post by paulmilliken on 2006-01-11
[QUOTE=Fragma]Thank you for the reply.

I downloaded the file to the "desktop", I don't what it's referred to in linux. How will I change the directory to it? 



That link will definitely help me, I appreciate it! 

Allan[/QUOTE]

Firstly, open a terminal and type "pwd" to find the current working directory.
If your current directory is "/home/username" then type "cd Desktop" to change to "/home/username/Desktop"
Then type "ls" to see a list of files in that directory.

For more information on the cd command type "man cd".

---

### Post by Sef on 2006-01-11
> Originally Posted by Fragma
Thank you for the reply.

I downloaded the file to the "desktop", I don't what it's referred to in linux. How will I change the directory to it? 



That link will definitely help me, I appreciate it! 

Allan

You can also just type this:  cd /home/username/Desktop

---

