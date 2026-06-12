---
title: "Desktop + LAMP - Perl installation guidance needed"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by Winterdream on 2007-04-03
Yesterday I tried to install Ubuntu Server and then add the desktop - that was a real failure so I've stepped back and changed direction.  I've installed Ubuntu Desktop successfully - and it's wonderful!  I've disabled ipv6 and now I have good internet access.

Next, I installed Apache and configured it to look at localhost.  I tested it with a simple HTML page and it works!  :) 

I think my next step is the Perl installation (I'm not interested in PHP now) and I think I can install MySQL later.  Is that correct?

Is there an easy way to install Perl?  I've searched the documentation but have not found it, if it exists.

Many thanks for any guidance!

---

### Post by az on 2007-04-03
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

I beleive that perl is already installed.  You would need the libapache2-mod-perl* packages.


[http://packages.ubuntu.com/edgy/perl/libapache2-mod-perl2](http://packages.ubuntu.com/edgy/perl/libapache2-mod-perl2)

---

### Post by Braken on 2007-04-03
I went along the Ubuntu server root and then added the desktop, I actually found it quite painless.
I used apt-get install ubuntu-desktop and that installed everything i needed to get a workign desktop

Atm I am trying to test going from a normal server build and then go to lamp. I found someone suggesting the command apt-get install ubuntu-lamp, either its obsolete and not used in edgy or, its someone leading me on a wild goose chase :)

---

### Post by Winterdream on 2007-04-03
> **az said:**
> 
I beleive that perl is already installed. 

You're right !  I spent half a day looking for something that was already there.  Oh well, sometimes learning by bashing my head against a wall works .... and sometimes it just gives me a headache.

Thanks for taking the time to reply.  :)

---

### Post by Winterdream on 2007-04-03
> **Braken said:**
> I went along the Ubuntu server root and then added the desktop, I actually found it quite painless.

I tried that and ended up without the desktop - some stuff either didn't get downloaded or got corrupted or something.  But I think the reason for it was that "ipv6" thing - but with only the server install, I didn't realize that I had an internet problem.  Once I started over with the desktop, the internet problem was obvious and searching led me to the "disable ipv6" advice.

And now that much works !  :) 

You might find the HowToForge article helpful - [here]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06")
if you haven't already found that...

---

### Post by az on 2007-04-03
> **Winterdream said:**
> I tried that and ended up without the desktop - some stuff either didn't get downloaded or got corrupted or something.  

It may have been that you needed the desktop kernel for your hardware - there is a lot of hardware that the server kernel doesn't like.

Installing the base server system and then installing the
ubuntu-desktop and linux-generic
packages should work for everybody.

---

