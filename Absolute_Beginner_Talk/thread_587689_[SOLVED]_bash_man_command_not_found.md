---
title: "[SOLVED] bash: man: command not found"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by bw44 on 2007-10-23
When I open a Terminal window and type  "man" followed by some command name
I get the message:

bash: man: command not found

I see suggestions everywhere about using man -- why do I get this message?

I looked in the Synaptic Package Manager, found, and installed the bash-doc
component.  It installed successfully and I thought this would solve the problem.
No such luck

Can anyone tell me what I need to do to get the man pages working? Sorry if the
solution is obvious, but I haven't been able to find a forum post that describes this
problem.


Thanks.

---

### Post by jon zendatta on 2007-10-23
as far as i know you enter the program then man for example 

file man

---

### Post by SomethinSnappy on 2007-10-23
> **bw44 said:**
> When I open a Terminal window and type  "man" followed by some command name
I get the message:

bash: man: command not found

I see suggestions everywhere about using man -- why do I get this message?

I looked in the Synaptic Package Manager, found, and installed the bash-doc
component.  It installed successfully and I thought this would solve the problem.
No such luck

Can anyone tell me what I need to do to get the man pages working? Sorry if the
solution is obvious, but I haven't been able to find a forum post that describes this
problem.


Thanks.

Try  sudo apt-get install man  in a terminal or "manpages" in Synaptic. Thats my guess at least. 

Let us know if it helps :)

---

### Post by Beggar on 2007-10-23
In order to install it you would run:

```
sudo apt-get install manpages
```

---

### Post by bw44 on 2007-10-23
> **jon zendatta said:**
> as far as i know you enter the program then man for example 

file man

Thanks for replying, Jon.

When I try your suggestion  I get the following:

bob@DELL2:~$ file man
man: ERROR: cannot open `man' (No such file or directory)

Maybe I didn't describe my original problem very clearly. When I enter

bob@DELL2:~$ man mv   (for example) the system responds with: 

bash: man: command not found

All the other commands I have tried seem to work fine: ls, cd, mv, and so on.

Any other thoughts?

---

### Post by bw44 on 2007-10-23
> **Beggar said:**
> In order to install it you would run:

```
sudo apt-get install manpages
```

I didn't know that it had to be installed, but doing so did not seem to solve the
problem.   I copied your code into my terminal command line and ran it. After
asking me to  insert the Feisty distribution CD it seemed to complete normally
(no error messages, anyway). I exited the terminal session and started a new
 one, but it still didn't work.

This is driving me nuts!  But thanks for trying!

---

### Post by Beggar on 2007-10-23
Can you post the exact output produced by this?

```

sudo apt-get install manpages
bash
ls /usr/bin/man
man rm

```

---

### Post by bw44 on 2007-10-23
> **SomethinSnappy said:**
> Try  sudo apt-get install man  in a terminal or "manpages" in Synaptic. Thats my guess at least. 

Let us know if it helps :)

That did it!  Your "guess" was spot on. Was it also necessary to do as Beggar suggested and
run the ```
 the $ sudo apt-get install manpages
```?

Thanks so much to everyone for your help.  I'll mark the problem solved.

---

### Post by bw44 on 2007-10-23
> **Beggar said:**
> Can you post the exact output produced by this?

```

sudo apt-get install manpages
bash
ls /usr/bin/man
man rm

```

I can't send you the original output when I first ran it.  Here is what the first command
produced when I re-ran it:

bob@DELL2:~$ sudo apt-get install manpages
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
manpages is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic linux-headers-2.6.20-15
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

The output from the other commands was:

bob@DELL2:~$ bash
bob@DELL2:~$ ls /usr/bin/man
/usr/bin/man
bob@DELL2:~$ man rm
Reformatting rm(1), please wait...
bob@DELL2:~$

Now, every time I enter $ man [command name] the manual pages are displayed OK
but I get the message:

bob@DELL2:~$ man [command]
Reformatting [command](1), please wait...
bob@DELL2:~$ 

It does this every time I enter the same command.  This doesn't look normal.
What is being reformatted and why?   Also, should I do as it says:

The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic linux-headers-2.6.20-15
Use 'apt-get autoremove' to remove them.

Thanks for continuing to  pursue this; I'm not quite there yet, but getting closer!:)

---

### Post by SjRaptor on 2007-10-23
> **bw44 said:**
>  the manual pages are displayed OK
but I get the message:

bob@DELL2:~$ man [command]
Reformatting [command](1), please wait...
bob@DELL2:~$ 

It does this every time I enter the same command.  This doesn't look normal.
What is being reformatted and why?   Also, should I do as it says:

The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic linux-headers-2.6.20-15
Use 'apt-get autoremove' to remove them.

Thanks for continuing to  pursue this; I'm not quite there yet, but getting closer!:)

That's completely normal for man to do that. What it's doing, is it's formatting the text to your display. You should be okay to `apt-get autoremove'

---

### Post by bigboy_pdb on 2007-10-23
> **jon zendatta said:**
> 
as far as i know you enter the program then man for example 
file man


No, it's "man *command*".

---

### Post by bw44 on 2007-10-23
> **SjRaptor said:**
> That's completely normal for man to do that. What it's doing, is it's formatting the text to your display. You should be okay to `apt-get autoremove'

Thanks very, very much (and to every one else who pitched in) -- what a great community!

I'll mark the problem  solved.  (But I'm curious why the man pages weren't installed by default in
7.04, since the Ubuntu Help facility said that $command --help  and $man command  were 
where to go for help with using commands.)

---

### Post by SomethinSnappy on 2007-10-23
> **bw44 said:**
> Thanks very, very much (and to every one else who pitched in) -- what a great community!

I'll mark the problem  solved.  (But I'm curious why the man pages weren't installed by default in
7.04, since the Ubuntu Help facility said that $command --help  and $man command  were 
where to go for help with using commands.)

I'm pretty sure it is supposed to auto install. I have no idea what could have gone sideways??? :-k 

Glad it's fixed though!

---

### Post by bw44 on 2007-10-23
> **SomethinSnappy said:**
> I'm pretty sure it is supposed to auto install. I have no idea what could have gone sideways??? :-k 

Glad it's fixed though!

So am I!  Maybe man did not install automatically because I installed Feisty from the "Alternate" CD.
I gather that the alternate is a somewhat trimmed down version for people who can't install from the
Desktop CD.  (Just a guess.)

---

### Post by elnur on 2008-05-20
I had the same problem. The problem was that link was broken:

```

$ ls -l /usr/bin/man
lrwxrwxrwx 1 root root 17 2008-03-19 01:32 /usr/bin/man -> h???ib/man-db/man

```

Don't know what caused it to be broken, but here is my solution:

```

$ sudo rm /usr/bin/man
$ sudo ln -s /usr/lib/man-db/man /usr/bin/man

```

Fixed! =)

---

