---
title: "[SOLVED] How do I modify a launch command to always execute with sudo?"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by crunchfighter on 2008-01-03
Hi,
I am trying to execute my brokers platform (thinkorswim).  I can install it fine.  It ran fine until they pushed an update.  Now it just hangs while it tries to update itself.  One theory on a similar post is that the update requires 'sudo' privileges.

How do I modify the launch command so that it automatically launches with the sudo command and accepts their frequent updates?

I tried doing it by right click->properties->launcher and typing sudo at the front of the command line, but it is never there after I close it out and look again.  It appears that I do not have the privilege to alter the command.

Any help would be appreciated.

Thanks.

---

### Post by p_quarles on 2008-01-03
If this is a graphical program (I'm assuming it is), you should use "gksudo" rather than "sudo."

What happens if you type this in the terminal?:
```
gksudo thinkorswim &
```

---

### Post by pointone on 2008-01-03
You'll need to use gksudo instead of sudo if you're using a launcher from the applications menu or desktop.

Another option would be to set the SUID bit of the executable to run as root, although this is somewhat insecure.

---

### Post by Ertai87 on 2008-01-03
One way to do it is to write a bash script to do it.  The bash script should look something like this:

#!/bin/sh/
sudo [command]

then chmod +x that file and put it in your classpath (/usr/bin I think, although you can modify your classpath in your bashrc file to make it point to wherever, although if you do that, make sure to append to it, not overwrite it, otherwise you won't be able to do basic commands like ls and stuff anymore).

Alternately, you can add your user accounts to the list of superusers, but that's inadviseable because if you ever get hacked the hacker will have sudo access to your computer without needing the sudo password.

---

### Post by crunchfighter on 2008-01-03
gksudo worked like a champ!  

So how do I make it so that when I click my icon on the panel, it does it automatically?

---

### Post by p_quarles on 2008-01-03
Try creating a *new *launcher (desktop or panel) and typing in the gksudo command. Do you have the same issue? (i.e., does "gksudo" disappear after saving it?)

---

### Post by crunchfighter on 2008-01-03
> **pointone said:**
> 
Another option would be to set the SUID bit of the executable to run as root, although this is somewhat insecure.

Can you walk me through this?  What do you mean by insecure?

---

### Post by crunchfighter on 2008-01-03
> **p_quarles said:**
> Try creating a *new *launcher (desktop or panel) and typing in the gksudo command. Do you have the same issue? (i.e., does "gksudo" disappear after saving it?)


p_quarles you did it!  That was much easier than I thought it would be and as easy as it should be.

Just to clear the air then, two questions:
1.  When do you use gksudo vice sudo
2.  How do i mark this thread as solved?

---

### Post by g2g591 on 2008-01-03
as in any user running it would be running it as root, if the application had some vernability such that arbitrary code could be exectuted, that code would be able to access all of your files, and/or anihilate your system. if you don't use it in the terminal, use gksu ,to mark the thread as solved, use thread tools at the top of the page

---

### Post by p_quarles on 2008-01-03
> **crunchfighter said:**
> Just to clear the air then, two questions:
1.  When do you use gksudo vice sudo
This should explain things:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
> 2.  How do i mark this thread as solved?
Top of the thread, click on "thread tools," and you'll see the option to mark it as solved.

---

