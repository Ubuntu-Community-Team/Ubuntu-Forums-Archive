---
title: "make /home on another computer"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by TJCIB on 2008-03-23
I have a group of computers with dinky hard drives.  I have another with a really big hard drive that could fit them all and more.

Is there a way I can make a user's home directory a directory on another system?  Would I have to use samba?

I am assuming I would define it in /etc/shadow where it tells where the home directory is.  But how do I make the actual link between computers?

This is sort of like a thin client, except only the home directory is stored on the "server" whereas the OS and everything else is stored on the workstation.

I found this link 
[http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/](http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/)
but it seems like its director toward accessing it on a windows machine.  Is it still relevant?

I don't want to just access a directory, I want the actual home directory to be on another computer.

I am using 7.10

Thanks

---

### Post by tkiesel on 2008-03-23
There shouldn't be anything impossible about this.. you'd just need to locate the /home partition on a remote machine through samba.  There are some guides out there that will help you experiment with this.. it'll be quite experimental though. :)

---

### Post by saj0577 on 2008-03-23
Where is i that the variable for where your home folder is, is stored?

Saj

---

### Post by Darganot on 2008-03-23
it should be $HOME

---

### Post by saj0577 on 2008-03-23
> **Darganot said:**
> it should be $HOME


What file is that value stored in?

Saj

---

### Post by louieb on 2008-03-23
Might want to look at NFS. Haven't done it but it looks like your can set up a partition on an NFS server and mount it as /home on the client computer when its boots.
[Setting Up an NFS Server]("http://tldp.org/HOWTO/NFS-HOWTO/server.html")

---

### Post by saj0577 on 2008-03-23
How/where do you mount your home directory ( i know how to mount but not to make it your home directory)

Saj

---

### Post by jkreef on 2008-03-23
Have you tried going to System-Administration-Users and groups. Then click on the user you want to change the home directory then preferences. Click on the advanced tab, then you should be able to change the home directory from there.
Hope it helps!

---

### Post by saj0577 on 2008-03-23
> **jkreef said:**
> Have you tried going to System-Administration-Users and groups. Then click on the user you want to change the home directory then preferences. Click on the advanced tab, then you should be able to change the home directory from there.
Hope it helps!

Yeah thanks I think that will work, i will give it a go.

You know how to access this menu through terminal? 

Saj

---

### Post by jkreef on 2008-03-23
Sorry I don't. I'll try to figure it out for you though. Also, make sure the method works using a throw-away account first. It should work but I don't want to mess up your system.

---

### Post by saj0577 on 2008-03-23
Yeah cheers. I just need to work out if it will work with a networked folder which im trying right now as we speak :)

Saj

---

### Post by jkreef on 2008-03-23
Let me know if it works please.

---

### Post by saj0577 on 2008-03-23
Just to see i tried smb as a tester and it did not work so i think i need to mount to /media/home/saj  for example and then set that as my home directory which will intern link it to the networked folder that make sense and seem possible?

Saj

---

### Post by jkreef on 2008-03-23
It all seems perfectly logical to me. However I am an extreme beginner to Ubuntu and Linux in general so I don't know if it's possible.

---

### Post by saj0577 on 2008-03-23
Lets give it a go ;)
Saj

---

### Post by saj0577 on 2008-03-23
I think i will have to actually try it on my proper computer for real as creating a shared folder over virtualbox is causing a bit of a problem.

Saj

---

### Post by jkreef on 2008-03-23
Being an impatient person, I have to wonder if it worked? And if so how to do it.

---

### Post by saj0577 on 2008-03-23
Right I have nto got a shared folder from a linux machine.
so what i am gonig o do is try and make a external USB pen drive the home folder to see if i link the home folder to /media/usb cos if that works than my idea will work in theory :)

Saj

give me 5 minutes mate

---

### Post by louieb on 2008-03-23
> Have you tried going to System-Administration-Users and groups. 
> **saj0577 said:**
> You know how to access this menu through terminal? 
There are several commands for you to play with **userad usermod userdel passwd** as well as **groupadd  groupdel  groupmod  groups**
To get tot he GUI from a terminal window its ```
gksu users-admin 
```

