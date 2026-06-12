---
title: "Can't login to main account"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by nhandler on 2007-02-07
"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem."

I get that error when I try and log into my main account. I can still log in to a second account I have set up. How can I fix this error. I've tried going to TTY1 and removing the .ICEauthority file. I have 1.6 gb free. Shouldn't that be enough to create the login tmp files? And if I'm able to log into my secondary account, shouldn't I be able to get into my primary account? How can I fix this problem?

---

### Post by lhtown on 2007-02-07
The problem could indeed be just what the error message said. I think I had something like that happen once when a sound capturing program went awry and ate up all of my disk space.

I am wondering if you may be able to log into the second account because it is on a different partition. It wouldn't matter if you have extra space on the disk if all of the affected partition is used up.

---

### Post by nhandler on 2007-02-07
> **lhtown said:**
> The problem could indeed be just what the error message said. I think I had something like that happen once when a sound capturing program went awry and ate up all of my disk space.

I am wondering if you may be able to log into the second account because it is on a different partition. It wouldn't matter if you have extra space on the disk if all of the affected partition is used up.

The second account is on the same partition. Could editing the .bashrc file cause this?

---

### Post by nhandler on 2007-02-08
If we can't fix it, is there any way to transfer everything to the second account so that it is identical to the first?

---

### Post by steve.horsley on 2007-02-08
You may need to boot into recovery mode to get access to the original home directory unless your second user is also a member of the admin group, in which case he can use **gksu nautilus** to get a full-rights file manager window.

You could try renaming .gnome and .gnome2 (and .bashrc) to see if the problem lies in one of those. Or drag all the user data somewhere else and delete everyting (including hidden files/folders) in the user's home directory. 

I once had a problem like this that was caused by a gnome config file for the user in /tmp, would you believe? Yes, Gnome also hides usesr config files in /tmp.

Another solution might be to install and launch KDE instead on gnome - it depends on what is crashing X.

A useful approach might be to Ctrl-Alt-F2 and log in (as the first user) on a text terminal and use the command **startx** from there. This may give some useful error messages as to why X is crashing.

---

### Post by nhandler on 2007-02-08
When I log into one of the Ctrl+Alt+Fx terminals as my main account, I get this message:

No directory, logging in with HOME=/

It then tells me how to run a root command using sudo.

If I then try and run startx. I then remove the lock file with sudo rm /tmp/.X0-lock

Next, I ran startx again. It looks like it starts to start, but then it sends me back to the terminal.

Renaming .gnome and .gnome2 didn't do anything either.

---

### Post by nhandler on 2007-02-08
Something else I've noticed is that my sound isn't working anymore.

---

### Post by shareMenaPeace on 2007-02-08
What do you get when you type 

```
df -h
```

Do you have space left?

---

### Post by nhandler on 2007-02-08
> **shareMenaPeace said:**
> What do you get when you type 

```
df -h
```

Do you have space left?

I have 1.7GB available. Shouldn't that be enough? Or should I free up more space?

---

### Post by shareMenaPeace on 2007-02-08
No that is ok than ..

---

### Post by nhandler on 2007-02-08
Is there a way to restore the .bashrc file to defaults? I modified it before I got this problem to add an alias to it. If I remember correctly, one error message mentioned that file.

---

### Post by steve.horsley on 2007-02-09
You can rename .bashrc for now and see if that fixes things. If so, create a new user and copy his.

> No directory, logging in with HOME=/
That's all wrong. Do you see your home directory when you say 
**ls /home**
? If not, I wonder where it went. Replace cheater with your user name in these commands:
[B]sudo mkdir /home/cheater
sudo chown cheater:cheater /home/cheater[/B]

You can check where your home directry should be (set as you log in) with this command:
**grep cheater /etc/passwd**
and your home directory is the last field.

---

### Post by nhandler on 2007-02-09
Renaming .bashrc did nothing. I know my folder is still there, because I can cd to /home/cheater and access all the files.

---

### Post by steve.horsley on 2007-02-10
What is your home folder set to in /etc/passwd?
**grep cheater /etc/passwd**
and your home directory is the last field.
This is the file you edit to change the home directory you get placed in when you log in.

---

### Post by nhandler on 2007-02-10
My home directory is the second to last field and says /home/cheater. The last field says /bin/bash.

---

### Post by steve.horsley on 2007-02-11
My mistake. The startup shell is indeed the last field. This looks OK then. 

I don't know what's wrong with the home setup then. I attach a copy of a clean .bashrc from my system for you. I called it bashrc.txt.

If you log in a B&W console, the command **env** should list all your environment variables, including your supposed home path. **echo $HOME** should also tell you your environment home setting, without all the other cruft.

From the B&W console, **startx** should start the x server, and any error messages you see may prove helpful.

---

