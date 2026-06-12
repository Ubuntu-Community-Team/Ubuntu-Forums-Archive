---
title: "[SOLVED] sudo not working.  Help!"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by Aurora@FleetBuzz on 2008-01-12
I was able to access the superuser account yesterday with "sudo" and my password.  However, today I type "sudo" and this is what I get:
> donj@donj-desktop:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
donj@donj-desktop:~$ 

However, I can access the root with "sudo su":
> donj@donj-desktop:~$ sudo su
(prompts for password)
root@donj-desktop:/home/donj# 


How do I get "sudo" working again?

Also, when I run "gksudo" from the terminal, I get a "Run Program" dialog box.  Is this what's supposed to happen?

---

### Post by Pevichaey5 on 2008-01-12
just use the command 

su

that means Switch User, and the default user is root, use sudo if you are trying to open a particular program as root lik

sudo gedit

---

### Post by fiddledd on 2008-01-12
Unless you know something I don't, I thought sudo had to be follwed by a command to execute, for example sudo vnstat, sudo gedit, sudo cp etc etc. in which case there's nothing wrong with "sudo"

EDIT:
I type way too slow and post way too late :(

---

### Post by amo-ej1 on 2008-01-12
sudo should be followed by exactly one parameter, in this case the application you wish to run. To run 'su' as root you would enter 'sudo su' to run 'ls' as root you'd type 'sudo ls'. When there is no application specified you will get a message just like you did. And it probably behaved like that as well yesterday ;) 

The same story goes for gksudo, but instead of providing you with some textual information on the console like sudo does, it simply prompts you which application you wish to run as which user.

For more info, type 'man sudo'.

---

### Post by monte48lowes on 2008-01-12
By default the root account is not enabled in ubuntu. Use sudo to start a program or execute a command as root. Use gksudo to start a graphical program as root.

Examples:

sudo apt-get install firefox

gksudo nautilus

Mike

---

### Post by Aurora@FleetBuzz on 2008-01-12
Thanks, but I thought "su" meant "super user" and was supposed to be disabled by default?

Is there any way I can restore the "sudo" command back to 'normal'?

Mike:
When I type "sudo", I get the gibberish in my first post.  I have to type "sudo su" to actually access the root.  Also, there's that launcher that starts up when I type "gksudo".  I used it yesterday to modify file permissions in Nautilus and I might have altered something!

---

### Post by Aurora@FleetBuzz on 2008-01-12
amo-ej1, thanks!  Well that cleared up the "gksudo" application launcher thing.  I tried it with "gksudo nautilus" and it worked fine!

Is there an innocent command I can type after "sudo" to verify that the thing's working correctly?  Perhaps the only problem here is operator ignorance!

---

### Post by amo-ej1 on 2008-01-12
try whoami:

```

edb@Flying-Spaghetti-Monster:~$ sudo whoami
root
edb@Flying-Spaghetti-Monster:~$ whoami
edb

```


edit: whoami shows you your current user id

---

### Post by Aurora@FleetBuzz on 2008-01-12
I did.  This is what I got:
> donj@donj-desktop:~$ sudo whoami
root
donj@donj-desktop:~$ whoami
donj
donj@donj-desktop:~$ 
Does it appear to be working correctly?  It looks like the one in your post....

---

### Post by Pevichaey5 on 2008-01-12
su is switch user

from terminal, you can log in as different users, such as root, yourself, all users as long as you have the password

---

### Post by amo-ej1 on 2008-01-12
sure it works correctly, you can clearly see it says that it was executed as root when you put sudo in front of it, and that it was running normally when the sudo was omitted.

---

### Post by Aurora@FleetBuzz on 2008-01-12
My sincere thank to all of you who took the time to answer this for me!  I'll mark the thread as "Solved".

---

