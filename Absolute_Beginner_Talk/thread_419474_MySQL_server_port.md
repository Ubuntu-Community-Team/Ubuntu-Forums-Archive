---
title: "MySQL server port"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by ahlandberg on 2007-04-23
Hello. I have installed MySQL on my Ubuntu machine and want to remotely access it through putty.

I have a dyndns account and have tried to logon this way: mysql -h [email]root@hostname.dyndns.org[/email] -u root -p

But I only get an error telling me "Unknown MySQL Server host".

How can i find out which port mysql is running on, isn't it usually 3306??
And how can i connect to the server remotely then?

Thanks in advance!

Anders

---

### Post by Stickymaddness on 2007-04-23
Have you been able to log in remotely using putty normally? If you have remote shell access surely you can just run

```

mysql

```

From the command line?

---

### Post by ahlandberg on 2007-04-23
I can logon to my Ubuntu machine via putty/ssh, that works fine.

What I wanna do is to logon to another ssh account that I have and then logon to my ubuntu machine from there.

---

### Post by Stickymaddness on 2007-04-25
> **ahlandberg said:**
> I can logon to my Ubuntu machine via putty/ssh, that works fine.

What I wanna do is to logon to another ssh account that I have and then logon to my ubuntu machine from there.

Then once you've logged on your other account

```


ssh your_ubuntu_machine


```

---

### Post by az on 2007-04-25
Mysql does not listen to the network by default.

[https://help.ubuntu.com/community/ApacheMySQLPHP#head-2b91cc1ce37842102d20e88e029477b035bee150](https://help.ubuntu.com/community/ApacheMySQLPHP#head-2b91cc1ce37842102d20e88e029477b035bee150)

---

