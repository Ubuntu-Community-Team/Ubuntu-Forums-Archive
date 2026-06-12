---
title: "lost in ubuntu land"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by dbbd1 on 2006-07-19
actually maybe i should say lost in lamp land,

ok here is my trouble and questions. 
I installed ubuntu 6.06 lts .. I tried to follow along with the perfect setup but the version I have dont have a program called proftpd .. to make a long story short I found the program but have no idea how to add it to the programs, I have the server installed and I also have the desktop installed..  I found the proftpd in the ubuntu downloads and downloaded it.. to the desktop, it said open and install as I was downloading it and it did something  but it did show up in the services at start up deal. 

ok now the back ground.. on the install of the main ubuntu program that all went flawless(i did not have to do a thing except choose a few options) I even figured out.. well fumbled my way thru setting up the apache2..(I think) I say I think because I can access the ip thru puddy now and also if I type the ip into a browser. a page i made.. yea me!!.. but it wont show up when I try the domain name.. I think the dns has to be installed.. 
so my question is..
how do I add a tar.gz to the package handler, or how do I install the proftpd from the tar.gz
and..
how do I add the dns or check the config?
keep in mind I was and still do have trouble even removing a file, or using any commands, exact commands would be great.. and thanks in advance.

---

### Post by sean_ on 2006-07-19
> **dbbd1 said:**
> actually maybe i should say lost in lamp land,

ok here is my trouble and questions. 
I installed ubuntu 6.06 lts .. I tried to follow along with the perfect setup but the version I have dont have a program called proftpd .. to make a long story short I found the program but have no idea how to add it to the programs, I have the server installed and I also have the desktop installed..  I found the proftpd in the ubuntu downloads and downloaded it.. to the desktop, it said open and install as I was downloading it and it did something  but it did show up in the services at start up deal. 

ok now the back ground.. on the install of the main ubuntu program that all went flawless(i did not have to do a thing except choose a few options) I even figured out.. well fumbled my way thru setting up the apache2..(I think) I say I think because I can access the ip thru puddy now and also if I type the ip into a browser. a page i made.. yea me!!.. but it wont show up when I try the domain name.. I think the dns has to be installed.. 
so my question is..
how do I add a tar.gz to the package handler, or how do I install the proftpd from the tar.gz
and..
how do I add the dns or check the config?
keep in mind I was and still do have trouble even removing a file, or using any commands, exact commands would be great.. and thanks in advance.

[http://ubuntuguide.org/wiki/Dapper#FTP_Server](http://ubuntuguide.org/wiki/Dapper#FTP_Server)

[http://ubuntuguide.org/wiki/Dapper#Apache_HTTP_Server](http://ubuntuguide.org/wiki/Dapper#Apache_HTTP_Server)

---

### Post by dbbd1 on 2006-07-19
you are the man! 
thanks very much.. those look like what I need! :D

---

### Post by dodger on 2006-07-19
most applications in ubuntu are available in so called "packages", which can be installed using a package-manager. ubuntu uses synaptic. you could start by searching the wiki pages, the forums or the ubuntu-documentation that is available from the default firefox-startpage after a fresh install for information on apt-get install *packagename*, synaptic or generally on installing software in ubuntu.

have fun.

---

### Post by sean_ on 2006-07-19
> **dbbd1 said:**
> you are the man! 
thanks very much.. those look like what I need! :D Glad to help.

---

