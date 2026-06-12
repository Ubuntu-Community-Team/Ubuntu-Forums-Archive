---
title: "Lost sudo and Synaptic"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by lakelovers on 2007-09-18
I have searched this problem but have been unable to solve it. I have edited visudo and nano /etc/group files following instruction on http;//www.psychocats.net/ubuntu. I cannot access any program/file requiring a password except for loggning onto Gnome. Just prior to losing sudo and Synaptic, I installed java through Synaptic, and I tried to enable Java Scripts (unsuccessfully). I need lots of help on this one.

**Edit: I forgot to say that I'm running Feisty**

---

### Post by alienexplorers on 2007-09-18
Please post your sudoers file using:

> sudo cat /etc/sudoers

---

### Post by lakelovers on 2007-09-19
How do I copy sudoers? I can't sudo and I've tried "cp" but I get a "permission denied." When I "sudo cat /etc/sudoers," I get "sudo: must be setuid root." I don't know how to get a copy from visudoers in the recovery terminal.

---

### Post by splintercellguy on 2007-09-19
Did you do any mass permission changes as root recently? That may have been the cause.

---

### Post by lakelovers on 2007-09-19
I may have. I recall doing a "chmod. . . .?" in my attempt to enable Java. If so, what's my next action? Thank you for answering my post

---

### Post by OffAxis on 2007-09-19
If you screwed up your ownership system wide then give this a try...

reboot into safe mode (boot off the disc and choose 'Repair' to get a root shell)

Then 

[B]chown root:root /usr/bin/sudo
chmod u+s /usr/bin/sudo
reboot
[/B]

chown = change ownership
root:root = individual : group
/usr/bin/sudo = the sudo command binary

chmod = change mode (how the file operates, what it can modify, etc)
u = user who owns the file (in this case, root)
s = set user (in this case we've changed the user to root, so the file will execute as root)

How's your networking? Do you still have internet access?

---

### Post by lakelovers on 2007-09-19
I couldn't get the second command to work. u+s. u. s. all returned "invalid user." I didn't try using "chmod /usr/bin/sudo without the u+s." Should I have used "-u -s?" Guess I'll try that.

I still do have access to the internet. Everthing seems to work unless a root password is required (e.g. Synaptic).

---

### Post by OffAxis on 2007-09-19
what does
**ls -l /usr/bin/sudo**

give you?

(and for the sake of clarity, that's an LS -L )

And does it come up highlighted in Red?

---

### Post by alienexplorers on 2007-09-19
If the sudoers file is not read only then you will not be able to run the sudo command.  You must use chmod to make /etc/sudoers read only.

---

### Post by lakelovers on 2007-09-19
OffAxis and all, Thank you, thank you all. . .** my sudoer is now working**. I inadvertently used "chown" instead of "chmod" in the second command. And OffAxis, I really appreciate your explanations of the commands. That helps a lot.

The bold type command: "ls -l. . . ."   did not come up in red.

---

### Post by OffAxis on 2007-09-19
you're welcome.

I'm glad to hear it's working again.

(and sorry about the red question; it's a function of the terminal program that I'm using to indicate mode status, I think (if someone out there could elaborate or point me to a definitions file I'd appreciate it). I usually use KDE, so it wouldn't necessarily be the same in the gnome terminals. if you run a
**ls -l /usr/bin** 
command you should notice a few files (sudo, fileshareset, for instance) that are colored or highlighted differently than the others.)

---

