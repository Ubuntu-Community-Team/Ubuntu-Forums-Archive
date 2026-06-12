---
title: "Newbie Fun w/Ubuntu"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by firestorm_v1 on 2007-11-01
Ok, well here we go.  After needing to upgrade my badly outdated RedHat 7.3 server, I asked my local LUG and they recommended to me Ubuntu. I was considering going to Fedora Core 4, but thought I'd try something new.  I downloaded and installed Ubuntu Server and Ubuntu Workstation in VMware sessions.  The installs went off without a hitch and I'm supposed to have installed a LAMP server on the Ubuntu server, and the standard desktop on the workstation version but now I'm at a loss.


On the server:
where's /etc/httpd/conf/httpd.conf?  (apache configuration)
where is /var/www/html? (HTML files for apache webserver)

On both systems:
Where is /etc/sysconfig/network-scripts/ifcfg-ethX (network interface configuration) Right now I am set up with a DHCP configuration, but how do I set it up as a static?
where is /etc/inittab and how do I go about finding/changing the default runlevel?
What is the name of the package manager?  I used to do apt-get install (package), has that changed or do i need to do something else now?

I haven't used any Debian related distro in ages, so forgive me in advance if I ask some really newbish questions.

---

### Post by trak87 on 2007-11-01
> **firestorm_v1 said:**
> where's /etc/httpd/conf/httpd.conf?  (apache configuration)

/etc/apache2

> where is /var/www/html? (HTML files for apache webserver)

I believe you just stick your index.html in /var/www/

---

### Post by defrex on 2007-11-01
And *apt-get install package-name* is right. Well, *sudo apt-get install package-name* is probably more accurate.

---

### Post by x1a4 on 2007-11-06
> **firestorm_v1 said:**
> where's /etc/httpd/conf/httpd.conf?  (apache configuration)

/etc/apache2/
It contains httpd.conf for backwards compatibility but you should use apache2.conf
see the Apache documentation for details.

> where is /var/www/html? (HTML files for apache webserver)

/var/www/

> where is /etc/inittab and how do I go about finding/changing the default runlevel?

boot scripts are in /etc/init.d/
they are symlinked in /etc/rc#.d/ (where # = runlevel #)
the symlink naming convention is very important
essentially, the links to scripts you want to start are named 'S#scriptname' (where # = the order in which to start it.
links to scripts you want to kill for a given runlevel are named 'K#scriptname'
the #s have to be from 01 - 100.  if a script you want to start begins with, say, S20 the kill link has to be K80
see the README file in either of the /etc/rc#.d/ directories for details

You can also place your custom scripts in /etc/rc.local and set its executable bit to enable it.

Also, I'm not 100% on this, but I'm quite sure Ubuntu will honour an /etc/inittab file if you create one.  
Anyone try it? 

> What is the name of the package manager?  I used to do apt-get install (package), has that changed or do i need to do something else now?

You can use 'apt-get' or 'dpkg' (Debian's version of FreeBSD's 'pkg') but I would recommend you use 'aptitude' as it has better dependency handling.  If you want a GUI use Synaptic which is an apt-get interface.  Aptitude without options will run a curses interface.

---

### Post by nickbooker on 2007-11-06
> **firestorm_v1 said:**
> Where is /etc/sysconfig/network-scripts/ifcfg-ethX (network interface configuration) Right now I am set up with a DHCP configuration, but how do I set it up as a static?

You're looking for /etc/network/interfaces.  Look at the man page for detailed instructions on using it:--
```
man interfaces
```

What you need in /etc/network/interfaces is:--

```

auto eth0
iface eth0 inet static
address xxx.xxx.xxx.xxx
netmask yyy.yyy.yyy.yyy
gateway zzz.zzz.zzz.zzz

```

Of course, substitute your ethernet interface as necessary; and if you don't want the interface configured at boot remove the "auto" line.

Whatever you do, don't remove these lines lest you break the system:--
```
auto lo
iface lo inet loopback
```

---

### Post by firestorm_v1 on 2007-11-18
Well, it's been a week since anyone responded, and man do I feel like a 'tard.

I reinstalled the whole OS and did some new stuff to it, but couldn't find any of the server apps.

I got the network configuration thing figured out, it sure does help to read the effin man page. :P

The root reason why I couldn't do anything with it was because I didn't realize that when you select "Install to Hard Drive" (whatever the first option says) taht it installs a base system, but nothing else.  No SSH, no Apache, nothing.    Boy did I make my life easier when on myt 3rd attempt, I selected "Install a LAMP server".

*sigh*.  That made me feel real smart...   But at least I learned and got it working...

Thanks so much for the help! I appreciate it.

---

### Post by ByteJuggler on 2007-11-18
Hey dude, it happens with the best of us, so don't be too hard on yourself! :-)

---

