---
title: "How can I make ddclient run as a daemon?"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by d.j.schroeder on 2006-10-26
I have installed ddclient several times.  It seems ok but clearly is not running as a daemon, or at all.  

I don't know much about linux, what can I do to make it actually do something?  I have only used the package manager to install it, which prompts for things like the service you want the IP address updated, your web site name, the ethernet adapter to use etc.  But after that it never actually does anything.

If I go to dyndns with a web browser and manually type in the address I get from ifconfig I am able to reach my site from other computers no problem, until my IP address changes.  That's how I know that ddclient isn't actually doing anything.

Any help would be appreciated.

---

### Post by mitch.c on 2006-10-26
> **d.j.schroeder said:**
> I have installed ddclient several times.  It seems ok but clearly is not running as a daemon, or at all.

I don't know much about linux, what can I do to make it actually do something?  I have only used the package manager to install it, which prompts for things like the service you want the IP address updated, your web site name, the ethernet adapter to use etc.  But after that it never actually does anything.

Are you sure it's not running? If you installed the ddclient package, an init script is installed that should start ddclient as a daemon. At a shell prompt, type:
```
user@ubuntu:~$ sudo /etc/init.d/ddclient status
```
What does that report? If it's not running, try:
```
user@ubuntu:~$ sudo /etc/init.d/ddclient start
```
Any luck?
> **d.j.schroeder said:**
> If I go to dyndns with a web browser and manually type in the address I get from ifconfig I am able to reach my site from other computers no problem, until my IP address changes.  That's how I know that ddclient isn't actually doing anything.
Maybe you don't have ddclient configured properly. Could you explain your networking setup (i.e. direct connect to Internet? Router in front of host? Using port fowarding?), and post a copy of ddclient.conf (less your dyndns account info of course).

---

### Post by d.j.schroeder on 2006-11-03
First, sorry it has taken me so long to get back to this.  I've been out of town.

I tried:

 sudo /etc/init.d/ddclient status
Password:
 * Usage: /etc/init.d/ddclient {start|stop|restart|force-reload}


So it looks like I'm not allowed to ask for status.

I tried the start command as you suggested and it returned:

 * Starting dynamic DNS service update utility...                        [ ok ]

So it looks like it is started.

However, I looked at the terminal view when it installed originally and it had returned the same thing, indicating, I thought, that it was starting then too.

dyndns.com still reports that there has been no update since the one I manually typed in a week or so ago.  All I can think of to do now is to wait and see if it updates when my IP changes.  Any other thoughts?

---

### Post by d.j.schroeder on 2006-11-03
Since the status command didn't work I played around a little with start and stop.  If you tell it to stop when you've already stopped it the system returns with a message that it couldn't find the process.  So I restarted the  computer and gave it the stop command and it did not return the error message.  I started it again, but the point of this whole ramble is that it appears that it was in fact running to begin with.

So my new question is what do I need to do to troubleshoot from here?

Thanks

---

### Post by d.j.schroeder on 2006-11-16
I finally got this problem solved and thought I would post the solution.

The host I was trying to update was a custom host at dyndns.  This has to be specified in the configuration file.  The package manager never asks this so it wasn't specified and dyndns would not accept the update.  I added cutom=yes to the ddclient.conf file just before the host name and now it is updating.

---

### Post by bsh on 2007-10-30
i had similar issue.
definde my wan ip address on the dyndns website, by hand, and it worked. so i thought, i'd install ddclient. installed tt about a month ago, and i believed it was working, since i could reach my site using a domain name.
but in fact, it was only working because i entered my ip address on the dyndns website manually and my ip didn't change since then. ddclient did not update it.
i found in the logs, that ddclient could not connect to "members.dyndns.COM" so i changed this to "members.dyndns.ORG" and it works now.
the default server is wrong. :(

---

### Post by darkazurka on 2008-06-16
Thank you very much! It helped me a lot. After > user@ubuntu:~$ sudo /etc/init.d/ddclient status it said : "NOT RUNNING", after > user@ubuntu:~$ sudo /etc/init.d/ddclient start it said: > To run ddclient as a daemon, please set run_daemon to 'true' in /etc/default/ddclient 
   ...done.

---

