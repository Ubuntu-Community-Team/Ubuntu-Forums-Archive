---
title: "[SOLVED] limited access through ssh?"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by kaiju on 2008-02-02
i want to create an account that will be accessed through ssh. the user is supposed to have read-only permissions for my directories.
it would be nice if i could set the directories to 'share', but it's not a major problem if the whole system is displayed. in this latter case though, it would still be good if i could limit access with the help of file permissions.

if anyone is using this kind of setup, please let me know how you got it working.
thanks

---

### Post by finer recliner on 2008-02-03
this has nothing to do with ssh. ssh will allow any user on the system remote access to the computer. the settings you are describing must be done on the account itself. i suggest looking into the command chmod. it is used to change file/directory permissions for users on a computer.

---

### Post by kaiju on 2008-02-03
thanks, you are right, finer recliner. my request is probably not clear enough.

what i'm interested in is not a setting for ssh or so, but the whole complex solution i could adopt. i've read about chroot, but it seems that it has problems with symlinks. i'm thinking there could also be a way of doing this just by limiting access through file permissions (like setting specific umask values) and group membership of the account that is to be used. and since i don't really know that much, there are probably other ways i've never even heard of.

so, to make it somewhat clearer: i'd need some setup models that can grant limited user access to my system.

---

### Post by kaiju on 2008-03-12
quick revision:

finer recliner was right, of course. in the end i made a separate account to be used for downloading files from my computer through sftp in an ssh session.
the new user account has its shell set to rssh, which is configured to only allow scp and sftp transactions. sweet.

---

### Post by kevdog on 2008-03-13
Can you provide details about how you did this?  Thanks!

---

### Post by bravo_s on 2008-07-03
Hi!

I found rssh tutorial [http://www.cyberciti.biz/tips/linux-unix-restrict-shell-access-with-rssh.html]("http://www.cyberciti.biz/tips/linux-unix-restrict-shell-access-with-rssh.html"). Alowed scp and sftp and everythig worked fine in the terminal. But when I tried to connect with gFTP I was able to browse the directories below the user's home directory. I'm not shure if I'm missing somethig but this doesn't meet my requirements.

I'm using Ubuntu Hardy and gFTP 2.0.18.

If anyone has solution, please share it!

---

### Post by kaiju on 2008-07-06
> **bravo_s said:**
> ...when I tried to connect with gFTP I was able to browse the directories below the user's home directory. I'm not shure if I'm missing somethig but this doesn't meet my requirements.

what a user logged in through sftp is allowed or not allowed to read/write/execute depends on file permissions. so if you set up a new account for this and it isn't included in any special groups, it will only give access to files that can be read/written/executed by anyone (last three values in the first column, if you do an 'ls -l'). to change permissions, you can use chmod (see 'man chmod').

---

