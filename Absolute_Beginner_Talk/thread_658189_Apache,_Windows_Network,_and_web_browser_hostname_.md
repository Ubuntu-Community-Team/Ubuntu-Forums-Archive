---
title: "Apache, Windows Network, and web browser hostname access"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by Delsphynx on 2008-01-04
Hello everyone,

First of all, amazing resource that is present here.  I've learned a lot from this site with my first install of Ubuntu, and really only second foray into Linux at all.  

What I have is Ubuntu 7.10 running with the LAMP pieces all installed and working properly.  I've done a lot of digging and configuring, and have things playing nicely for the most part with the large corporate Windows network where this box is installed - except for one thing that is:

I am unable to access the web pages hosted by Apache by using the hostname of the Ubuntu box.  I can access the page through the IP address just fine (DHCP is being used here), and have Samba and WinBIND running so I'm able to ping the hostname from the command prompt in Windows with no issue.  I can even get the browser in Ubuntu to access pages hosted by Windows machines through hostnames.  It's just that I can't seem to get IE on Windows to access the apache server directly.  

Any suggestions or pointers for things to try with this?  Are there more settings that need to be made for the DNS information being sent to the corporate network?

---

### Post by reckless2k2 on 2008-01-04
is your hostname displayed properly in /etc/hosts? you might want to cat it for us so we can see it. also, DHCP on a server in general is a no no. hahaha. that is what is probably causing your issue. 

you may have to list the name in virtual hosts and restart apache so everyone can "find" it by hostname since you have DHCP.

---

### Post by Delsphynx on 2008-01-04
Thanks for the fast response!

The /etc/hosts contains two entries, aside from the ip6 stuff:

127.0.0.1 localhost
127.0.1.1 ubuntubox

Yeah, DHCP doesn't make a lot of sense probably.  The main issue though is my like of familiarity with the rest of the Windows Server network, which I don't have access to (this machine is being set up for a testbed purpose, so it's not being added to the domain, etc. etc.)  If I set a static IP address outside the range will it be left alone by the network, but still be allowed access?  (This is where my lack of real in-depth understanding of networking starts to show...)

With some similar test boxes using Windows and IIS though, access of host names in the browser works just fine, even though they acquire via DHCP as well.  

I have touched absolutely nothing right now with apache and virtual hosts.  Everything is "stock" for lack of a better word, and when I access the site I'm just presented with the directory tree.  I can then append /myphpadmin to the address and get to that just fine, too.  I'm just trying to get that done via hostname and not IP with the potential of the IP address changing eventually...

---

### Post by reckless2k2 on 2008-01-04
well you definitely need a hosts edit or two to get this working right/better. take a look at this page and it should help you:

[http://www.howtoforge.com/perfect_server_ubuntu7.10_p3](http://www.howtoforge.com/perfect_server_ubuntu7.10_p3)

you want it looking something like this:
```
127.0.0.1       localhost.localdomain   localhost
192.168.0.100   server1.example.com     server1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

then you have to do the hostname gimmick:
```
echo server1.example.com > /etc/hostname
/etc/init.d/hostname.sh start
```

if you are really running into a DHCP issue, then you will have to use the virtual host mod for apache. it's crazy simple to add the virtual host to fix the call when it's made. 

the 127.0.1.1 is doing nothing for you. hahaha.

---

