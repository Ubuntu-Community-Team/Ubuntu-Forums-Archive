---
title: "Installed 6.06 but cannot log in."
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-02
Hi I installed Ubuntu 6.06, changed the hostname from "ubuntu" to for example "xyz". I set my password, for example "password".

The install goes fine, I get to the log in screen. I see my hostname bottom right, type that in and my password and then I get this error message, "Incorrect username or password. Letters must be typed in correct case."

So I reinstalled Ubuntu 6.0.6 and the exact same problem.

Then I go to my other box, type in that username and password and once again I have this problem.

I have no idea what the problem is. I am here on XP as my 2 Ubuntu boxes deny me access.

I installed the system as an OEM.

Any idea what the problem is? My username and password are correct and in the correct case.

Thanks.

](*,)

---

### Post by adam.tropics on 2006-06-02
I know you said correct case and all, they wouldn't happen to be laptops? Numlock?

---

### Post by Jagot on 2006-06-02
When you install as an OEM you set a specific password for the OEM user to set up the machine usually before giving it to someone else to setup their username/password etc, on.  You did set up another user after the OEM setup?

---

### Post by u.b.u.n.t.u on 2006-06-02
[QUOTE=Jagot]When you install as an OEM you set a specific password for the OEM user to set up the machine usually before giving it to someone else to setup their username/password etc, on.  You did set up another user after the OEM setup?[/QUOTE]

No. I saw OEM or text install - I just wanted a GUI install.

I want the "install Ubuntu on this machine for me to use" option.

How do I set up the user or have I installed this wrong? 

Thanks.

---

### Post by u.b.u.n.t.u on 2006-06-02
I am installing Ubuntu for a 3rd time now. This time in "text" mode and leaving "Ubuntu" as the hostname.  This time I was given the option of adding a username and password. Seems more promising. It takes 25 minutes to install on my box - 2.5Ghz AMD, 1GB RAM.

What exactly is the OEM for and how can a user be added?

Thanks.

Edit. Compared to about 40/45mins for XP PRO. Then another 10-15 minutes turning off all the default settings, setting up the look etc. Ubuntu Dapper I just install and can use (If I am allowed to log in that is :P). So Ubuntu "installs" about half the time that XP does.

---

### Post by u.b.u.n.t.u on 2006-06-02
Install as "text" worked. :D

---

### Post by skippy81 on 2006-06-02
[QUOTE=u.b.u.n.t.u]I see my hostname bottom right, type that in and my password and then I get this error message, "Incorrect username or password. Letters must be typed in correct case."[/QUOTE]

Probably just a typo on your part, but you do know that *username* and *hostname* are two entirely different things? 

The hostname identifies your PC on a network, it does not have a password set against it.

Your username should have been entered during installation.  You will have been asked for your hostname (ie "ubuntu") It should then have asked you for your full name (Ie "john smith") and then your username (ie "john"). Finally it will ask for you to enter your password twice (ie "apple25").

To log in, you would type "john" (your username) and your password "apple25".   Your hostname is irrelevant to this process.

---

### Post by Perfect Storm on 2006-06-02
If you want gui installation, you need to use the live CD which boot you into ubuntu live and from their hit the icon that says install ubuntu. It takes alot more time though.

---

### Post by u.b.u.n.t.u on 2006-06-02
skippy81 there was no typo on my part. The "OEM" install didn't let me nominate a user. The "text" install did and that worked - I am typing this on the exact same computer.

Note to self: learn more about what an ubuntu "OEM" does.

---

### Post by u.b.u.n.t.u on 2006-06-02
[QUOTE=Artificial Intelligence]If you want gui installation, you need to use the live CD which boot you into ubuntu live and from their hit the icon that says install ubuntu. It takes alot more time though.[/QUOTE]

The "text" install on the "alternative" had a GUI. That works.

Thanks everyone for the suggestions.

:D

---

### Post by mcduck on 2006-06-02
You need the OEM install if you want to preinstall Ubuntu, for example when selling computers with Linux installed. It allows you to install Ubuntu, and then configure it, and when the user/customer first time boots the machine Ubuntu will ask to create user & set password.

Just like when you buy a machine with windows preinstalled.

---

### Post by u.b.u.n.t.u on 2006-06-02
Thanks. :cool:

---

### Post by bluefrog on 2006-06-02
OEM installation creates an oem user with the password you specified, that's all.

so you need to log in as 

oem
your password

James

---

