---
title: "Installing Programmes"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by richard978 on 2008-03-11
I have installed my dual boot xp and ubuntu linux os system and so far it's working fine. I've installed the desktop version for standard pentium and I'm looking at running apache friends so I can develop in a linux environment.

I'm a bit lost though, how do you install new programmes????????????????????????????

Please help

Richard

---

### Post by hyper_ch on 2008-03-11
Open synaptic, chose the programs you want, click "apply" or "install" or something like that.

Or use the command line:

```

sudo apt-get install taskel

```
for the whole apache/php package... or you could install all the components individually - what I would do

btw:

[http://www.psychocats.net](http://www.psychocats.net)

[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

[https://wiki.ubuntu.com](https://wiki.ubuntu.com)

three excellent sites that should answer a lot of questions.

---

### Post by jken146 on 2008-03-11
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by richard978 on 2008-03-11
Apache Friends looks easier to use, if I install it from the synaptic package manager as individual items how difficult are the individual items to use? For example, php, mysql and apache.

Please consider the fact that I am a windows user and have been for 15 years. The reason I'm moving to linux is I think Vista is possibly the worst os I have ever seen and I'm fed up with getting malware and system crashes.

Also I tried logging in as a root adminstrator su and it asks for a password. My login password does not work, is there a default for this.

---

### Post by jken146 on 2008-03-11
Ubuntu uses sudo.  See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for an explanation.

It's highly recommended that you install software from the repositories.  PHP, MySQL and Apache all work very well together and it's easy enough to use them once installed.

[http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100](http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100) will take you through it step by step.

---

### Post by hyper_ch on 2008-03-11
[http://www.howtoforge.com/perfect_server_ubuntu7.10_p4](http://www.howtoforge.com/perfect_server_ubuntu7.10_p4) --> Step 13 for MySQL
[http://www.howtoforge.com/perfect_server_ubuntu7.10_p6](http://www.howtoforge.com/perfect_server_ubuntu7.10_p6) --> Step 16 for Apache/PHP

---

### Post by richard978 on 2008-03-11
I've installed apache and php via the package manager and via the terminal and I'm coming across the same problem. As Ubunto uses sudo as the root login once I've installed these applications it won't let me save documents into the www directory. I don't have permission as a user. 

What am I doing wrong?

---

### Post by mikecomua on 2008-03-11
If you want to be root for the entire terminal session```
sudo -i
```
This may not work, but try doing chmod a=rwx www(your directory).

---

### Post by MONODA on 2008-03-11
you can also use add/remove from the applications menu.

---

### Post by hyper_ch on 2008-03-12
well, the /var/www folder is owned by root... so either you edit files there as root or your change ownership/permissions.... apache2 should run by default as www-user I think

---

