---
title: "Root login"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by prhandley on 2007-11-23
Hi:
I am a complete novice newbie on linux so please forgive me if this question has been asked many times.
I have installed 7.10 server edition and the install seems as though it went fine as I can boot up and get a login request.  Being a non-techy though I would like to get a GUI up  and running and I have found details of how to do that.  HOWEVER when I log in as me (user) it says I am not on the sodoer list and can't therefore set up a GUI, and apparently the root login is disbled by default.  With my user account I can't enable a root login.
This seems like a closed loop - can anybody help me please?
Thanks

---

### Post by TidusBlade on 2007-11-23
I would recommend try messing around in the Users and Groups section in System >Admin.
And you can enable root login by going to System >Admin >Login Window. OR it could have been in prefrences. Look in one of the tabs, and it should be there.
Sorry if my information is a bit off, Im using Kubuntu and my Ubuntu Knowledge is quite rusty...

---

### Post by s26c.sayan on 2007-11-23
If you need a GUI, why not install the 'regular' version of Ubuntu instead of the server edition! :O

---

### Post by prhandley on 2007-11-23
I am trying to get into Ubuntu server so I can add the machine to my network for use as a file server - also I would like to learn more about Linux in general hence my interest.

---

### Post by prhandley on 2007-11-23
Thanks for the info but when I try what you recommend I get "-bash: system: command not found"
Do you have any more suggestions please?
Thanks

---

### Post by LaRoza on 2007-11-23
You might want to install Ubuntu Desktop, and then install the server:

```

sudo tasksel

```

This will enable you to do things easier if you are just using this for a small network and you can use the extra CPU cycles for the GUI.

---

### Post by prhandley on 2007-11-23
Sorry to seem a bit thick but do you mean install the PC version first and then upgrade to server edition.
You suggest using sudo tasksel which I can't do at the moment with my login.

Thanks

---

### Post by LaRoza on 2007-11-23
Ubuntu is just a collection of packages. The desktop version and server version are just different packages, and are not exclusive to the other.

You can install "ubuntu-desktop" from the server, but with your problems, you can install the desktop version first, then the server with tasksel.

You will have the functions of both.

---

### Post by hyper_ch on 2007-11-23
well, root is disabled by default. Use *sudo* instead.
Then, a server with a gui doesn't make much sense. It will waste unnecessary processing power and ram. Au contraire to Windows, Linux does not have a central registry for configuration stuff. Each service will have its own configuration file and for most (server) services, there are no GUI configuration tools - except stuff like SWAT, webmin, ISPConfig....
So if you want to operate a server, you will need to get to know on how to get along in the command line. It's not that difficult but you'll have to learn.

And what does, for you, the fileserver need to do? What does it need to be capable of?

---

### Post by LaRoza on 2007-11-23
> **hyper_ch said:**
> Then, a server with a gui doesn't make much sense. It will waste unnecessary processing power and ram.

And what does, for you, the fileserver need to do? What does it need to be capable of?

No, a GUI on a server is not recommended, but it helps when learning.

If the need is not great (no public websites, or corporate servers) a home computer with a GUI will be useful.

---

### Post by hyper_ch on 2007-11-23
> **LaRoza said:**
> No, a GUI on a server is not recommended, but it helps when learning.

How does it help when learning?

---

