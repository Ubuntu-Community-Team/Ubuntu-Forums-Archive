---
title: "SSL News Reader"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by dirtblack on 2007-09-12
I'm looking for  a news reader like news rover or newsbin.  Something that can put together posts such as yenc.  I need it to have SSL encryption on it for various reasons.  I'd like it to have a search so I can search for files that are needed.  I've tied pan but it doesn't use SSL nor have a search.  It's just basically a newsreader.  Is there anything out there like this?

---

### Post by linuxwizard on 2007-09-12
Look through this see if you can find what you want

[http://www.newsreaders.com/unix/clients.html](http://www.newsreaders.com/unix/clients.html)

---

### Post by toasterofirony on 2007-09-12
Why not go with Google Reader?

---

### Post by chrome307 on 2007-09-12
I'm using KLibido for downloading Binaries at present and then PyPar2 for the Repair/Creation of PAR files

[IMG]http://i4.tinypic.com/6fa8eqf.jpg[/IMG]
[B][COLOR="Red"]
OR[/COLOR][/B]

[IMG]http://i5.tinypic.com/4kv95as.jpg[/IMG]

---

### Post by dirtblack on 2007-09-15
Thanks guys I do appreciate your input.

---

### Post by yabbadabbadont on 2007-09-15
Another option is to use Pan with stunnel4.

---

### Post by Badtothebone on 2007-11-14
I use klibido with stunnel4

Install stunnel4 via synaptic or adept

====

in /etc/stunnel ->  edit stunnel.conf  ->  nano stunnel.conf

client = yes
foreground = yes
debug = 7 

[nntp]
accept = localhost:119
connect = yournewshost.com:563

====

In klibido use the following server settings

server localhost 
port 119

start stunnel4 as follows

sudo stunnel4 stunnel.conf

You need to use root to start stunnel4 if using port 119

---

### Post by mangurt on 2007-11-14
I'm currently using hellanzb or sabnzbd for downloading (there are shell scripts posted to set these up).  Both support SSL as long as you know what port to connect to for SSL (and if your newsgroup provider supports SSL).

[http://ubuntuforums.org/showthread.php?t=369371&highlight=hellanzb](http://ubuntuforums.org/showthread.php?t=369371&highlight=hellanzb)

[http://ubuntuforums.org/showthread.php?t=169749&highlight=hellanzb](http://ubuntuforums.org/showthread.php?t=169749&highlight=hellanzb)

I took the liberty to post both scripts.

As for looking around newsgroups, I use binsearch.info but I feel PAN is pretty good at grabbing headers.

Hope this helps out.

---

### Post by les-h on 2008-03-23
> **dirtblack said:**
> I'm looking for  a news reader like news rover or newsbin.  Something that can put together posts such as yenc.  I need it to have SSL encryption on it for various reasons.  I'd like it to have a search so I can search for files that are needed.  I've tied pan but it doesn't use SSL nor have a search.  It's just basically a newsreader.  Is there anything out there like this?
News Rover runs in wine.  I cant yet find a complete linux replacement.  Use stunnel4 for SSL.  Hope this helps

---

### Post by dirtblack on 2008-04-22
How did you get news rover to run in wine??  I can never get it installed, it always errors out telling me some files aren't present. It's been awhile I don't exactly remember.

---

