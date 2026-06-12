---
title: "Help to configure Mutt"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by Cheves on 2007-03-21
Well, presenting myself first, I am Cheves.
I'm a newbie in all this linux stuff, and I'm doing my best to learn.
I've been reading the forum for a few weeks and I think it's was time to register.
I need help to configure Mutt.
I'v already installed mutt, but I need the commands to be able to configure my email account.
Any help will be apreciated.


](*,) :-k :-D

---

### Post by Cheves on 2007-03-21
:Bump:

anyone?

---

### Post by tkjacobsen on 2007-03-22
I'm not at home, so I cannot send you my configuration files.. I learned it from the configuration file examples on their homepage [www.mutt.org](www.mutt.org).. (Can't send you a more specific link 'cause their site is offline).

I can post some of my configuration files tomorrow if you like. (I actually use fetchmail and procmail to get and sort my email - that's because I have multiple mail accounts to fetch from. Then I use msmtp to deliver my mail)

EDIT:
These links also helped me
[http://www.debian-administration.org/articles/75](http://www.debian-administration.org/articles/75) (in Ubuntu use w3m instead of links -- it's installed by default )
[http://www.linux.com/article.pl?sid=05/10/07/172259](http://www.linux.com/article.pl?sid=05/10/07/172259)

---

### Post by Cheves on 2007-03-24
Thanks for your help!
I'm gonna try that!

---

### Post by tkjacobsen on 2007-03-24
Here are all my mutt configuration files attached..

Sorry about the delay.


NOTE that muttrc should be .muttrc in your $HOME, same with mailcap.

---

### Post by andrew.46 on 2007-07-05
Hi,

 This may be a little late to help your query:

> **Cheves said:**
> Well, presenting myself first, I am Cheves.
I'm a newbie in all this linux stuff, and I'm doing my best to learn.
I've been reading the forum for a few weeks and I think it's was time to register.
I need help to configure Mutt.
I'v already installed mutt, but I need the commands to be able to configure my email account.
Any help will be apreciated.](*,) :-k :-D

 but I have just finished a page that may help you:

[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

                              Andrew

---

### Post by Cheves on 2007-07-05
> **andrew.46 said:**
> Hi,

 This may be a little late to help your query:

 but I have just finished a page that may help you:

[http://people.aapt.net.au/~adjlstrong/mutt.html]("http://people.aapt.net.au/%7Eadjlstrong/mutt.html")

                              Andrew

Thank you for your help Andrew, but I'm still getting problems here:

checking build system type... i586-pc-linux-gnu
checking host system type... i586-pc-linux-gnu
checking target system type... i586-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
configure: autobuild project... fetchmail
configure: autobuild revision... 6.3.8
configure: autobuild hostname... galileo-desktop
configure: autobuild timestamp... 20070705-141508
checking for a Python interpreter with version >= 2.0... python
checking for python... /usr/bin/python
checking for python version... 2.4
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.4/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.4/site-packages
checking for gawk... (cached) mawk
checking for gcc... no
checking for cc... no
checking for cl.exe... no
[COLOR=Red]configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.[/COLOR]

---

### Post by andrew.46 on 2007-07-05
Hi,

 Might be a simple solution here:

> **Cheves said:**
> Thank you for your help Andrew, but I'm still getting problems here:

[COLOR=Red]configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.[/COLOR]

I suspect that you have no compiling tools. You need:

```
sudo apt-get install build-essential checkinstall
```

Then all will be well. If you are new to compiling have a quick read at:

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

 and be prepared to hunt dependencies.

                 Andrew

---

