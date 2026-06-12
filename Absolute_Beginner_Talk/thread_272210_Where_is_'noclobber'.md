---
title: "Where is 'noclobber'"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by Portable_Jim on 2006-10-05
I was reading through "The complete Idiot's guide to Linux" (based on Calderia Openlinux 1.3) when I was a command called 'noclobber'. I went to try it out using terminal, but it did not stop my file from being clobbered.
This is what I did:
```
james@jamescomputer:~/Desktop$ touch file1
james@jamescomputer:~/Desktop$ noclobber=1
james@jamescomputer:~/Desktop$ date > file1
james@jamescomputer:~/Desktop$ cat file1
Fri Oct  6 11:15:42 EST 2006
james@jamescomputer:~/Desktop$
```

Did I do anything wrong? or is there another command to do the same thing?

(I am using Dapper Drake)

---

### Post by mitch.c on 2006-10-05
> **Portable_Jim said:**
> I was reading through "The complete Idiot's guide to Linux" (based on Calderia Openlinux 1.3) when I was a command called 'noclobber'. I went to try it out using terminal, but it did not stop my file from being clobbered.
This is what I did:
```
james@jamescomputer:~/Desktop$ touch file1
james@jamescomputer:~/Desktop$ noclobber=1
james@jamescomputer:~/Desktop$ date > file1
james@jamescomputer:~/Desktop$ cat file1
Fri Oct  6 11:15:42 EST 2006
james@jamescomputer:~/Desktop$
```

Did I do anything wrong? or is there another command to do the same thing?

(I am using Dapper Drake)
Actually, the way to set noclobber is:
> # turn no clobber on
set -o noclobber
# turn no clobber off
set +o noclobber
Here's what the bash man page says:
> If set, bash does not overwrite an  existing  file  with the  >,  >&,  and <> redirection operators.  This may be overridden when creating output files by using the redirection operator >| instead of >.

Hope that helps.

---

### Post by szf on 2006-10-05
[FONT="Courier New"]
sean@host:~$ set -o | grep noclobber
noclobber       off
sean@host:~$ set -o noclobber
sean@host:~$ set -o | grep noclobber
noclobber       on
[/FONT]

---

### Post by bodhi.zazen on 2006-10-05
> **Portable_Jim said:**
> I was reading through "The complete Idiot's guide to Linux" (based on Calderia Openlinux 1.3) when I was a command called 'noclobber'. I went to try it out using terminal, but it did not stop my file from being clobbered.
This is what I did:
```
james@jamescomputer:~/Desktop$ touch file1
james@jamescomputer:~/Desktop$ noclobber=1
james@jamescomputer:~/Desktop$ date > file1
james@jamescomputer:~/Desktop$ cat file1
Fri Oct  6 11:15:42 EST 2006
james@jamescomputer:~/Desktop$
```

Did I do anything wrong? or is there another command to do the same thing?

(I am using Dapper Drake)

Just a thought:

Add noclobber to your .bashrc

A few others you may like:

```
gedit ~.bashrc
```

Add this:> #Set Prompt
PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# My alias
alias ls='ls --color=auto'
alias la='ls -a --color=auto'
alias ll='ls -la --color=auto'
alias mv='mv -i'
alias cp='cp -i'
alias rm='rm -i'
set -o noclobber

---

### Post by Portable_Jim on 2006-10-05
Thanks for the info. I ran:
```
james@jamescomputer:~/Desktop$ set -o noclobber yes
james@jamescomputer:~/Desktop$ set -o | grep noclobber
noclobber       on
james@jamescomputer:~/Desktop$ date > file1
bash: file1: cannot overwrite existing file
james@jamescomputer:~/Desktop$

```
 :KS :KS :KS :KS :KS :KS :KS :KS

---

### Post by sbergman27 on 2006-10-05
> Just a thought:

Add noclobber to your .bashrc

OK.  Sorry for the semi-off-topic post.  But I remember "noclobber" being a keyword in an unrelated context.  It was Linux related, but not bash related.  Could someone please give my brain a little kick?

Thanks,
Steve

---

### Post by bodhi.zazen on 2006-10-06
> **sbergman27 said:**
> OK.  Sorry for the semi-off-topic post.  But I remember "noclobber" being a keyword in an unrelated context.  It was Linux related, but not bash related.  Could someone please give my brain a little kick?

Thanks,
Steve

Not sure what you are asking.

Linux runs the bash shell by default. Bash is not unique to Linux.

If you set your prompt, set an alias, or clobber when you open a shell, it will hold for one session only.

~/.bashrc is a user config file for bash.
no clobber is an option for bash.
If you add "set -o noclobber", prompt settings, alias, etc to ~/.bashrc this will modify the default behavior for all bash shells for a user and be in effect each time that user (you) open a shell.

In terms of your question, no clobber is a bash option.

The relation to Linux is bash is the default Linux shell.

---

