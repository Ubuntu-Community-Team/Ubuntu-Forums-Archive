---
title: "First post"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by blakebb on 2008-01-26
I've had Ubuntu for a little while now and I'm really enjoying it.  Although recently I was messing around in the users window to see about adding different people.  

Anyways, the crux of the matter:  while I was in there I changed my home directory name, because I didn't really like it.  Unfortunately, when I logged off and tried to log back in, it said that my home directory is correct and it can't login. 

If I proceed to try to login as the root, it gives me : User's $HOME/.dmrc.file is being ignored and something about 644 permission.

Can I change this with terminal commands?

I'm a newbie.. thanks

---

### Post by taurus on 2008-01-26
You need to reset the permissions to that file.  Assuming your login name is blake, run

```
sudo chmod 644 /home/blake/.dmrc
```

---

### Post by JoshuaRL on 2008-01-26
You should be able to.  Remember three commands:

```

cd

```
That stands for change directory.  That will allow you to manuver around in the filesystem.  If you wanted to move to the X11 folder inside the etc folder, you would add "/etc/X11" to the end.  To go to the root folder, just type "cd" followed by nothing else.

```

ls

```
That stands for list.  It will list all the files and folders in the current directory.  It will tell you where you are.  Really useful.

```

mv

```
That stands for move.  It will either move files or rename them depending on how you use it.  For what you want, you'll want to type something like:
```

mv -i /home/wrongname /home/rightname

```
where /home/wrongname is a real directory and /home/rightname isn't yet but will be after the command.  The "-i" option stands for "interactive."  It will prompt you to change the directory name.

And for a great tutorial on the terminal, go here:

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by The Cog on 2008-01-26
At the boot prompt, choose rescue mode. This dumps you in a text console as root. You can do one of two things:

Rename your home directory as JoshuaRL says:
**mv -i /home/wrongname /home/rightname**

Edit the file /etc/passwd and put the home directory name back again so it matches the directory name:
**nano /etc/passwd**

---

