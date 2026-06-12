---
title: "Easy Way To Set DNS Servers"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by Ronnie_USA on 2006-09-29
My problem is Ubuntu doesn't seem to remember the DNS Servers I setup.
Alway reverts back to My ip address.
Thats no problem for surfing, but not for trying to get updates.
I have to edit the DNS Servers, and list them again before I can check.
All I'm wanting to be able to do is reboot, and have the DNS Servers remain the same.

---

### Post by taner on 2006-09-29
try to write DNS servers on

/etc/resolv.conf

---

### Post by Ronnie_USA on 2006-09-29
I'm new at this.
So here is the dumb ?, How do I go about doing it?

---

### Post by danderson3 on 2006-09-29
if you use dhcp your resolv.conf is overwritten each time you get
a lease, such as at boot time.  you can edit /etc/dhcp3/dhclient.conf
and add lines like these:

prepend domain-name-servers 208.67.222.222;
prepend domain-name-servers 208.67.220.220;
prepend domain-name-servers 192.168.0.2;

which will cause dhclient to write these at the
top of the list ( in reverse order )  in resolv.conf
when it runs.  note that the third line here is
the ip addr of the localhost - i set my router's
dhcp server to always give my machine that ip addr - 
if I use 127.0.0.1, it is always written to resolv.conf
and the others ignored.

David

---

### Post by bigken on 2006-09-29
in a terminal type sudo gedit  /etc/resolv.conf
then type somthing like 
nameserver 195.92.195.95
nameserver 195.92.195.94
yours will differ

you could also do this in your router if it allows you too

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=16537&stc=1&d=1159535764[/IMG]

---

### Post by Ronnie_USA on 2006-09-29
Thank You to Everyone who helped its fixed now.
Again, Thank You

---

### Post by bigken on 2006-09-29
could you tell us how you fixed it as it might help others ;)

---

### Post by Ronnie_USA on 2006-09-29
By doing what danderson3 posted.
I added the lines he suggested at the end.
I changed the servers to the ones  I wanted, and everything works great now.

---

### Post by pomegranate on 2006-09-29
> **bigken said:**
> in a terminal type sudo gedit  /etc/resolv.conf
then type somthing like 
nameserver 195.92.195.95
nameserver 195.92.195.94
yours will differ

you could also do this in your router if it allows you too

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=16537&stc=1&d=1159535764[/IMG]

How do I find out my equivalent of nameserver and the IP? I can get into my router's control pages, but I don't know what I'm looking for.

---

### Post by danderson3 on 2006-09-29
your ISP should have provided that to you.  if you use dhcp, these
will be set for you by dhcp.  what we are doing here is relevant only
if you want something other/more than what dhcp provides by itself.

David

---

### Post by pomegranate on 2006-10-02
> **danderson3 said:**
> your ISP should have provided that to you.  if you use dhcp, these
will be set for you by dhcp.  what we are doing here is relevant only
if you want something other/more than what dhcp provides by itself.

David

Well, I am having unexplainable problems with apt-get updating and installing any packages, and the DNS issue is that latest thing I'm trying, because nothing else makes sense. The ISP (UK's virgin.net) haven't provided the info, is there any way to find it out?

---

### Post by danderson3 on 2006-10-02
A DNS problem would prevent access to the net by machine name,
such as 'could not resolve hostname foo.com.'  This problem 
wouldn't be specific to apt-get, it would effect all net access.

As to finding the nameserver ip addresses, either dhcp assigns
them, if you use it, or you set them.  Contact the tech support
people at your ISP or look at their web pages.

---

### Post by bigken on 2006-10-02
give [this]("http://www.dnsstuff.com/tools/ispdns.ch?name=me.smockgirl.com&type=A") a try it might help find your dns ;)

---

