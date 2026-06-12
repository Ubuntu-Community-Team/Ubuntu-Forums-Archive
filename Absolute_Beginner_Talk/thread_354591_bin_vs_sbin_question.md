---
title: "/bin vs /sbin question"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by InTheFlow on 2007-02-06
Hello.

What is the difference between the important binaries of the /bin folder and the important system binaries of the /sbin folder?

And another question...those of you who reply to us with "here, type this code in a console window", how did you get to where you knew that stuff?  I'd like to be able to do the same thing. :) 

So far I'm starting by reading the Ubuntu documentation. Is this how y'all learned or is there another good way?

Thanks.

---

### Post by mizar001 on 2007-02-06
In the standard literature 
bin:Commands needed during bootup that might be needed by normal users
sbin:Like bin but commands are not intended for normal users.  Commands run by LINUX.

If you want to know more simply google "linux directory structure" and you'll find a lot of infos.

The commands used in ubuntu are often similar (if not equal) to other distros. Who know how linux works and its main commands, are able to manage an ubuntu distro as well. Buy a linux manual to know everything about linux mechanisms and philosophy. When yoy read that i assure that ubuntu is the easier linux system, but also one of the most powerful.

Though you ca be well aquainted with windows systems, with linux you must know this command line thing, and i think that ubuntu documentation can really help you.

For example you can read this :
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html)

But for more terminal commands you can refer to any linux documentation.

---

### Post by poohbear1616 on 2007-02-06
Try this site below. I am reading on the site myself and have learned alot.

[http://www.linuxcommand.org/]("http://www.linuxcommand.org/")

---

### Post by Jussi Kukkonen on 2007-02-06
> 
What is the difference between the important binaries of the /bin folder and the important system binaries of the /sbin folder?
The S is for "system" -- sbin contains stuff that will not be run by normal users, just system administrators. And before you ask: the difference between /usr/bin and /bin (also /usr/sbin and /sbin) is supposed to be that stuff in /bin may be used during system startup.

> how did you get to where you knew that stuff? I'd like to be able to do the same thing.
One command at a time, young Padawan, one command at a time...

---

### Post by InTheFlow on 2007-02-06
Thanks for the help everyone!

> **Jussi Kukkonen said:**
> One command at a time, young Padawan, one command at a time...

:lolflag:

---

### Post by Brunellus on 2007-02-06
rule of thumb:  if it's not in /home you shouldn't be messing with it without knowing what you're doing.

As to how I learned the shell:  I had a book ("How Linux Works" by Brian Ward) and read that on the train to & from work.  Then, I'd try things out.  

Most commands have manual pages attached to them.  If you can learn how the man page flows, then you can glean a lot of information from it.  so for 'tar' you'd go

man tar

also, I have to give a shout out to the guys in the ubuntu community and especially #ubuntuforums for helping me learn how to do neat things with the shell.

---

