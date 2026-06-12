---
title: "[SOLVED] Problem With Ximian Evolution"
date: 2007-12-05
forum: Apple PPC Users
---

### Post by tgs1952 on 2007-12-05
Been using Evolution since installing Ubuntu. However, an email from my local public television station has completely frozen the application. I can't delete it - the program is completely locked.

Searching the internet I found the suggestion to open the gconf-editor and deselecting 'preview' for Evolution.

Didn't work. Application is still jammed.

Is there any way to delete messages from the command line?

Any other suggestions?

Thanks in advance for any help.

---

### Post by stmiller on 2007-12-06
You can kill evolution as a process if it is getting stuck. Fire up a terminal and type
```

ps ax

```
and look for something that looks like:
```

10470 ?        Sl     0:02 evolution --component=mail

```
Make note of the process ID number on the left hand side. Then kill that process by issuing the command
```

kill *number*

```
So that above one (for a random example) would be
```

kill 10470

```

---

### Post by tgs1952 on 2007-12-06
Thanks for the reply.

Killing the process did not work.

Whenever I open evolution, the same offending email is selected and the application is completely unresponsive - absolutely locked.

I must say, for a 'mature' open source email client to be rendered useless because of one non-malicious email is unbelievable.

---

### Post by tgs1952 on 2007-12-06
I was able to resolve the issue by using the gconf-editor from the command line.

at the prompt: gconf-editor

choose apps, evolution, mail and deselect preview

---

### Post by gmos on 2007-12-08
Great ! 

Thanks for that solution. 

My sister's email (evolution) had frozen in much the same way. Thanks to your solution it was finally fixed (after a lot of previous searching, reinstalling, etc), and the offending email message deleted.

Good thinking (I'd never thought of using Configuration Editor:  gconf can be added to menu using menu editor,,  Applications > System Tools > Configuration Editor)

---

