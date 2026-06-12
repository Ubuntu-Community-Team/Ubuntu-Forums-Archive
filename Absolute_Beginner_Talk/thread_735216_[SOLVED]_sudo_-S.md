---
title: "[SOLVED] sudo -S"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by alejaaandro on 2008-03-25
I was trying to run a script with sudo... so I searched to sudo man and tried "sudo  -S (command)" and I can run the command as sudo ...later on, I searched the forum and found that I should do  "echo psswd | sudo -S command" (I know, there is a safer way, I just wanted to test it)

why could that be? I 'm pretty alarmed because, as it seems, anyone can just sudo -S and act as root, right?

You think it might have to do with me having the same user psswd with the root psswd?

---

### Post by northern lights on 2008-03-25
Unless you're planning on publishing your password - where's the trouble?

Any system is vulnerable by the way, if you allow people physical access...

---

### Post by alejaaandro on 2008-03-25
maybe i didn't make i t clear 

by running sudo -S i am not asked for my psswd

---

### Post by munkyeetr on 2008-03-25
> **alejaaandro said:**
> maybe i didn't make i t clear 

by running sudo -S i am not asked for my psswd

I just ran sudo -S and I was asked for a password. I am curious if you had just run sudo recently because the password stays in memory for an amount of time (not sure how long offhand), so you can run 1 sudo command and it prompts, and if you use sudo again right after it doesn't prompt.

---

### Post by northern lights on 2008-03-25
> **munkyeetr said:**
> the password stays in memory for an amount of time (not sure how long offhand), so you can run 1 sudo command and it prompts, and if you use sudo again right after it doesn't prompt.

This is it - sort of, at least. The option -S causes sudo to try to read the password from the terminals standard input stream, stdin (nearly every UNIX app runs three I/O streams: stdin, stdout, stderr). If you've entered your password before and it's still in stdin you won't be prompted.

Nothing to be alarmed about.

---

### Post by munkyeetr on 2008-03-25
Is there a setting somewhere to have it automatically cleared from stdin after it authenticates?

---

### Post by Oldsoldier2003 on 2008-03-25
> **munkyeetr said:**
> I just ran sudo -S and I was asked for a password. I am curious if you had just run sudo recently because the password stays in memory for an amount of time (not sure how long offhand), so you can run 1 sudo command and it prompts, and if you use sudo again right after it doesn't prompt.

sudo has a default timestamp life of 5 minutes. meaning you can run as many sudo'd commands as your lil fingers can type in that 5 minute session. to change this behavior you can eedit the sudoers file with the command :
```
sudo visudo
```

see this thread for a howto:
[http://ubuntuforums.org/showthread.php?t=183418](http://ubuntuforums.org/showthread.php?t=183418)

---

### Post by aysiu on 2008-03-25
> **alejaaandro said:**
> maybe i didn't make i t clear 

by running sudo -S i am not asked for my psswd
I don't know what you're talking about. I'm asked for a password.

---

### Post by Oldsoldier2003 on 2008-03-25
> **alejaaandro said:**
> I was trying to run a script with sudo... so I searched to sudo man and tried "sudo  -S (command)" and I can run the command as sudo ...later on, I searched the forum and found that I should do  "echo psswd | sudo -S command" (I know, there is a safer way, I just wanted to test it)

why could that be? I 'm pretty alarmed because, as it seems, anyone can just sudo -S and act as root, right?

You think it might have to do with me having the same user psswd with the root psswd?

Setting the root password in effect negates the security of using sudo. In rare cases it is necessary to log in as root but for the most part you should leave root disabled and use sudo instead.

---

### Post by alejaaandro on 2008-03-25
yeah, i've noticed the psswd is kept in memory for some time, that's why I waited a while before trying.. I just didn't know how long I should wait, (obviously I was just too impatient and never made it to the 5 min) .. I tried it now that I just turned the computer on and it prompted me for the psswd..

thanks guys, and sorry to bother with that...

---

### Post by joshrobinson on 2008-03-25
> **aysiu said:**
> I don't know what you're talking about. I'm asked for a password.

run a standard sudo command first
```
sudo apt-get update
```
it asks for your password, enter it, you now how 5 minutes of sudo commands with no password
```
sudo -S apt-get update
```
this code now goes fine with no prompt for password, because you are within the 5 minutes

if you run
```
sudo -S apt-get update
``` 
with no previous sudo commands, you will be prompted for a password

---

### Post by aysiu on 2008-03-25
I know that, joshrobinson, but that's not special to *sudo -S*. **Any** command you run with *sudo* before the timeout ends will not require a password.

---

### Post by joshrobinson on 2008-03-25
> **aysiu said:**
> I know that, joshrobinson, but that's not special to *sudo -S*. **Any** command you run with *sudo* before the timeout ends will not require a password.

sorry, but when you said "I don't know what you're talking about. I'm asked for a password." i assumed that meant you didnt know why the op wasnt prompted for a password

your wording threw me off i guess, i know its not special to sudo -S

---

### Post by toupeiro on 2008-03-25
+1 aysiu.  If you were to download the source for sudo and compule from scratch, I believe the default is 60 seconds it will cache a password starting from the last time a sudo-command was executed.  The more times you run sudo, regardless of which terminal window you are using, or tty or ssh connection, it will reset after each execution.

You can play with your sudoers file to set a new TIMEOUT setting, but I think in general, visudo will complain at you if you have the variable set any longer than 2 minutes out from the last execution timestamp.  You can also do sudo -v which forces sudo to validate.

---

