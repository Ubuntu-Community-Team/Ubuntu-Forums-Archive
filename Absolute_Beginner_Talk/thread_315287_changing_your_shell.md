---
title: "changing your shell"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by bajetownrep on 2006-12-08
hello guys I was wondering if you could give me some assistance with the changing of my shell.

Currently the default is bash and I would like to change it to the c-shell to help complete this tutorial I am trying.(yes yes I know the c-shell isnt the best shell for scripting but this is what the tutorial uses :p )

I looked in the manpage for chsh( change shell) and was trying to change it using the -s flag as was suggested in the man page.

I also performed a cat on /etc/shells and the  /bin/csh shell was listed. 

However when I try the command does not seem to work. I also looked at this page

[http://www.faqs.org/faqs/unix-faq/shell/shell-differences/](http://www.faqs.org/faqs/unix-faq/shell/shell-differences/) and tried to follow the instruction there but with no success. 

I suspect I may be missing something simple and throw myself to the wolves in the hope that I may gain some knowledge.

---

### Post by taurus on 2006-12-08
Applications -> Accessories -> Terminal
```
chsh
```
You need to log out and back in again for the new change, /bin/csh, to be in effect.

---

### Post by bajetownrep on 2006-12-09
hmmm

dont i have to supply the -s option as well as the shell I want.

:-k 

and do you mean close the terminal or log off the machine completely?

---

### Post by taurus on 2006-12-09
It will ask you which shell you want to change to...  After changing to /bin/csh, log out completely (no need to reboot) and log back in and this time, you will be running /bin/csh instead of the default shell, /bin/bash.

---

### Post by PapaNerd on 2006-12-09
For an alternate shell to work, the executable file for that shell needs to exist.  On my system, when I run the following command:
  for SHELL in `cat /etc/shells`; do ls -l $SHELL; done
it shows me that not all the shells listed in /etc/shells actually exist, and some are symbolic links to bash.

Presuming a shell exists, and if you are running in a terminal window, not the GUI, then typing the path to the new shell on the command line will put you into that shell without affecting your login default.  When you are done, just type "exit" to return to the previous shell or close the terminal window.

---

### Post by bajetownrep on 2006-12-09
taurus when I did what you told me it asked me for a password and when i supplied it the /bin/csh shell it informed me that
/bin/csh was an invalid shell.

I did what PapaNerd suggested at the prompt and it informed me that /bin/csh  no such file or directory.

So it seems like PapaNErd says, that all of these shells do not actually exist.

So any other ideas, can you point me to a link with instructions on how to install one of these shells. The link I posted in my orignal post implied that this was not easily done.


thanks for any help in advance

---

### Post by PapaNerd on 2006-12-09
Go to: System > Administration > Synaptic Package Manager
Enter your password when prompted
Do a search on the word "shell"
Check whichever additional shells you like
Click on "Apply"

---

### Post by taurus on 2006-12-09
```
sudo aptitude update
sudo aptitude install csh
```

---

