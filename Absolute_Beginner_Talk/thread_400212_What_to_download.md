---
title: "What to download?"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by theratwonder on 2007-04-03
I have had Fedora Core 6 dual-booted with WinXP on my laptop for a few months, and I've finally had enough and decided to replace FC6 with Ubuntu, and I was wondering if someone could tell  me exactly what to install?

The main reason for having Linux on my Laptop is to run an Apache server for developing websites, even though I'm not actually planning for my laptop to be a server to anything other than itself ([http://localhost/)](http://localhost/)). So my question is, should I therefore install Ubuntu "Server Edition"?

And my other question is, what is the difference between 6.10 and 6.06 LTS, and why does it say the latter will be supported longer ("supported to 2011"), even though it has a lower version number?

Thanks.
Robin.

---

### Post by jvc26 on 2007-04-03
The server edition has no GUI, it is just the Ubuntu base install, whereas the Ubuntu install puts on the gnome desktop. 6.06 has a longer support because it is LTS (Long term support) which meant that it was super-stable and thus people could install it and use it for the long term rather than installing the new Ubuntu install every 6 months. 6.10 is the current version and 7.04, feisty is coming out in a few days. As Ubuntu has a 6 month release cycle they release LTS versions every now and again I presume for companies and stuff who dont want to put a new version on so regularly.
Il

---

### Post by hyper_ch on 2007-04-03
if you just want to run apache then you might as well do tthat in windows... I think just to run apache you don't need linux although some stuff will not work in the windows edition...

The Server edition of Ubuntu does not install a gui... so I somewhat doubt you want that... you'd be better off installing the Desktop or Alternate cd and add apache to it.

Well, ubuntu 6.06 has 5 years of support... 6.10 has not.... and 7.04 has not either....

---

### Post by Obor on 2007-04-03
Ubuntu 6.06 is long term support release (3 years on desktop and 5 for servers) 6.10 is the latest stable (normal releases are not supported for that long as there is a new version every 6 months so its unnecessary)  and 7.04 will be out on 19 April and its very nice already :) 

I would suggest that you install the Desktop version and then add the LAMP stuff on top. Which is very easy. Howto [here]("https://help.ubuntu.com/community/ApacheMySQLPHP").

---

### Post by slimdog360 on 2007-04-03
The 6.06 version is a version for businesses etc, such that they can have a stable operating system with long term support. The newer versions are for the likes of you and me. 

The server version is just a barebones install, it doesnt come with X or anything, you have to install all that via the command prompt. Hence making it a lot lighter and good for use as a server. So If I were you Id just download the live cd of either 6.10 or the newer 7.04 beta (stable is due out on the 19th) and install that.

 Probably best using the 7.04 beta since it will soon become the new standard.

---

### Post by compmodder26 on 2007-04-03
Just to add a little to the above posts.  Non-LTS releases are supported for 18 months.

---

### Post by bcrom on 2007-04-03
I ran an Apache web server with PHP and MySQL on Windows for a year and it worked fine once I had it configured.  Personally, I think Fedora does a better job with Apache because Apache comes configured and installed out of the box.  On Ubuntu it's a little more trouble to install.

---

### Post by theratwonder on 2007-04-03
Thanks guys.

So for ease of use it would certainly be better to install the Desktop edition, rather than the server edition. I imagine doing everything via command line would get rather tiresome. So there's no problem with running Apache on the Desktop Edition?

I want to use Linux for development because:

a) Apache actually works properly - most specifically XBitHack for running server-parsed pages only if they are executable, which doesn't work under windows.

b) Generall all sorts of programming and file and text manipulation is so much easier in Linux (well, Unix). It's really easy to search multiple files, most compilers/ runtime environments come already installed - most importantly Perl.... I can't think of all the reasons but Linux is just so much easier and most of the open source stuff (e.g. Apache and Perl) tends to just work better on Linux.

I guess there's no reason for me to install the LTS edition then, because I'm not a corporation, and I have no need for an Uber stable edition. I'll probably want to upgrade to each new edition straight away anyway just out of curiosity.

Thanks again guys. I think I'm gonna just wait for Feisty then and install the Desktop Edition of that.

Robin.

---

### Post by hyper_ch on 2007-04-03
No, apache runs fine on the desktop :) Just go ahead and install the desktop...

I you want apache/mysql/php afterwards installed, you may want to have a look at this here... it's a little bit more than you need but I think it's a good guide:

[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

---

### Post by theratwonder on 2007-04-03
About Fedora, I couldn't even get the web server to work properly. It did come with it pre-installed, but it kept saying "Forbidden" whatever I tried to access, whatever permissions were set to on the files, the folders, and within the Apache config. Think it might have been something to do with Fedora's SE Linux. Just gave up in the end. 

On top of that I found a lot of other annoyances with Fedora. I couldn't get my wireless card to work. Installing any kind of functional media player was extremely difficult. 

These might be general Linux issues, but I decided to give Ubuntu a try as it's a lot more popular and a lot better supported, and I'm even more encourages by the speed with which you guys reply to me. So hopefully I'll be using Ubuntu for quite a while.

Robin.

---

### Post by theratwonder on 2007-04-03
Awesome that perfect setup looks pretty good.

I do indeed want apache/mysql. Dunno about PHP. I disapprove of it for no very good reason. We just don't get on. Probably gonna use perl, but perhaps Java or Ruby or something...

---

### Post by compmodder26 on 2007-04-03
You can find Java and Ruby in the repositories, so no problems there either.

---

### Post by Lucifiel on 2007-04-03
> **theratwonder said:**
> About Fedora, I couldn't even get the web server to work properly. It did come with it pre-installed, but it kept saying "Forbidden" whatever I tried to access, whatever permissions were set to on the files, the folders, and within the Apache config. Think it might have been something to do with Fedora's SE Linux. Just gave up in the end. 

On top of that I found a lot of other annoyances with Fedora. I couldn't get my wireless card to work. Installing any kind of functional media player was extremely difficult. 

These might be general Linux issues, but I decided to give Ubuntu a try as it's a lot more popular and a lot better supported, and I'm even more encourages by the speed with which you guys reply to me. So hopefully I'll be using Ubuntu for quite a while.

Robin.
Trust me, you'll love Ubuntu and the support this forum provides. :P I had some issues that caused parts of Gnome to crash and Ubuntu to shut down and not only was everyone willing to put up with my mega-thread, they gave me plenty of advice too! :D Of course, I've also been visiting #ubuntu on freenode too 'cos it's not too fair to demand 24/7 support from the folks at the forums. 

Now, how's that for excellent support? :P 

On many tech support forums for WinXP/other Windows operating systems, the staff are often rude, unfriendly and elitist and so far, only Geektogo has provided excellent support. :D

---

