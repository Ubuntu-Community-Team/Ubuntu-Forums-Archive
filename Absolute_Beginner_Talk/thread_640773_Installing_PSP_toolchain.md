---
title: "Installing PSP toolchain"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by Jet8225 on 2007-12-14
I've been having some problems when installing this the PSP toolchain so I'll copy the steps I did here just in case I commited an error before the part I'm having trouble with. 

```
jesus@jesus-laptop:~$ cd /home/jesus/Desktop/psptoolchain
jesus@jesus-laptop:~/Desktop/psptoolchain$ ./toolchain.sh
ERROR: Set $PSPDEV before continuing.
../depends/check-pspdev.sh: Failed.
jesus@jesus-laptop:~/Desktop/psptoolchain$ export PSPDEV=/usr/local/pspdev
jesus@jesus-laptop:~/Desktop/psptoolchain$ export PATH=$PATH:$PSPDEV/bin
jesus@jesus-laptop:~/Desktop/psptoolchain$ ./toolchain.sh
touch: cannot touch `/usr/local/pspdev/test.tmp': Permission denied
ERROR: Grant write permissions for /usr/local/pspdev before continuing.
../depends/check-pspdev.sh: Failed.

```

What does that last part mean?

---

### Post by llamakc on 2007-12-14
Run it with "sudo" or change the permissions of /usr/local/pspdev so your user may access & use it.

---

### Post by Jet8225 on 2007-12-14
How can I change the permision of /usr/local/pspdev? I haven't created any file with that name, and when I run it with sudo I get this :

```
ERROR: Add /usr/local/pspdev/bin to your path before continuing.
../depends/check-pspdev.sh: Failed.
```

---

### Post by llamakc on 2007-12-14
You may have to export the variables again, and possibly into root's environment.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) for learning about permissions.

Read that and if you have questions, post back.

---

### Post by Jet8225 on 2007-12-14
what about the output I got when I used sudo?

---

### Post by Jet8225 on 2007-12-14
anyone?

---

### Post by llamakc on 2007-12-14
EDIT: I missed your comment.

1.) DO not bump threads that are 20 minutes old. If nobody helps by tomorrow, bump then. If you need immediate help check IRC first.

2.) I explained that you may need to set the variables again. Have you tried setting them with sudo, and then re-running the command?

---

### Post by Jet8225 on 2007-12-14
I'm a complete newbie so I hardly understand what you are saying. If by variables you mean the r x w that appear in the article link you gave me, then no. If those aren't the variables then i don't know what you are talking about.

---

### Post by llamakc on 2007-12-14
Let's take this from a newbie approach then.

Why are you building psptoolchain? And from where did you get it?

```

jesus@jesus-laptop:~/Desktop/psptoolchain$ export PSPDEV=/usr/local/pspdev
jesus@jesus-laptop:~/Desktop/psptoolchain$ export PATH=$PATH:$PSPDEV/bin
```

Are the variables that YOU set, not anything that I recommended.

Since you're new, it will  help others help you if you include a link to what you're trying to do. Often, there are easier alternatives already available as an Ubuntu download in Synaptic (or apt-get).

---

### Post by Jet8225 on 2007-12-14
I'm building a psptoolchain to create homebrew for PSP using C++ programming language (which I still need to learn). I got it from here:
 [http://www.psp-programming.com/tutorials/c/lesson01.htm](http://www.psp-programming.com/tutorials/c/lesson01.htm).
It's supposed to go with Cygwin, which is a Linux emulator for Windows, but since I'm already running Linux they advised me just to install the toolchain. 

I set up those variables because the toolchain came with a read me file that showed the steps to install it and it's said to set those variables.

---

### Post by llamakc on 2007-12-14
> **Jet8225 said:**
> I'm building a psptoolchain to create homebrew for PSP using C++ programming language (which I still need to learn). I got it from here:
 [http://www.psp-programming.com/tutorials/c/lesson01.htm](http://www.psp-programming.com/tutorials/c/lesson01.htm).
It's supposed to go with Cygwin, which is a Linux emulator for Windows, but since I'm already running Linux they advised me just to install the toolchain. 

I set up those variables because the toolchain came with a read me file that showed the steps to install it and it's said to set those variables.

Become root with `sudo -i`

Then start over @ 

```

export PSPDEV=/usr/local/pspdev
export PATH=$PATH:$PSPDEV/bin

jesus@jesus-laptop:~/Desktop/psptoolchain$ ./toolchain.sh

```

And you most certainly will need to learn about permissions, which would have solved this issue also for you.

---

### Post by Jet8225 on 2007-12-14
I tried an alternative way, instead of using ./toolchain.sh I used ./toolchain-sudo.sh which was another script that came with the file, and now it's working pretty well. Well, actually it's  setting up the environment which the tutorials I'm reading say that it's going to take  a while. Well, it finished but I don't think it worked... I'll try that other way you suggested. I did it that way and it's working for now. It didn't work but I'll try it later because I gotta go now. Thanks for all your help.

---

