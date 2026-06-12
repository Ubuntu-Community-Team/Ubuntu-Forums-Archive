---
title: "Slow internet after moving to wireless"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by sefs on 2006-05-10
Hi initially I was using a wired network, and things then were snappy.  

When I upgraded the Breezy 5.10 to wireless.  The internet slowed down.

I believe its because of some kind of resolving problem and I do not know why it is occuring.

I find that if i manually change resolv.conf and add some more name servers of my ISP then things go back snappy again. That is.

Initially in my resolv.conf I had

#slow performance setup
nameserver my.router.ip

and i change this to 

#fast performance setup
nameserver my.isp.nameserver.1
nameserver my.isp.nameserver.2
nameserver my.router.ip

I have aslo installed resolvconf from synatic.

in my /etc/network/interfaces I have.
dns-nameservers my.isp.nameserver.1 my.isp.nameserver.2 my.router.ip

... along with the other stuff.

Now the problem is this.  When ever i shut down or restart.... resolv.conf gets overwritten back to what it originally was... that is

it just have in the single namesever entry, namely
nameserver my.router.ip

and the two additional dns entries i updated with manually has disappeared.

How do I get reslov.conf to keep what I put in there.

Thanks muchly :)

---

### Post by DSn0wMan on 2006-05-10
[QUOTE=sefs]Hi initially I was using a wired network, and things then were snappy.  

When I upgraded the Breezy 5.10 to wireless.  The internet slowed down.

I believe its because of some kind of resolving problem and I do not know why it is occuring.

I find that if i manually change resolv.conf and add some more name servers of my ISP then things go back snappy again. That is.

Initially in my resolv.conf I had

#slow performance setup
nameserver my.router.ip

and i change this to 

#fast performance setup
nameserver my.isp.nameserver.1
nameserver my.isp.nameserver.2
nameserver my.router.ip

I have aslo installed resolvconf from synatic.

in my /etc/network/interfaces I have.
dns-nameservers my.isp.nameserver.1 my.isp.nameserver.2 my.router.ip

... along with the other stuff.

Now the problem is this.  When ever i shut down or restart.... resolv.conf gets overwritten back to what it originally was... that is

it just have in the single namesever entry, namely
nameserver my.router.ip

and the two additional dns entries i updated with manually has disappeared.

How do I get reslov.conf to keep what I put in there.

Thanks muchly :)[/QUOTE]


I originally had the same problem, until I added a search domain to my settings.

In the Network settings GUI you can add a search domain on the DNS Tab.

Hopefully that helps.

---

### Post by sefs on 2006-05-10
Can you elaborate as to what a search domain is?

---

### Post by sefs on 2006-05-10
Update: 

following a lead in another thread about some sort of bug... see below

***
So I've figured out the problem with resolvconf. I filed a bug report against the package. The issue is that the resolvconf link in the /etc/rcS.d directory (S07resolvconf) is executing before the procedure that sets up /dev/shm (S11mountdevsubfs), therefore the link for /dev/shm/resolvconf fails to get created. I modified the resolvconf symlink to be S12resolvconf (to force it to load after S11moutndevsubfs) and it works fine now.
***

my resolvconf in this directory was S38resolvconf and I changed it to load last after the last thing i saw in this directory S75sudo...so i mv S38resolvconf to S76resolvconf

This had partial results where indeed when the file loads it kept the first two values i had put in sytem -> administration -> networking befroe rebooting....but i think i am having a probably with the SXX part I think its loading too late as during the boot up process... when it tries to connect to the ubuntu time server it fails very quickly.  So i think i have to put it at something earlier than S76.... does anyone know where....
S38 was too early and S76 being too late
my list of things in /etc/rcS.d btween S38 and S76 are ....


S38pppd-dns     
S39dns-clean
S39ifupdown
S40hostname.sh
S40hotplug
S51ntpdate
S55bootmisc.sh                   
S55urandom

---

### Post by DSn0wMan on 2006-05-12
[QUOTE=sefs]Can you elaborate as to what a search domain is?[/QUOTE]

just the domain name of your ISP. 

For me it's san.rr.com

FYI - syncing time with ubuntu allways fails on startup for me, but other than that everything works well.

---

