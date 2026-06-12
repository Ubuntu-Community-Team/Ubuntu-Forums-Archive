---
title: "Just installed.. now what?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by rgrimes on 2007-05-08
Ok, I'm not a complete moron, but I'm starting to feel like.........

I just downloaded and  installed Ubuntu Server 7.04, now somewhere I'm sure I missed how to login as "root", can someone clue me in on the password or where to find it?? 

I created my own user id when doing the install, but I don't believe that would have admin rights.

Thanks in advance!
rgrimes

---

### Post by aysiu on 2007-05-08
There is no root.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Gmbrdilos on 2007-05-08
[https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29](https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29)

---

### Post by fakie_flip on 2007-05-08
If you want root, just do this:

sudo passwd root

Now when you do:

su -

You can login as root and get the # prompt instead of the $ one.

---

### Post by rgrimes on 2007-05-08
ok, so what is the administrator user and password? Sorry if I sound like a dunce, I'm trying real hard to break free from "Uncle Bill Gate" and company.

---

### Post by compmodder26 on 2007-05-08
The user you created when you first installed it.

---

### Post by rgrimes on 2007-05-08
Thanks fakie_flip!! 

How do I get a GUI running?

---

### Post by rgrimes on 2007-05-08
Man, THIS IS GREAT!!!!!!

I will have to adjust to these "instant" replies to my posts!! :o)

---

### Post by aysiu on 2007-05-08
> **rgrimes said:**
> Thanks fakie_flip!! 

How do I get a GUI running?
This will help you get a GUI:
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

By the way, the Server edition usually doesn't have a GUI, because it's a server, not a desktop. The Desktop CD and Alternate CD give you a GUI straightaway.

---

### Post by rgrimes on 2007-05-08
Thanks aysiu! I'll give it a try. Yeah I noticed when I ran the Live CD for desktop there was a GUI, so thought maybe there was one for the server also. 
I seem to remember something about xwindow in RedHat a couple of years ago..

Thanks for the help!

---

### Post by aysiu on 2007-05-08
Just to clarify, though, are you installing a server or a home desktop?

---

### Post by ilikeytacos12345 on 2007-05-08
> **rgrimes said:**
> Thanks fakie_flip!! 

How do I get a GUI running?

guis are not for servers. gui + servers in linux do not go together. you want all the system resources for the server, not to run a gui.

---

