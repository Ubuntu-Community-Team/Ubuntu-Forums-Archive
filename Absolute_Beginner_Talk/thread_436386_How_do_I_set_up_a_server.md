---
title: "How do I set up a server?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by GoneWithTheWind on 2007-05-07
This is an absolutely beginner question.  What I'd like to do is set up a web page on a server, where people can enter their times for certain events, get a "score" for each one, and get placed  in the order of their total score in the rankings.  I have set up web pages through the years and think I can figure out how to put the formulas on one and get them ranked, but need to know what is needed for a  server.

I have an extra computer that is an old macintosh 6300cd.  How fast does the server computer need to be?  I have another that I'm planning to give away that iss 64 ram, and another that is used  briefly each day that is 533 mhz and 128 ram..

My broadband is 768/128.  I'd need to be on this computer when the server is working on the other one.

Could someone please outline what I need to have and learn to be able to do this.  Thanks.

---

### Post by tbg58 on 2007-05-07
I just wrote a doc on how to do a bare metal install of Ubuntu LAMP (Linux, Apache, MySQL, PHP) server for a specific open source project called ChurchInfo.

You don't have to install ChurchInfo to use the doc, which is located here:

[http://www.churchdb.org/How%20To%20Set%20Up%20ChurchInfo%20on%20Ubuntu%20LAMP%20Server.pdf](http://www.churchdb.org/How%20To%20Set%20Up%20ChurchInfo%20on%20Ubuntu%20LAMP%20Server.pdf)

(Sorry about the file name -- I'm working on correcting it.)

This will get you set up with a LAMP server.  If you're using a Linux box as your client, you can disregard the part about the Windows support tools, but Ithink you may find the install useful if you decide to install a Content Management System like Joomla, Drupal, or Typo3. These are very easy to set up and good ways to set up a site that has a marvelous look and feel that you can edit.

They are PHP packages (and the doc will explain what that means).

Once you get your web server up, just remember a couple of other things:

The Apache web server root installs by default in /var/www - you can leave it there or reconfigure Apache to use a different directory if you like.

If you use the default directory, just remember to sudo -s when you want to do file system work. This gives you root user privileges.

Hope this helps -- and do have a look at the CMS packages I referred to.  Google 'em and you can find them . They are free, open source software, and I think they might be helpful as well.

Hope this helps!  Good luck!

Rob in TN

---

### Post by Griff on 2007-05-07
> **tbg58 said:**
> I just wrote a doc on how to do a bare metal install of Ubuntu LAMP...

WOW.  That is a really nice doc you have there.  A little off topic but this will come in very handy for my own purposes.  Thanks for the post tbg58!

-Griff

---

### Post by GoneWithTheWind on 2007-05-08
Thanks much!  

I'll read through this and then post more questions.  :)

---

### Post by GoneWithTheWind on 2007-06-11
I'm back, and realize the best thing for me is to keep on going through this till it's done.  Otherwise, stopping means forgetting and losing touch with the project.  This is to be a community web page, where people can register and input their results to a ranking system for an athletic event.

So far I have (1) downloaded XAMPP from the net and have (2) written the html for a web page.  Next is to (3) set up a server on my machine (or on the net) to send my web page to, and (4) write the php so my web page gets working as intended.

Any suggestions for what I do next?   :confused:

By the way, would this server on the net work for practice?  [http://johnlvs2run.byethost7.com/](http://johnlvs2run.byethost7.com/)
 In fact if I could do the whole thing on that server it would be cool, or should I go about setting up a server on my own computer from the start?  

Thanks.

---

### Post by NeoGreen on 2007-06-11
Awesome tutorial tbg58.  That was very helpful:D

---

### Post by zvacet on 2007-06-12
[https://help.ubuntu.com/7.04/server/C/]("https://help.ubuntu.com/7.04/server/C/")

---

### Post by Yizi on 2007-08-30
I like it the tutorial its very helful also includes screenshots which helps  a lot.

---

### Post by irish_flu on 2007-08-30
> **John Rupp said:**
> 

I have an extra computer that is an old macintosh 6300cd.  How fast does the server computer need to be?  I have another that I'm planning to give away that iss 64 ram, and another that is used  briefly each day that is 533 mhz and 128 ram..

I think you'd have difficulty finding a webserver for that Mac.  Nice machine, though!  I have one of those too, with a TV card and remote.  All I use it for is watching TV.

As long as the site doesn't receive very many hits and the page is fairly lightweight, the 533MHz machine should do just fine.  The issue is going to be finding an OS that runs happily with that small amount of RAM (including running the web server).  Given those choices, I'd try to find a little more RAM for the 533MHz box and use it.

Alternatively, find yourself a really tiny Linux distro (that should require less RAM) and then run a very, very streamlined version of Apache.

> 
My broadband is 768/128.  I'd need to be on this computer when the server is working on the other one.

The 128k up is gonna bottleneck you.  Again though, as long as it doesn't get too many hits you should be fine.  Folks page won't load "instantly", but waiting is a lost art anyway.  :)

Do you already have a "static" IP address?  If not, you'll either need to get one, or else use a service (such as DynDNS) to compensate whenever your IP changes.

---

### Post by hyper_ch on 2007-08-30
I just had a small browse through it and it's nice... well done...

However two remarks:

SSH --> shouldn't it be  "openssh-server"? (never tried apt-get install ssh)

MySQL --> I think phpMyAdmin would be a lot less complicated to use for setting up mysql at all... no command line would be needed ;)

---

