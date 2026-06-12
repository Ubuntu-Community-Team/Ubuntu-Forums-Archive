---
title: "Ubuntu Proxy Server, Advert Blocker and COntent Filter"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by apjone on 2006-10-14
Ubuntu Proxy Server
-------------------

Index
------

Linux Proxy Server & Content Filter
Proxy Server Set-Up
Getting Started / OS Install
Download the latest Ubuntu Server ISO from
Setting Up The Base System - Networking
Setting Up The Base System - Software
Setting Software - Squid
Setting Software – Bannerfilter
Setting Software - Sarg
Setting Software - Dansguardian
Configure Dansguardian:
Defining blocked and allowed site's

Getting Started / OS Install
----------------------------

Ubuntu is a complete Linux-based operating system, freely available with both community and professional support. It is developed by a large community and we invite you to participate too!

The Ubuntu community is built on the ideas enshrined in the Ubuntu Philosophy: that software should be available free of charge, that software tools should be usable by people in their local language and despite any disabilities, and that people should have the freedom to customise and alter their software in whatever way they see fit.

These freedoms make Ubuntu fundamentally different from traditional proprietary software: not only are the tools you need available free of charge, you have the right to modify your software until it works the way you want it to.

Ubuntu is suitable for both desktop and server use. The current Ubuntu release supports PC (Intel x86), 64-bit PC (AMD64), UltraSPARC T1 (Sun Fire T1000 and T2000) and PowerPC (Apple iBook and Powerbook, G4 and G5) architectures.

Ubuntu includes more than 16,000 pieces of software, but the core desktop installation fits on a single CD. Ubuntu covers every standard desktop application from word processing and spreadsheet applications to web server software and programming tools. Read more about Ubuntu on the desktop and Ubuntu on the server.

Download the latest Ubuntu Server ISO from

