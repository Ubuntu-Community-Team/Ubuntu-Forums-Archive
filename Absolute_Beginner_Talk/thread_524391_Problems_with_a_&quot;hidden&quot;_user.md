---
title: "Problems with a &quot;hidden&quot; user"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Helleshoj on 2007-08-13
I am quite new to the world of Linux, but have played around a bit with Unix on IBM and OS X in the course of my job. Now I succeeded in installing Ubuntu 7.04 on an old G4 PPC with no more difficulty then can be expected, but when I wanted to install Postgresql I ran into difficulties.  During installation a user "postgres" was made, and probably also a password, but I do not know the password and have not been able to find a way  to show the user. 
In  Users and Groups administration, when I try to make a user "postgres", I get the message that such a user exists, but even though I have set  show_all and show-all in gconf  - as is suggested in another thread - I can not make the system show me that user.

Any suggestions on how to make it come forward?

or any suggestions on how to get Postgresql working?

---

### Post by Skrynesaver on 2007-08-13
The postgres user is a dummy user which the posqrtesd will run under.

you can become the postgres user using the command
```

sudo su postgres
```
have a look [here]("http://bioinformaticsonline.co.uk/2007/02/26/postgresql_on_ubuntu_linux_how_to") for more details on setup

---

### Post by Helleshoj on 2007-08-13
[QUOTE=Skrynesaver;3181112]The postgres user is a dummy user which the posqrtesd will run under.


```

sudo su postgres
```

I still need an unknown password for that – I have tried.

I will go through the instructions contained in your link.

---

### Post by Helleshoj on 2007-08-13
> **Skrynesaver said:**
> The postgres user is a dummy user which the posqrtesd will run under.

have a look [here]("http://bioinformaticsonline.co.uk/2007/02/26/postgresql_on_ubuntu_linux_how_to") for more details on setup

I can see that I have already used that instruction. Think it will be one more time from the beginning with this. 
I installed Ubuntu because I could not get Postgresql running under OS X... Seems it is a difficult one to configure.

---

### Post by Skrynesaver on 2007-08-13
> **Helleshoj said:**
> sudo su postgres[/code]I still need an unknown password for that – I have tried.

The password you are asked for is the sudo password which is your own password, su allows you to switch to any user

---

