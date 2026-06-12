---
title: "Setting the Command Prompt?"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by MOGuy78 on 2008-03-18
I'm fairly new at using Ubuntu, and I'm just beginning to try out the terminal.  Now I've used Microsoft
for many years (since way back when it was only DOS 5), and I was trying to figure out if there was
a way to set up a different prompt.  Is there a list of the different characters you can use, and where
can I configure it?  I know in DOS you would use the config or autoexec files, is there an equivalent
for Linux?

Another question that goes along with this, are there any editors used for the terminal, and if so,
which are most commonly used?

---

### Post by wolfen69 on 2008-03-18
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by PointyWombat on 2008-03-18
```
man bash
```

and look for PROMPTING

You can add the PS variables into your .profile file (create new if necessary) and make the prompt whatever you need.

As for cli editors. Learn vi. 

Hope this helps.

---

### Post by cm.squared on 2008-03-18
Regarding text editors for the command line, probably the most commonly used are vim, emacs and nano.  Vim and emacs are full fledged, feature rich editors that require some investment in learning all of the commands and shortcuts, so most people use one or the other (and argue endlessly over which one is better).  Nano is simpler and is more for the person who only needs to edit a text file every once in a while.  Its probably worth it to know vim or emacs if you're going to spend any significant amount of time using the command line.

Some time ago I resolved to learn vim and emacs to see what the big deal was about, and after fooling around with them both I was just taken with vim and have never looked back.  There is a great tutorial for it [here]("http://www.apmaths.uwo.ca/~xli/vim/vim_tutorial.html").

Also, I agree with wolfen.  Linuxcommand.org has a wonderful tutorial for the bash shell (command line).

---

