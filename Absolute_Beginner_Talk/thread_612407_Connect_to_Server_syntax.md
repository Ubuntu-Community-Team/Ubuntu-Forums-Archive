---
title: "Connect to Server syntax?"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by xyloweb on 2007-11-13
I have tried "Connect to Server", but cannot successfully connect.
I typed in what I thought were the correct parameters, and I see the server name show up on my File Browser, but when I double-click on it, I get the spinny thing (waiting...), and it never returns with a file list.

Details:
It is an FTP server, which requires a password, and the user name must include the server name (e.g. "something@myserver.com").  I think that an active FTP connection is required.

I have input:
Service Type: FTP (with login)
Server: myserver.com (should it be [ftp://myserver.com/](ftp://myserver.com/) ?)
User Name: [email]myname@myserver.com[/email] (or should it be just 'myname'?)

I've tried various combinations, but no luck.  I've looked in the Ubuntu manual, but there are no examples.
Ideas/suggestions?

I am very experienced with Windows and the internet, but just installed Ubuntu 7.10 a week or so ago.  Everything is working fine, otherwise.

P.S. I am trying to get this working because I see that Bluefish has no FTP services, so it looked to me that this was the best way to access my server files and do web development.  On Windows, I use Dreamweaver.

---

### Post by some_random_noob on 2007-11-13
You may have mucked up the username thingy - It shouldn't have the domain name on the end. Also, you shouldn't need to do [FTP://mydomain.com;](FTP://mydomain.com;) because you have already selected FTP as the connection method.

I've had trouble with this in the past... it's one of those things that I don't figure out until I go for a walk and then come back :)

---

### Post by xyloweb on 2007-12-20
I thought I would post what I have figured out.
My FTP server does indeed require the whole site name as part of the user name, but you can use a '+' instead of '@'.  Therefore, I would use myname+myserver.com as the user name.
(FYI: I read somewhere that percent '%' would also work, but I got a syntax error.)
In the end, what gets sent to the FTP site is:
[ftp://myname+myserver.com@myserver.com](ftp://myname+myserver.com@myserver.com)

That was just part of my problem.

The other problem was that I was using the master user name for the site, and I needed to be using a subordinate user name.  The reason is that the master user logs in to a directory above the web site root, in order to be able to upload executable content (e.g. Perl).  So, when a relatively simple application tries to connect to the server with that user name, it gets confused about what directory it is in etc. because of the symlinks (I believe) to the real web directories.
I haven't actually successfully done this yet (I'm moving on to other things), but I believe it is true.

I hope that helps someone else.
:)

---

