---
title: "watch tty"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by timon_tg on 2007-01-04
Hi,
Can anyone tell me if I am logged as root , how to check what commands are entered in other ttys?

---

### Post by Rhubarb on 2007-01-04
If you see a "#", you're logged in as root,
if you see a "$", you're not.

I'm not sure how to check what commands are entered in other ttys.
(Apart from going to those ttys, then pressing Shift + PgUp if there's a lot on screen).

Hope this helps.

---

### Post by timon_tg on 2007-01-04
I meen entered from other user logged on the system at the same time. I want to check what they are doing.

---

### Post by Rhubarb on 2007-01-05
Ignore this post, it was just me trying to guess the location of the bash history file.
Read the next post for the file's exact location

---

### Post by Rhubarb on 2007-01-05
Ok, good news,

The Bash history is located in:
/home/username/.bash_history

It's a regular text file that can be viewed with nano/vim/gedit/kate or whatever text editor you prefer.


Example: Say you want to see user **bruce**'s bash history.

If using gedit, open up a terminal and type in
```
gksu gedit /home/bruce/.bash_history
```

If using nano, in the terminal type in
```
sudo nano /home/bruce/.bash_history
```

---

### Post by Lord Illidan on 2007-01-05
> **Rhubarb said:**
> If you see a "#", you're logged in as root,
if you see a "$", you're not.


Or else, just type whoami at the console

---

### Post by timon_tg on 2007-01-05
OK , but you can check .bash_history file only after the other user logout, couse the user history will be saved in the file after the logout...so how to check the othe user command at the time that are entered?
10x

---

### Post by Rhubarb on 2007-01-05
Ok, now you're getting tricky :)
After doing some quick searching on the net (google is your friend here), I've only got half an answer for you.  I'm still new to linux here.

If you want to update your unsaved bash history to ~/.bash_history (so you don't have to log out / exit the terminal for it to write the file):
```
history -w
```

This is where you're on your own now.
You'll somehow need that command to be run every time the other user presses enter in the terminal, or use a cron job for that use to make it run every 10s or so.

Another method that should work:
ssh into that users account, then run "history -w", exit out of your ssh session, then you should be able to read the .bash_history file.

I suggest you bump this thread every now and then or do some serious googling to work it out your self.

Hope everything works out well for you ;)

---

### Post by Sasa_Ivanovic on 2007-01-05
you can view all the procesess other users are doing by doing
```

ps -el

```
where e is everyone
and l gives full descriptons including tty

then if you want specific user you can do this :
```

ps -el | grep xxx

```
where xxx is the tty of the user

---

### Post by Rhubarb on 2007-01-05
Ok, because I was bored ... and you gave me a nice challenge there, I've worked out how to do it :cool: 

In the user's ~/.bashrc file, add these two lines:
```
shopt -s histappend
PROMPT_COMMAND='history -a'
```

Now everytime that user enters something in, it gets instantly updated in that users .bash_history file

I found the info here, topic number 8: Rewriting History
[http://www.ukuug.org/events/linux2003/papers/bash_tips/](http://www.ukuug.org/events/linux2003/papers/bash_tips/)



The PROMPT_COMMAND entry there runs whatever follows, whenever BASH displays a prompt.
So if you insert firefox here, it will run firefox whenever the terminal is opened, and whenever a user has finised executing a command.  (yeah this is a bit of a silly example).
```
PROMPT_COMMAND='firefox'
```

---

### Post by madman91 on 2008-03-24
> **Rhubarb said:**
> Ok, because I was bored ... and you gave me a nice challenge there, I've worked out how to do it :cool: 

In the user's ~/.bashrc file, add these two lines:
```
shopt -s histappend
PROMPT_COMMAND='history -a'
```Now everytime that user enters something in, it gets instantly updated in that users .bash_history file

I found the info here, topic number 8: Rewriting History
[http://www.ukuug.org/events/linux2003/papers/bash_tips/](http://www.ukuug.org/events/linux2003/papers/bash_tips/)

SNIP-----


That is a good idea, except for the fact that the user could figure it out and remove that from his configuration file. 

I've heard of Snoopy. Its a user command logger, I'm not quite sure how it works.

[http://sourceforge.net/projects/snoopylogger/](http://sourceforge.net/projects/snoopylogger/)
Snoopy is designed to aid the task of a sysadmin by providing a log of commands executed. Snoopy is completely transparent to the user and applications. It is linked into programs to provide a wrapper around calls to execve(). Logging is done via syslogd

---

