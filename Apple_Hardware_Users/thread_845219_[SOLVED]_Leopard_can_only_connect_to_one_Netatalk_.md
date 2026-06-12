---
title: "[SOLVED] Leopard can only connect to one Netatalk server at a time"
date: 2008-06-30
forum: Apple Hardware Users
---

### Post by fondle-em on 2008-06-30
I'm stumped.  I currently have three Hardy machines running custom-compiled Netatalk servers, and one Mac running Leopard.  One of these Hardy boxes isn't mine, it's destined for a Mac-dominated network environment - which already has one Ubuntu box runnning Netatalk.

The problem is that when I connect to one of the boxes, doesn't matter which, OS X thinks that any other Netatalk box that I try to connect to is  the *first* one, resulting in a whole lot of nothing; in Leopard's eyes the share is already mounted, so there's nothing to do.  This doesn't affect an actual Macintosh running its own AFP server; I can mount that, and then any one Netatalk share without issue.  Attempts to mount additional Netatalk shares result in Leopard getting confused and telling me that the Netatalk share I'm trying to mount is actually the one I've already mounted.  It should be mentioned that Netatalk is configured very simply, just one share per machine and it's the home directory.

I've done the bit from the Netatalk wiki where you edit /etc/hosts so that each machine has a unique first line, to no avail.  I seem to remember that trick working to solve a similar issue when I was running Tiger and Gutsy, but it's not working now.  What in the world am I doing wrong?  Is this a Leopard issue or a Netatalk/Hardy issue?

---

### Post by cyberdork33 on 2008-06-30
I am not that familiar with AppleTalk, but don't the machines need to be in the same "zone" or something?

---

### Post by tiresia on 2008-07-01
I guess, this page can help you to solve your problem:

[http://netatalk.sourceforge.net/wiki/index.php/MultipleServers?PHPSESSID=c2c5a3fd64717159126671c24464ba81](http://netatalk.sourceforge.net/wiki/index.php/MultipleServers?PHPSESSID=c2c5a3fd64717159126671c24464ba81)

---

### Post by fondle-em on 2008-07-08
Thanks all for your help, but I figured out what to do or so it seems.

The Netatalk wiki says to reverse the order of the first two lines of /etc/hosts.  With Leopard this doesn't work.  The IP ADDRESS in that line had to be changed for the Leopard AFP client to differentiate between the Netatalk servers.

```
127.0.0.1               localhost.localdomain localhost
<xxx.x.x.1>          hostname.domainname hostname
```

becoming

```
<xxx.x.x.3>          hostname.domainname hostname
127.0.0.1               localhost.localdomain localhost
```

worked for me, where each Netatalk server on the network should apparently have a unique entry in that line.

---

### Post by cyberdork33 on 2008-07-08
please mark thread as solved. (Hint: "Thread Tools" menu)

---

### Post by ratthing on 2008-07-16
Geez, haven't they every heard of the library functions gethostbyname() and gethostbyaddr()?  I'm not a fricking developer but even I know you don't look at the hosts file for that stuff when you're writing software.

Anyway, thanks to the poster who found that in the netatalk wiki. I am *finally* able to see my xubuntu TM NAS *and* my xubuntu media NAS.  It's pretty amazing what a couple of 900Mhz Athlons with 512MB each and some big honking disks can handle. :)

=RT=

---

### Post by cyberdork33 on 2008-07-17
> **ratthing said:**
> Geez, haven't they every heard of the library functions gethostbyname() and gethostbyaddr()?  I'm not a fricking developer but even I know you don't look at the hosts file for that stuff when you're writing software.
Since you seem to understand it, maybe you can submit a patch ?

---

