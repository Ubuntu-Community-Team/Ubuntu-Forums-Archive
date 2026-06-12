---
title: "[SOLVED] KTorrent Port Problems"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by 449 on 2007-11-29
When I start up Ktorrent I get this error:

> KTorrent is unable to accept connections because the ports 21 to 30 are already in use by another program.

Nothing is using those ports. I specifically opened that port on my router for downloading. I know it's open because it worked fine using Windows/Utorrent. 

Also in Ktorrent I get the little yellow Exclamation triangle in the the bottom left and it says "no incoming connections(possible firewalled.) Is there a default running firewall in Ubuntu? :confused:

---

### Post by Ek0nomik on 2007-11-29
> **449 said:**
> When I start up Ktorrent I get this error:



Nothing is using those ports. I specifically opened that port on my router for downloading. I know it's open because it worked fine using Windows/Utorrent. 

Also in Ktorrent I get the little yellow Exclamation triangle in the the bottom left and it says "no incoming connections(possible firewalled.) Is there a default running firewall in Ubuntu? :confused:

It isn't wise to use such low number ports.  Port 21 is commonly used as FTP, 22 with SSH, 25 with SMTP, 23 with Telnet.

Why not just use a larger port?  I use numbers in the 20 or 30 thousands.  There's nothing wrong with that.  Also, you aren't getting incoming connections because of your port issue.  Ubuntu blocks ports by default until a program asks for the port to be open, so unless you installed firewall software, it isn't Ubuntu.

---

### Post by antharr on 2007-11-30
The previous poster is right. Do not use well-known ports(low-numbered). Use ports up in the 20 or 30 thousands.
Also, if you are behind a router, you will have to forward the ports you want to use on the router itself.

---

### Post by 449 on 2007-11-30
> **antharr said:**
> The previous poster is right. Do not use well-known ports(low-numbered). Use ports up in the 20 or 30 thousands.
Also, if you are behind a router, you will have to forward the ports you want to use on the router itself.

I've done this before... But I'm having trouble now. Here's what I currently have.

[http://img413.imageshack.us/my.php?image=screenshotea4.png](http://img413.imageshack.us/my.php?image=screenshotea4.png)

---

### Post by 449 on 2007-11-30
anyone?

---

### Post by Ek0nomik on 2007-12-03
> **449 said:**
> anyone?

Well, can't you just verify that the port is open to rule out KTorrent being the issue?

I know deluge-torrent comes with a port tester.  Otherwise Google can be a friend:  [http://www.google.com/search?hl=en&q=test+if+port+is+open&btnG=Google+Search](http://www.google.com/search?hl=en&q=test+if+port+is+open&btnG=Google+Search)

---

### Post by vikram on 2007-12-03
I am not a linux expert but most Unix and Linux systems dont allow you to use port 1-1024 unless the user is root. Ktorrent which is started as user will not be allowed to run on port numbers below 1024.

easiest way to check is to use a higher port number or run ktorrent as root (not recommended)

havent used netstat much but try

man netstat 

to get info on how to use it to get information on other applications which may already be using these ports.

---

### Post by IeU on 2007-12-10
> **vikram said:**
> I am not a linux expert but most Unix and Linux systems dont allow you to use port 1-1024 unless the user is root. Ktorrent which is started as user will not be allowed to run on port numbers below 1024.

easiest way to check is to use a higher port number or run ktorrent as root (not recommended)

havent used netstat much but try

man netstat 

to get info on how to use it to get information on other applications which may already be using these ports.

that is true, i changed here and everything worked :)

---

