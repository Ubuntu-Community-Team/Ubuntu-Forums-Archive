---
title: "Root Account?"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by ravenproject_two on 2006-06-28
Hey,

I just installed Ubuntu a few days ago...I only have one user acct on my os so far-I was trying to explore the directories/hierarchy but it denied me access to every library file etc...do I have to log in to the root account?  If so how do I do that?  Plus I just downloaded the kde desktop package-was that a bad idea before I learned what the heck I am doing?  Thanks for your Time...

-TheRavenProject

---

### Post by Maggot on 2006-06-28
as your user you have to use:

sudo

They make it so you cannot login is root, only use root privileges with sudo

If you really wanna login as root (I do) type:  

sudo su
passwd

Though security wise you shouldn't ;)

---

### Post by aysiu on 2006-06-28
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions) explains everything.

---

### Post by ravenproject_two on 2006-06-28
Okay I checked out the link and did the "f you're using Ubuntu (Gnome), press Alt-F2 and type gksudo nautilus" and it pulled up a window with cache/desktop/share/socket/temp folders-Icons....when I clicked on a folder, say socket or temp, it told me that the link is broken and then prompted me asking if I wish to move that link to the trash?  What is that all bout?  Help

---

### Post by ciaka on 2006-06-29
To login as root, you can do one of the two things:

1.  Go to System/Users and Groups (I think thats what it is called)
     one of the options will be enable root login (doing this you can login as root from the login window.

2.  after you have logged in as the default user, you can issue the su command in terminal window.  Type su - (which will invoke the longin in that shell), then type in root password.  after that you will be logged in as root and can perform all the root functions.  Don't forget to type logout after youre done.

If anyone does not agree with this, please ring in so I can learn from you.  Thanks.

---

### Post by aysiu on 2006-06-29
[QUOTE=ravenproject_two]Okay I checked out the link and did the "f you're using Ubuntu (Gnome), press Alt-F2 and type gksudo nautilus" and it pulled up a window with cache/desktop/share/socket/temp folders-Icons....when I clicked on a folder, say socket or temp, it told me that the link is broken and then prompted me asking if I wish to move that link to the trash?  What is that all bout?  Help[/QUOTE] Why are you in this socket/temp folder? What are you trying to accomplish?

[QUOTE=ciaka]To login as root, you can do one of the two things:

1.  Go to System/Users and Groups (I think thats what it is called)
     one of the options will be enable root login (doing this you can login as root from the login window.

2.  after you have logged in as the default user, you can issue the su command in terminal window.  Type su - (which will invoke the longin in that shell), then type in root password.  after that you will be logged in as root and can perform all the root functions.  Don't forget to type logout after youre done.

If anyone does not agree with this, please ring in so I can learn from you.  Thanks.[/QUOTE] I don't agree with this. Logging in as root is unnecessary and usually requires too many extra steps in Ubuntu (other distros are a different story).

It's far easier to do Alt-F2 ```
gksudo nautilus
``` to make graphical changes than it is to do a new login with root and then log out again.

You can also temporarily gain root access in the terminal by typing ```
sudo -s
``` or, better yet, just preface each root-level command with *sudo*: ```
sudo aptitude update
sudo aptitude install *packagename*
```

---