---

### Post by saj0577 on 2008-03-23
> **louieb said:**
> There are several commands for you to play with **userad usermod userdel passwd** as well as **groupadd  groupdel  groupmod  groups**
To get tot he GUI from a terminal window its ```
gksu users-admin 
```

What about no GUi at all i know how to create a user in temrinal but that is it.

Saj

---

### Post by saj0577 on 2008-03-23
> **saj0577 said:**
> Right I have nto got a shared folder from a linux machine.
so what i am gonig o do is try and make a external USB pen drive the home folder to see if i link the home folder to /media/usb cos if that works than my idea will work in theory :)

Saj

give me 5 minutes mate

Got it kind of working just got permission problems now.

Saj

---

### Post by ByteJuggler on 2008-03-23
This is quite possible, and it would be a lot easier/better if you used NFS, rather than Samba, as NFS is "Unix Native" and will help maintain/respect file permissions from a Unix point of view.  That said, it should also be possible to make it work with Samba.  I've not looked at NFS in ages though so if you're interested in how to set that up/get stuck then post back and I'll dig into it a bit.

---

### Post by saj0577 on 2008-03-23
Yeah i am using NFS mate :). Just having a bit of trouble with the permissions but i think i have got that sorted now. Just need to link all the little bits togther now.

Saj

---

### Post by TJCIB on 2008-03-23
when adding users manually (i.e. changing the files, not through terminal or GUI) i had to change three files

/etc/shadow
/etc/passwd
/etc/group

in the /etc/shadow file it states the user's home directory in addition to a few other things.  I just added the lines in there for the new user and stated where the home directory was /home/<username>
This was on the same hard drive, so all I had to do what creat the directory /home/<username> and assign the 700 permission/ownership to the directory.

I wonder if I can just do that but instead of /home/<username> I could do something like //lab1/home/<username> and link it with samba.....interesting...

---

### Post by saj0577 on 2008-03-23
I tried using smb:// and that did not work so i think you have to mount the folder first but i am not sure.


Saj

---

### Post by ByteJuggler on 2008-03-23
> **TJCIB said:**
> 
I wonder if I can just do that but instead of /home/<username> I could do something like //lab1/home/<username> and link it with samba.....interesting...

Forget Samba for this.  Mount /home onto another machine via NFS at boot time, then you don't have to mess with your passwd file at all.  (Actaully you can even do that with Samba if you want, e.g. mount a samba shared folder on /home at boot time if you really must...)

---

### Post by TJCIB on 2008-03-23
My issue is I have 30 users on a lab network of computers.  We don't currently have a server strong enough to run thin client.  But if I could get everyone's home directory onto one drive, it would save a lot of confusion over which computer you did what on.

setting one user's home directory to another machine through NFS sounds simple enough, now how do I do that on 15 machines with 30 users each with their own /home on one main machine?  (Besides doing it manually, I'm lazy)

It will be a fun few days...

---

### Post by saj0577 on 2008-03-23
You know how to do it manually for one?

How?

Could automate it with a script but it wil be just as quick to do it manually unles you know what your doing lol

Saj

---

### Post by saj0577 on 2008-04-08
Anyone know how to do this between 2 systems?

Saj

---

### Post by TJCIB on 2008-04-08
Setting up the login system is easy.  All of your users set up on one system and then follow these directions for NIS

[http://www.debian-administration.org/articles/36](http://www.debian-administration.org/articles/36)

The NFS system was a little more involved.  I had some trouble getting it to work, but I think this is because of our complex school Network, not the instructions.  Most of my trouble came with getting the submasks right, but for two systems, should be a breeze.

The walk-through I used for NFS is here
[http://tldp.org/HOWTO/NFS-HOWTO/server.html](http://tldp.org/HOWTO/NFS-HOWTO/server.html)

it doesn't specifically say how to get the directory to be a /home directory, but I think with a quick search you could figure it out.  Its basically getting the ownership and permissions correct.

Hope this helps.

---

