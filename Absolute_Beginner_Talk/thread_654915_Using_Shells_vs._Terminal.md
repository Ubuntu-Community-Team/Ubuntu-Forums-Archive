---
title: "Using Shells vs. Terminal"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Mitchlb on 2007-12-31
How do you open the bash shell in ubuntu 7.10 or... Is does the terminal function like a shell. I've used linux before, but not ubuntu, so i'm a bit lost.

---

### Post by Vadi on 2007-12-31
I think the terminal is the shell.

---

### Post by Dr Small on 2007-12-31
If you open the terminal and type:
```
echo $SHELL
```

You'll see that the shell is /bin/bash

---

### Post by PeterJS on 2007-12-31
What the gnome-terminal program does is give you access to one of the pts virtual terminals, which emulate one of the physical consoles. On that virtual terminal you can run any shell you want, ubuntu defaults to bash.

What jeffus_il said, that's what I was trying to go for, but his version was more informative and complete.

---

### Post by jeffus_il on 2007-12-31
The terminal program gives you a window to run the shell in, the shell gives you the dollar prompt and waits for input, could be internal shell commands or external commands/programs. The shell could be one of many programs "sh" or shell "csh" or c shell "tcsh" "bash" and more.

The console also runs a shell (ctrl-alt-f1 etc), here a window such as xterm or gnome-terminal is not needed because the screen is only text. 

Once upon a time there were things called terminals or "dumb terminals" which had no cpu, mostly a keyboard and monitor, which were wired to a mainframe (what's that??) and talked to the mainframe directly, I think the big banks still use them for their transaction processing capabilities. Anyway that's getting a little off the subject ...

---

### Post by Mitchlb on 2007-12-31
Then how do you switch between shells? Say i'm using bash and i want to switch to c for a bit. Is there a code i can use in the current shell to switch to the next?

---

### Post by taurus on 2007-12-31
```
/bin/csh
```
Assuming you have csh installed.  When you are done, just type 

```
exit
```
to get back to your /bin/bash.

---

### Post by jeffus_il on 2008-01-01
In system->administration->Users and Groups
you can choose the advanced tab and choose a default shell for a user.

You could do the same by editing /etc/passwd

sudo nano /etc/passwd

and change the field containing "/bin/bash" to your preferred shell.
(on the line of your user, of course)

---

### Post by taurus on 2008-01-01
> **jeffus_il said:**
> In system->administration->Users and Groups
you can choose the advanced tab and choose a default shell for a user.

You could do the same by editing /etc/passwd

sudo nano /etc/passwd

and change the field containing "/bin/bash" to your preferred shell.
(on the line of your user, of course)

If you want to change shell permanently, no need to edit anything.  Just run

```
chsh
```
and the next time you log in, you are using the new one.

---

### Post by Mitchlb on 2008-01-02
Thanks a lot. Its been really helpfull. And mr. "i got my beans on ebay".... What's the point of beans anyways? Why would you need that many? Just out of curiousity.

---

