---
title: "Set Hostname ?"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by thornomad on 2006-08-25
Hello,

Have done a little searching (here and on the web) and can't find a specific solution to my quandary.  

I have a Ubuntu server (command prompt only) running; I set a static IP address in my /etc/network/interfaces file.  However, I would rather access my web pages from the "hostname."  

I ran: hostname from the command line to make sure I knew what mine was ... it is "server".  However, if I use my web browser on a another system and input: "http://server.local/" nothing happens.  I can't login via SSH using that either -- I have to use the IP address.

On my mac, I am able to view the web pages via: "http://mymac.local/" ... how do I do the same on my Ubuntu server ?

Thanks,
Damon

---

### Post by Endwin on 2006-08-25
Name services can be a little confusing.

Whenever you type something on-line like say [www.google.com](www.google.com) or say in your own network like mymachine your computer tries to take that name and resolve it to an IP address (which the computer understands). For public sites it uses domain name services (DNS) to lookup the name, however in a home environment you can't do that unless you yourself have a DNS setup (a lot of work). 

However there is an easy way! Every system has what is known as a hosts file. This file is looked at first when a computer tries to resolve a name to an IP address. If it can't find it in the hosts file then it goes to the DNS servers, and if it can't find it there then it gives up.

What you need to do is edit the hosts file on each machine you want to access your server from. You will want to add a line to it like this.

```
192.168.0.10		server

```
Now where to find it. 

**Windows: **

```
C:\windows\system32\drivers\etc\hosts
```

NOTE: On some systems it may be WINNT not WINDOWS
[B]
Linux:[/B]

```
/etc/hosts
```

**Mac:**

Not sure off hand but maybe /etc/hosts since it runs off of FreeBSD you can do a search for it. 

Once you add it in you should have name resolution to your machines!

---

### Post by thornomad on 2006-08-25
Oh!  Thanks for that explanation ... I guess that does make sense, though, that it would have to be on a machine by machine basis.  Hmm ... maybe I will stick with the IP address for simplicity.

I wonder how my Mac does it because other machines on my network can reach it via the host name ... does it broadcast that info or update their host files I wonder ?

Thanks a lot -- I learned a bit today.

---

### Post by Endwin on 2006-08-25
Since I have not personally owned a Mac I cannot say what may be different. (Some mac user here may be able to explain). You can always access the local machine it has a default in the hosts file for localhost. So for example on your mac you can type localhost into the web browser and it will access your local machine. As for other machines acessing the mac machine without a modification of the hosts file... well, as far as I know it is not possible. However there could be some strange setup I am not aware of. 

As for editing the hosts file. 

Its not a big deal (I do it all the time) I have a premade hosts file that I copy to the tail of any machine on my home network so I don't have to type everything. All it takes really is a few quick minutes and then you can reference it by name whenever. One thing you may want to note though is that if you do use it have a static IP for each machine (because if the IP changes the names stop working).

---

### Post by Jerome36 on 2006-08-25
> **Endwin said:**
> One thing you may want to note though is that if you do use it have a static IP for each machine (because if the IP changes the names stop working).

Yup.  If you do this you're going to want to have your router always give the same IP address for each computer.  You can have the router reserve a specific address, for each computer, by using each machine's MAC address.  If the router gives a new/different IP, to each computer, you're going to have to always find out the new IP address.

---

### Post by Iowan on 2006-08-25
Wouldn't that be a static lease?  The clients would still be set to use DHCP - the router would just assign the same "dynamic address" to the machine based on the MAC.  A (true) static address would be set in each client.  Machine ends up with the same IP either way, but the static lease is managed from one location (the router).

Or am I confused (again)?

---

