---
title: "why no application based firewall in linux"
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by mephisto56 on 2005-11-12
I know of one (tuxguardian) but development seems to have stalled. Isn't) an application based firewall more secure? Now you have to open a port (eg 80) to connect to something. Otherwise only certain programs are allowed to use that port, instead of all.

If I was correct linux would have had an app based firewall since long. So where am I wrong?

---

### Post by nemin on 2005-11-12
[QUOTE=mephisto56]I know of one (tuxguardian) but development seems to have stalled. Isn't) an application based firewall more secure? Now you have to open a port (eg 80) to connect to something. Otherwise only certain programs are allowed to use that port, instead of all.

If I was correct linux would have had an app based firewall since long. So where am I wrong?[/QUOTE]
I want to mention the "owner" match module of iptables. I believe you could create a sort of application based firewall using that module. 
I also want to note that an application based firewall is especially usefull to prevent spyware from sending out information. Since spyware for linux hardly exists, it'd be quite useless, especially for ordinary users.

---

### Post by aysiu on 2005-11-12
What about firestarter and guarddog?

---

### Post by blastus on 2005-11-12
As far as I know neither firestarter nor guarddog support this. There are situations where I would find this handy. For example, I would like to block Konqueror from accessing the Internet. A lot of web pages cannot be saved 100% locally because of JavaScript, Flash, advertisements etc... Sometimes I'll save important web pages with Firefox, but then view the web page locally with Konqueror. But because of dynamic and embedded advertising and other stuff, it can take just as long to view a locally saved web page as it does to view the actual web site.

---

### Post by mephisto56 on 2005-11-12
Another thing is that I like to know which program accesses the internet. Now that I need to open port 80, every program that uses it to send info can. That doesn't really give me a secure feeling. Maybe there are no programs I use that eg send a user registration, or statistics, but as linux becomes more popular it isn't unimaginable these come into existance.

---

### Post by nemin on 2005-11-13
[QUOTE=mephisto56]Another thing is that I like to know which program accesses the internet.[/QUOTE]
To just *know* that, you can use netstat with the -p parameter.

---

### Post by mephisto56 on 2005-11-13
And is there also an easy way to block one program on a port and allow another on the same?

---

### Post by AmboyGuy on 2005-11-14
Because I used windows for a long time and still have the lingering paranoia of my system being invaded by legions of zombie hosts, I still do some of the same things I did in Win98 SE.
1.) I use a firewall. Firestarter is fine for me and was a simple install using Synaptic or apt-get install. ( of course you would update sources.list )
2.) I use a combination of host file & pac file for blocking sites & ad's from firefox (or other mozilla based browsers)  Here's a pretty good link that explains the abilities of each : **_[http://www.sherylcanter.com/articles/oreilly_20040330_HostsPac.php](http://www.sherylcanter.com/articles/oreilly_20040330_HostsPac.php)_**
I downloaded the latest no-ads.pac and in firefox :
**[color=#CC0000]Edit > Preferences > General > Connection settings > Automatic Proxy Config[/color]**
I add this url :  **file:////home/ed/no-ads.pac** (you would change the directory to wherever you saved no-ads.pac)
3.) I use clamav. I just installed the version (0.87) yesterday ( of course 0.87.1 is out but screw it, it's working) & I need to read up on it.

Even the paranoid have enemies.

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8 ) Gecko/20051114 Firefox/1.5 - Build ID: 2005111404
Xfce 4, version 4.2.1, Ubuntu 5.0.4 ( Hoary )

---

### Post by ecadre on 2006-05-12
[QUOTE=AmboyGuy]3.) I use clamav. I just installed the version (0.87) yesterday ( of course 0.87.1 is out but screw it, it's working) & I need to read up on it.[/QUOTE]

Do you run, for example, a mail server distributing email to Windows PC's, or an application/data server for Windows desktops?

If not, then I think you misunderstand Clamav.  It's used to scan for viruses that may be passed on by a Linux box  (say a mailserver) to Windows PC's.  If you just run a Linux box (eg a desktop computer at home), then it's a complete and utter waste of time.

---

