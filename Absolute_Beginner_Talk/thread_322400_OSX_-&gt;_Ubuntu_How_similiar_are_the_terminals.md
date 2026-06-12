---
title: "OSX -&gt; Ubuntu: How similiar are the terminals?"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by crios on 2006-12-20
I'm seriously looking into buying a laptop to load up with Ubuntu. I'm a Mac user and can navigate around in the terminal to do fairly simple "copy and paste" type of stuff. (I've installed mediawiki on my machine and now use it as my personal notepad. That's my level of terminal use) 

How similiar are commands in the Ubuntu terminal to the OSX terminal? I don't really know a whole lot about Linux (but I'm learning) but from what I understand it's pretty similiar to Unix. Would the commands that I know (basic stuff: ls, cd, nano, sudo, rm, etc...) in OSX cross over to Ubuntu? 

Is the system organized in a simliar way? Is there a system library and then user librarys? 

Finally, (sorry for all the questions) if I wanted to install mediawiki or some other php, mysql, apache application, would it be pretty similiar to my experience in OSX. What I mean to say, would it be as simple as going to the php, mysql, apache websites, downloading, doubleclicking and then going through the installer and viola, they are up and running on your computer? Are the configuration files in roughly the same place so that I can go into (for example), etc/httpd/httpd.conf to alter apache and make changes?

Thanks
Chris

---

### Post by ButteBlues on 2006-12-20
> How similiar are commands in the Ubuntu terminal to the OSX terminal? I don't really know a whole lot about Linux (but I'm learning) but from what I understand it's pretty similiar to Unix. Would the commands that I know (basic stuff: ls, cd, nano, sudo, rm, etc...) in OSX cross over to Ubuntu? 

Yup.

Is the system organized in a simliar way? Is there a system library and then user librarys? 

> Finally, (sorry for all the questions) if I wanted to install mediawiki or some other php, mysql, apache application, would it be pretty similiar to my experience in OSX. What I mean to say, would it be as simple as going to the php, mysql, apache websites, downloading, doubleclicking and then going through the installer and viola, they are up and running on your computer? Are the configuration files in roughly the same place so that I can go into (for example), etc/httpd/httpd.conf to alter apache and make changes?

Even easier.

Open Synaptic, Edit > Mark Packages by Task.

Select LAMP server and install it. This should install Apache2, PHP5 and Mysql automatically. :) Default webdir should be /var/www

Apache stuff is in /etc/apache2, iirc.

---

### Post by cryogen on 2006-12-20
> **crios said:**
> I'm seriously looking into buying a laptop to load up with Ubuntu. I'm a Mac user and can navigate around in the terminal to do fairly simple "copy and paste" type of stuff. (I've installed mediawiki on my machine and now use it as my personal notepad. That's my level of terminal use) 

How similiar are commands in the Ubuntu terminal to the OSX terminal? I don't really know a whole lot about Linux (but I'm learning) but from what I understand it's pretty similiar to Unix. Would the commands that I know (basic stuff: ls, cd, nano, sudo, rm, etc...) in OSX cross over to Ubuntu? 

Is the system organized in a simliar way? Is there a system library and then user librarys? 

Finally, (sorry for all the questions) if I wanted to install mediawiki or some other php, mysql, apache application, would it be pretty similiar to my experience in OSX. What I mean to say, would it be as simple as going to the php, mysql, apache websites, downloading, doubleclicking and then going through the installer and viola, they are up and running on your computer? Are the configuration files in roughly the same place so that I can go into (for example), etc/httpd/httpd.conf to alter apache and make changes?

Thanks
Chris


I'm using OSX on my laptop and a G3 with Ubuntu 6.10 for my file server.  My experience has been that by and large the commands between the two systems are quite similar.  In the cases where there is a difference, it's pretty easy to figure out either by the man page or google.  So yes, the commands cross over in a great many cases.

That said, the largest difference I've found is using DarwinPorts for installing software on OSX as opposed to apt-get.  The command line syntax is a little different and DarwinPorts tends to complain a little more than apt-get, but again it's straightforward to figure out.  If you use fink, the two installers are essentially identical (fink uses apt-get) so there's little or nothing to change.

The amount of written documentation for Ubuntu is immensely helpful toward learning how to use it.  After following a few cut-and-paste HowTo's you understand some of the basics and can easily branch out from there.  If some file from Ubuntu isn't in the same place in OSX, command-f will solve that for you.

If you figured out the terminal in OSX in the first place you've gone a long ways.  I wouldn't sweat using Ubuntu.  Go for it!

--cryogen

---

### Post by crios on 2006-12-20
This is a little off topic, but what is the advantage to using LAMP (or MAMP on a Mac) over seperate installations of A, M, P (other than LAMP (or MAMP) being a singel install)?
When I was first learning this stuff people swore by MAMP, but I could not get it working. It wasn't until I installed A, M, P seperately that I was finally able to get Mediawiki up and running. I think if I tried it now I could probably get it to work, but would it really be worth it?

Chris

---

### Post by cryogen on 2006-12-20
> **crios said:**
> This is a little off topic, but what is the advantage to using LAMP (or MAMP on a Mac) over seperate installations of A, M, P (other than LAMP (or MAMP) being a singel install)?
When I was first learning this stuff people swore by MAMP, but I could not get it working. It wasn't until I installed A, M, P seperately that I was finally able to get Mediawiki up and running. I think if I tried it now I could probably get it to work, but would it really be worth it?

Chris

The idea behind LAMP is that everything is already configured to work together so it cuts down on the post-install config and bashing-your-head-on-the-desk you have to do.

--cryogen

---

### Post by lostguru on 2006-12-24
well the shell (bash) is exactly the same between them

they do act the same for the most part outside of some apps

obviously some things work in one that don't in the other but in my experience most of the cmd line tools are EXACTLY the same, or any OSX specific differences are noted in the man page on osx

if you are adventurous you can even install most any linux (ubuntu) app you want on osx provided your willing to try hard enough

but really compatibility is great. i use my osx laptop to do sys admin work on a large educational lab of linux boxen and it works great, and most everything applies to ubuntu

---

