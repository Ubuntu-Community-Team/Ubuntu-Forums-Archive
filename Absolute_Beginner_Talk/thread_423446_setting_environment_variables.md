---
title: "setting environment variables?"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by michaelw436 on 2007-04-25
Hey guys, I am new to Ubuntu, and am an aspiring Oracle DBA. I am working on installing Oracle on Feisty Fawn according the instructions that I found out at dizwell.com. Everything is going well, except for setting the oracle environment variables in the oracle users .bashrc file. I added the export statements to that .bashrc file, but they don't seem to be working... any help? below is the tail of the .bashrc file, and then me trying to echo them out as the oracle user, and they don't seem to be working. Please help! Thanks!

ubuntu1@ubuntu1-pc:~$ tail /home/oracle/.bashrc
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
. /etc/bash_completion
fi

export ORACLE_BASE=/oracle
export ORACLE_HOME=/oracle/10g
export ORACLE_SID=orcl10
export PATH=$PATH:$ORACLE_HOME/bin

ubuntu1@ubuntu1-pc:~$ su - oracle
Password:
$ echo $ORACLE_BASE

$ echo $ORACLE_HOME

$ exit

---

### Post by jfinkels on 2007-04-25
You might have to log out and log back in again.

---

### Post by michaelw436 on 2007-04-25
I have tried, that doesn't work.

---

### Post by jfinkels on 2007-04-26
maybe you can try editing your ~/.profile or if that doesn't work, your ~/.bash_profile. Then log out and log in, and see if it works.

---

### Post by michaelw436 on 2007-04-26
I have tried all of those, I have tried ~/.bashrc, ~/.bash_profile, ~/.bash_login, ~/.profile, and all of the same files in the /etc/ directory! Still none of them work for the oracle user.

---

### Post by jfinkels on 2007-04-27
> **michaelw436 said:**
> I have tried all of those, I have tried ~/.bashrc, ~/.bash_profile, ~/.bash_login, ~/.profile, and all of the same files in the /etc/ directory! Still none of them work for the oracle user.

Hmm...On my own system, I have a ~/.profile file that looks something like this, and it works as advertised:
```

EDITOR=/usr/bin/emacs
export EDITOR

```
```

jeff@jeff-laptop:~$ echo $EDITOR
/usr/bin/emacs

```

However, I have found that the contents of .bash_profile are not executed correctly, as stated in this thread ( [http://ubuntuforums.org/showthread.php?t=384156](http://ubuntuforums.org/showthread.php?t=384156) ).

This obviously has no bearing on your situation, but I'm just providing as much information as I know :P.

One thing you may want to try is to make a small script that just exports whatever you need to export to the environment, then just add it to startup programs using "System > Preferences > Sessions". This is annoying because your .bashrc should work, but it may be necessary.

---

### Post by michaelw436 on 2007-04-27
Thanks Jeff, I will try that tonight. Thanks for the help with this!!

---

### Post by jfinkels on 2007-04-27
> **michaelw436 said:**
> Thanks Jeff, I will try that tonight. Thanks for the help with this!!

No problem! Let us know if it works.

Oh, I forgot to mention, you should probably test first to see if you actually are able to export a variable from the command line directly with a command like
```

export FOO=bar

```

Good luck.

---

### Post by michaelw436 on 2007-04-27
~/.profile worked! Thanks so much Jeff!

---

### Post by drega on 2007-04-27
you can also use the source command to accomplish the same thing source .bashrc 

check out the man page for source. 

Derek

---

