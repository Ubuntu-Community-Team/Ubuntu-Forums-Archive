---
title: "Login users and start X sessions for them"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by tamster on 2007-10-24
Hello!

Is it possible to login multiple users, start X GUI for them and run script (from their uid, in their session) from different user's command line?
Didn't find anything related..

Thank you

---

### Post by kernel tom on 2007-10-24
If you add users to one machine, you can definately start an X GUI for them from remote computers, but I am not sure what you are trying to do.

I believe it is not possible to have more than one X session running at a time on the local machine, but you can secure connect to that machine from any other.

Can you explain what you are trying to do further?

---

### Post by tamster on 2007-10-24
I need to run multiple instances of one program and interact with it's interface (no command line options there).
I've written a script which clicks buttons, etc. So when I manually login, start X server and execute my script - everything's ok. Now I would love to automate this for multiple user accounts, without manually loggin to them and launching script for each. Scenario would be something like this:

Logging user1 in..
Starting X for user1
Logging user2 in..
Starting X for user2
Logging user3 in..
..
Running script as user1
Running script as user2
..and so on

---

### Post by Dr Small on 2007-10-24
This sounds similar to what you need:
[http://php.8ez.com/drsmall/blog/?p=110](http://php.8ez.com/drsmall/blog/?p=110)

---

### Post by tamster on 2007-10-24
> **Dr Small said:**
> This sounds similar to what you need:
[http://php.8ez.com/drsmall/blog/?p=110](http://php.8ez.com/drsmall/blog/?p=110)
Well.. not exactly.. I need to do this fully automatically, from script and for like 50 graphical sessions.. Is it even possible to run 50 X sessions on one machine?
Software that i'm dealing with doesn't allow multiple instances for one user, but I need it to be running at the same time..

---

### Post by tamster on 2007-10-28
Maybe using VNC would make it possible.. somehow? Any ideas?

---

### Post by timcredible on 2007-10-30
it's possible to do 50 x sessions using xdm, providing your server is beefy enough.  you can automate the xsession by adding the command line in the following link to the user's .bashrc file.  i'm assuming that you have 50 linux machines all connecting to 1 linux machine.  that's not a problem.  please see my how-to for setting up xdm:  [http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=27](http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=27)

---

### Post by tamster on 2007-10-31
> **timcredible said:**
> it's possible to do 50 x sessions using xdm, providing your server is beefy enough.  you can automate the xsession by adding the command line in the following link to the user's .bashrc file.  i'm assuming that you have 50 linux machines all connecting to 1 linux machine.  that's not a problem.  please see my how-to for setting up xdm:  [http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=27](http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=27)

Thanks, I will check out the link you provided.
Actually I just need 50 x sessions with script running inside each of them - I don't need to connect to server from other machines. Just a bunch of local activity..

---