UK: [http://www.mirrorservice.org/sites/releases.ubuntu.com/](http://www.mirrorservice.org/sites/releases.ubuntu.com/)
Belgium: [ftp://ftp.easynet.be/ubuntu-iso/](ftp://ftp.easynet.be/ubuntu-iso/)
USA: [http://ubuntu-releases.cs.umn.edu//](http://ubuntu-releases.cs.umn.edu//)
Europe: [http://se.releases.ubuntu.com/](http://se.releases.ubuntu.com/)

Boot the server machine with the CD in and follow the easy to use prompts. You should be asked to create a user.
Setting Up The Base System - Networking

Once the system has rebooted log-in. We will now set the root password, at the prompt type:

user@server:~$ sudo -s

and press enter, enter your password and press enter again. The prompt will now change to

root@server:~#

At this prompt type

root@server:~# passwd

and press enter. You will now be prompted to enter a password and confirm it, this will allow you to log-in as root directory.
You should have been able to set the host-name during setup, if not type

root@server:~# hostname myserver

and this will set 'myserver' as the hostname. Next we will set the networking up,

root@server:~#vi /etc/network/interfaces

and press enter. If you are not familiar with vi please check out [http://www.vim.org/](http://www.vim.org/). You will now see the following

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
network subnet
broadcast broadcast address
address your IP
netmask netmask
gateway default gateway

This will make the network address static, no save and quit. Type

root@server:~# ifdown eth0 and
root@server:~# ifup eth0

for the network settings to be applied. Now we will set the DNS, enter

root@server:~# vi /etc/resolv.conf

This file may be emtty if it is enter the following then save and quit.

nameserver IP of Primary DNS Server
nameserver IP Of Secondary DNS Server

The '/etc/hosts' file can be edited to customise DNS address, syntax is :

IP HOSTNAME FULLY QUALIFIED DOMAIN NAME e.g.
xxx.x.x.x servername servername.domian.com

Setting Up The Base System - Software

Ok, now that the networking is setup we can get some software down. First we need to edit the apt sources list, to do this type the following:

root@server:~# vi /etc/apt/sources.lst

and remove the leading hashes from lines begin deb and deb-src. Add a hash in front of 'deb-cdrom'. This will give you more choice in software and stop the OS asking for stuff off the cdrom.
Now we will update the base system with security updates and software updates. Run the following:

root@server:~# apt-get update

This updates the local list of available updates and software

root@server:~# apt-get update
This will tell the system you want to update the system and it will ask are you sure and tell you what it will do.

Next you may be asked to reboot if you get a new kernel, if so log back in as root. Now we will install the software we will use.

root@server:~#apt-get install build-essential apache2 apache2-common squid squid-common dansguardian sarg postfix perl ssh clamav

You will probably be asked to configure postfix, if not run

root@server:~#dpkg-reconfigure postfix

For the type of mail select 'Local Only'. Type your username or the username of the person responsible for the server as the person to recieve roots mail. Then select the default options for the rest.

After that run

root@server:~# apt-get update and
root@server:~# apt-get update

again, this will update anything that needs to be updated. This should be the base system.
Now we will edit the mail aliases file

root@server:~# vi /etc/aliases

in here you can edit who receives mail from the system. Next to your username enter your work email address to allow the system to email you logs, alerts, etc. eg.

# Added by installer for initial user
root: user1
user1: [email]my.email@company.com[/email]

Save and quit, for these changes to take affect either restart postfix or run

root@server:~# newaliases

Next we will configure ssh so it will not allow remote root login. type

root@server:~# vi /etc/ssh/sshd_config

And change PermitRootLogin from Yes to No, then save, quit and restart ssh

root@server:~# /etc/init.d/sshd restart

Now we will download bannerfilter from [http://phroggy.com/bannerfilter/](http://phroggy.com/bannerfilter/) which blocks adverts on websites. Unzip the downloaded file into /usr/local/etc/bannerfilter using

root@server:~# tar -xf archive /usr/local/etc/bannerfilter


Setting Software - Squid
-------------------------

To edit the squid config type

root@server:~# vi /etc/squid/squid.conf

To a working squid proxy server you will need to add a acl for your network and tell the server to accept connections, give the server a visible hostname and change the server administrator email.

To do this search for 'acl all src' under that add a new line
acl mynetwork src 10.7.152.0/24

next search for
#http_access allow our_networks
http_access allow localhost

And add in the folloing below it.

http_access allow mynetwork

Now to set the hostname, search for 'visible_hostname' and add the following

visible_hostname myserver.my-network.com


Now to set the cache manager, search for 'cache_mgr ' and add the following

cache_mgr [email]me@myemail.com[/email]

Now restart squid

root@server:~# /etc/init.d/squid restart

and in your browser set the proxey sever setting to the address of your proxy server and the port to 3128. And try to browse the web, you should be able to browse the web, if not read the error message and review the configuration. Then Google it.


Setting Software – Bannerfilter
------------------------------------
see: [http://phroggy.com/bannerfilter/](http://phroggy.com/bannerfilter/)


Setting Software - Sarg
-----------------------

Sarg is a squid reporting tool, which gives you browsing stats by host and top n sites visted by connects or bandwidth used. To customise sarg edit

root@server:~#vi /etc/squid/sarg.conf

to set up the Ttile and other options for the appearance of the report and where it should be placed once produced. To run a sarg report type

root@server:~#sarg


Setting Software - Dansguardian
--------------------------------

Configure Dansguardian:

root@server:~# vi /etc/dansguardian/dansguardian.conf

Add a '#' in-front of 'UNCONFIGURED'.
Chose what you want users to see when a site is blocked. To create a custome page chose option 3 and edit
/etc/dansguardian/languages/your-lanuage/template.html .
Chose want you want to log.
Chose the log format
Review the rest of the settings and set as desired.
To test the proxy set your proxy settings in your browser to the ip of the server and port to 8080 and goto sex.com. It should be blocked and you will receive the blocked screen, you can edit the custome html template at

vi /etc/dansguardian/languages/your-lanuage/template.html

Defining blocked and allowed site's

To restrict website you can edit bannedsitelist in the dansguardian root directory. You can either specify certain domain names or unquote the ** to enable blanket block, thus blocking any domain not in the exceptionsitelist.
To allow certain domains edit the exceptionsitelist
You can also set allowed/denied mime types, extensions etc
You can also edit the weighted phrases.
You can add your own custom denied page.
After editing any of these restart dansguardian and squid demons in /start/
To test or use dansguardian set the proxy IP to the machine with dansguardian
and port to 8080 unless you specified otherwise in the dansguardian.conf. Then try and go to a site you have blocked.

---

### Post by revertex on 2007-04-21
Nice tutorial, but have some suggestions, squidguard as a lightweight alternative for ppl that don't need something too facist as dansguardian, page-prefetch as a obligatory companion to squid.

Chain privoxy to  squid, it's one of the best advertisement blocker out there.

Configure squid as transparent proxy,(needs a NAT rule) this way you don't need  to change anything client side.

---

### Post by Sampler on 2008-02-18
Thanks for a great toot - managed to work my way through most of it and have a working proxy server.

Just two things left - one is to auto-configure dansguardian blacklists, I've got it running and can type in my own sites to block - but don't fancy facing half the internet worth of URLs to type in - googling for an existing list comes up with little but scripts that don't seem to work due to out of date URL's.

The other is segmentation faults when I run SARG reports - looking at the URL it seems to create the folder and index page but most of that is missing.

Not really used linux much before this, especially server so any help for a dummy would be really appreciated.

Tried squidguard too but the extra DB thing it needed confused me. (page-prefetch went on a treat).

---

### Post by Sampler on 2008-02-20
Bit more googling found me:
[http://urlblacklist.com/](http://urlblacklist.com/)
Which has a nice big list with a one time free download

Fixed SARG by removing the package mentioned in the above, downloading the version from the [SARG sourceforge]("http://sarg.sourceforge.net/sarg.php") page and applied the [patch [ 1746289 ] Segfault in x86_64]("https://sourceforge.net/tracker/index.php?func=detail&aid=1746289&group_id=68910&atid=522793") which has done the trick - for those liek me who don't know how to add a patch, compile and install there's details in [this patch listing]("https://sourceforge.net/tracker/index.php?func=detail&aid=1771501&group_id=68910&atid=522793") which helped.

One issue I do have outstanding though is my sarg reports don't report on users properly - it bundles them all in as Localhost?

---

### Post by Sampler on 2008-02-22
Fixed the SARG reports by adding LDAP lookup following this site:
[http://www.papercut.com/kb/Main/ConfiguringSquidProxyToAuthenticateWithActiveDirectory](http://www.papercut.com/kb/Main/ConfiguringSquidProxyToAuthenticateWithActiveDirectory)
But now have users prompted for username and password *everytime* they open their browser!

Anyone know of a way round this?

---

### Post by upbeat.linux on 2008-03-17
I take it your users' primary browser is Firefox. 

Add the FQDN of your proxy server to the following entry (about:config):

network.automatic-ntlm-auth.trusted-uris

This also comes in handy if you use OWA or have an intranet site that authenticates the same way and don't want the user entering credentials at every login.

On a side note you could automate this by creating a user.js file with your organizations default firefox config (including the above ntlm-auth line).  Then write a logon script to copy the user.js file at logon to:

C:\Documents and Settings\<username>\Application Data\Mozilla\Firefox\Profiles\<profile string>\

BTW, what does the auth_param section of your squid.conf look like?

Sources:

[http://www.mozilla.org/projects/netlib/integrated-auth.html](http://www.mozilla.org/projects/netlib/integrated-auth.html)
[http://kb.mozillazine.org/Network.automatic-ntlm-auth.trusted-uris](http://kb.mozillazine.org/Network.automatic-ntlm-auth.trusted-uris)

---

### Post by upbeat.linux on 2008-03-17
Also, the Gentoo Wiki (as usual) comes in extremely handy for the 127.0.0.1 resolution:

[http://gentoo-wiki.com/Dansguardian](http://gentoo-wiki.com/Dansguardian)

---

### Post by Sampler on 2008-03-20
Cheers - will look into this - we actually have IE as a default browser (baby steps in talking the management out of the default MS wares).

Thanks again.

---

