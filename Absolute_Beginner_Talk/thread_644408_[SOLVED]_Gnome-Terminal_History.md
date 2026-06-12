---
title: "[SOLVED] Gnome-Terminal History"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by GrandpaLeaman on 2007-12-18
I've run into a real head scratcher, and I have not been able to find the solution by myself.

When I first installed Ubuntu I was running Feisty. By default the terminal was set up already to view previous command line history. This was a great time saver and I loved it!

A few weeks ago I completely removed Vista from my machine and did a clean install of Gutsy. Everything went smoothly, but when I started running commands through the terminal, it would not save the history. I tried Googling for the fix, but was not able to find a step-by-step "how to" in order to get the history running again. I hope that someone can help me with this. But please, take it slow and give me all the details as I am old and sometimes don't understand very well.

---

### Post by Dr Small on 2007-12-18
Hmm... Have you tried pressing the "up" arrow key, to view the previous command ?

---

### Post by wormser on 2007-12-18
Do you have a file in your home directory called .bash_history?  What happens when you type the command **history** into the shell?

---

### Post by ctyc on 2007-12-18
what happens when you type cat .bash_history

As you may guess from the name of the file, it should contain your shell history.

---

### Post by GrandpaLeaman on 2007-12-19
Yes, and using the up arrow works when I'm in a terminal session. But when I close the terminal, all the history is erased. So the next time I open a terminal session, there is no history.

---

### Post by GrandpaLeaman on 2007-12-19
> **wormser said:**
> Do you have a file in your home directory called .bash_history?  What happens when you type the command **history** into the shell?
Yes, I do have this file in my home directory. Running "history" returns the message '1 history'.

---

### Post by GrandpaLeaman on 2007-12-19
> **ctyc said:**
> what happens when you type cat .bash_history

As you may guess from the name of the file, it should contain your shell history.
When I type in cat .bash_history as root, I get the following:

echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
exit
echo ndiswrapper >> /etc/modules
exit

This must be history from when I first installed Gutsy and set up my wireless card. Wild! Something must have broke after that.

---

### Post by legend2440 on 2007-12-19
Grandpaleaman

This page may help you

[http://richbradshaw.wordpress.com/2007/11/25/bash-tips-and-tricks/](http://richbradshaw.wordpress.com/2007/11/25/bash-tips-and-tricks/)

---

### Post by seventhc on 2007-12-19
Not to hijack this thread or anything but is there a way to set how much history is in the history?? it seems to be 500 by default. I would like to set that higher.
If anyone knows how I'd appreciate it. :)

would it be something like
set history = <value>?

and is there a limit to what the value can be?

---

### Post by legend2440 on 2007-12-19
Seventhc this page may help

[https://wiki.ubuntu.com/Spec/EnhancedBash](https://wiki.ubuntu.com/Spec/EnhancedBash)

echo "export HISTSIZE=1000" >> ~/.bashrc
echo "export HISTFILESIZE=1000" >> ~/.bashrc

---

### Post by GrandpaLeaman on 2007-12-19
I wish I could say this worked, but it didn't.  I added these two lines to .bashrc:

shopt -s histappend
PROMPT_COMMAND='history -a'

I then saved the file, restarted the computer and ran a terminal session using 'sudo apt-get update' and 'sudo apt-get upgrade' in order to get some history going. While still in the session I hit the up arrow and down arrow keys and everything seems to be working fine. I then close the terminal and reopen it. I hit the up arrow and...NOTHING! For some reason it doesn't want to append past history to the file. Funny thing is, this is the only problem I have had with my Gutsy install.

Truth be told, I can live without this great time saver. But I really would like to have it back. So if anybody has any ideas, please let me know.

---

### Post by seventhc on 2007-12-19
worked for me, what command are you trying?
oh wait.....

---

### Post by wormser on 2007-12-19
It is a shot in the dark, but you did ask for any ideas.  Check the permissions of .bash_history.  My other idea is to create a new user and see if the problem exists there too.  If it does then the problem would be with a global file.

---

### Post by legend2440 on 2007-12-19
Maybe this will help

[http://briancarper.net/2007/09/14/keeping-bash-history-in-sync-on-disk-and-between-multiple-terminals/](http://briancarper.net/2007/09/14/keeping-bash-history-in-sync-on-disk-and-between-multiple-terminals/)

---

### Post by GrandpaLeaman on 2007-12-20
> **wormser said:**
> It is a shot in the dark, but you did ask for any ideas.  Check the permissions of .bash_history.  My other idea is to create a new user and see if the problem exists there too.  If it does then the problem would be with a global file.
I show the owner of .bash_history is root. Shouldn't I be the owner of this file since it is in my home directory?

If you think this is the problem, how can I correct it?

---

### Post by legend2440 on 2007-12-20
Yes nothing in the home directory needs to be root unless of course you are logging in as root (not a good idea for security reasons) then of course everything will have root permissions. Hope I didn't confuse you. Anyway substitute "your user name" for whatever your personal user name is.

sudo chown  your user name ~ /.bash_history

sudo chgrp your user name ~/.bash_history

After these two commands go to your home directory and right click .bash_history then properties then the permissions tab and make sure read and write boxes are clicked. At this time you can also verify that your name is in the owner and group fields of the permissions box

The two commands above will change the owner and group permissions from root to your personal user name
Hope that helps. It should. Without user permissions you couldn't write to the file

---

### Post by GrandpaLeaman on 2007-12-20
> **legend2440 said:**
> Yes nothing in the home directory needs to be root unless of course you are logging in as root (not a good idea for security reasons) then of course everything will have root permissions. Hope I didn't confuse you. Anyway substitute "your user name" for whatever your personal user name is.

sudo chown  your user name ~ /.bash_history

sudo chgrp your user name ~/.bash_history

After these two commands go to your home directory and right click .bash_history then properties then the permissions tab and make sure read and write boxes are clicked. At this time you can also verify that your name is in the owner and group fields of the permissions box

The two commands above will change the owner and group permissions from root to your personal user name
Hope that helps. It should. Without user permissions you couldn't write to the file
That did the trick!!! It looks like I have everything running OK now, except for wine. But that is another story for another thread.

Thanks for the help legend2440 and wormser! If it wasn't for you two I would NEVER have gotten that right.

Well, it looks like I can mark this as resolved!

---

### Post by mdsmedia on 2007-12-20
> **GrandpaLeaman said:**
> That did the trick!!! It looks like I have everything running OK now, except for wine. But that is another story for another thread.

Thanks for the help legend2440 and wormser! If it wasn't for you two I would NEVER have gotten that right.

Well, it looks like I can mark this as resolved!I've learned something here too. Thanks for a valuable primer.

---

