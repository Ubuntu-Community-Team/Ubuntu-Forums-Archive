---
title: "I've tried and tried (Really) But no luck with Shell Script."
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by bmachia on 2008-02-23
Every time I logon, I need to start ndiswrapper so my wireless network becomes available.

This is a two part step.

First, from Konsole, I type 'sudo modprobe ndiswrapper'
as expected it returns asking for a password.

Second I need to start KNetworkManager.  After a few seconds I have network connectivity.  KNetworkManager is currently setup to start automatically upon logon.

In order to automate this for every logon, I created a shell script called netstart.sh and placed the script in: ~/.kde/Autostart.  I gave the script file 'executable' permission.  The file consisted of two lines.  They are;
#!/usr/bin/bash
sudo modprobe ndiswrapper

But nothing happens..?..??
So to troubleshoot, I tried to execute it from Terminal mode.  And even though I'm in the right directory and I can see the file (green in color) using a ls -l, Terminal mode responds with 'Can't find file'.

2 Questions
1)Can anyone explain what is happening, so I can fix it?
2)Whats is going to happen within the computer and .kde/Autostart when sudo needs a password. Isn't there anyway to do this smartly, without typing a password in ASCII text within a script?

Any different directions or thoughts would be greatly appreciated.

Bill

---

### Post by shad0w_walker on 2008-02-23
you can tell the ndiswrapper module to load at boot by putting the line

```
ndiswrapper
```

into the file /etc/modules

To access /etc/modules, press Alt-F2 and run this command

```
gksu gedit /etc/modules
```

When you have put in the line save and close the editor.

---

### Post by jordanmthomas on 2008-02-23
> **bmachia said:**
> 
So to troubleshoot, I tried to execute it from Terminal mode.  And even though I'm in the right directory and I can see the file (green in color) using a ls -l, Terminal mode responds with 'Can't find file'.

2 Questions
1)Can anyone explain what is happening, so I can fix it?
2)Whats is going to happen within the computer and .kde/Autostart when sudo needs a password. Isn't there anyway to do this smartly, without typing a password in ASCII text within a script?

Any different directions or thoughts would be greatly appreciated.

Bill

For the file not found problem, are you just typing
```
script.sh
```
?  If so, when you're in the Autostart directory you'll need to type
```
./script.sh
``` because "." is not in your PATH variable (and you don't really want it to be probably)

As for what will happen when it reaches the sudo, it will just sit there waiting for a response it's not going to get.  There are **several** ways you can fix this.
1.  Put ndiswrapper in /etc/modules
2.  Instead of using sudo in your script, use kdesu and it will give you a window and you'll need to type your password.
3.  Put modprobe ndiswrapper in /etc/rc.local

Probably the best solution is number 1.

---

### Post by bmachia on 2008-02-23
Thank both of you Very Much.  You have helped to teach the ignorant! 

I used the /etc/modules solution and it works Great!  1 less thing I need to do at startup.

Bill

---

### Post by shad0w_walker on 2008-02-23
Glad you got things working. Mind marking the thread as solved? In thread tools menu is memory serves.

---

