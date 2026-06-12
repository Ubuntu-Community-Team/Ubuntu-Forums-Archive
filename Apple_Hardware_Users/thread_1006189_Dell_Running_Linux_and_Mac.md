---
title: "Dell Running Linux and Mac"
date: 2008-12-09
forum: Apple Hardware Users
---

### Post by Oliver.BS on 2008-12-09
How could or would I acess my Dell Running linux via my Mac Running OSX I want to acess it from work and my dell is at home what software do I need ?

---

### Post by tuvw610 on 2008-12-09
As a matter of fact, you are giving your character to someone else to mess around wirh when you are [power leveling](http://www.inwowgold.com/power-leveling/). They play your character for a set amount of time, or to a certain level, making sure that your character is the way you want it. This all comes with a price, however. Most of the sites that offer [WoW Power Leveling](http://www.inwowgold.com/power-leveling/) and [wow gold](http://www.inwowgold.com/) have a decent price range for starting out level 1 to 20. It can get a bit more expensive if you want your character to go from level 1 to level 70, as it takes almost a month to accomplish this [http://www.inwowgold.comIt](http://www.inwowgold.comIt) is hard to save and gain [world of warcraft gold](http://www.inwowgold.com/) in WoW, alike in the real world. Some compare the auction house in the realm of Azeroth to a huge online shopping mall. Many beginning players want to begin with the crafting profession. This ends up with costing more than it is worth to the new player, who do not hold a lot of [cheap wow gold](http://www.inwowgold.com/) at hand. Crafting supplies are quite expansive as well as the items made from those supplies.

---

### Post by Leslie Viljoen on 2008-12-09
> **Oliver.BS said:**
> How could or would I acess my Dell Running linux via my Mac Running OSX I want to acess it from work and my dell is at home what software do I need ?

By "access" do you mean you want to access the command line on that machine or the graphical desktop? If its the desktop you'll need something like VNC or FreeNX. Command-line you'd use SSH.

Whichever you choose, you'll need to do a bit of configuring, and you'll probably also need to solve two other problems:

1. You need to determine the current IP address of the home system. If you dial up using ADSL, this will change every now and then, locking you out.
2. You need to open your firewall to allow incoming connections. If you dial up using ADSL, this probably means configuring NAT in your ADSL modem setup screen.

So it's a few things to set up, and will take some time and learning. Are you game?

---

### Post by hyperboloid on 2008-12-09
> **Oliver.BS said:**
> How could or would I acess my Dell Running linux via my Mac Running OSX I want to acess it from work and my dell is at home what software do I need ?

I do this all the time. However, your situation may be different than mine. 

I have a desktop PC at home running Ubuntu, accessing the internet through an ethernet cable connected to a router. The router has *port forwarding enabled* to forward port 22 to the computer, and the home machine is running ssh ("sudo apt-get install ssh"). My home box is connected to the router using a *fixed* IP address on the LAN; if you connect using DHCP then port forwarding might not always work. 

Once you get that far, find out your external IP address at home (visiting [http://whatismyip.com/]("http://whatismyip.com/") from your home box is the simplest way) and you should be able to log in from anywhere by "ssh userid@ipaddress" (substitute YOUR userid and YOUR IP address).

If your ISP provides a fixed IP address with your service, then that's all you need. You could add the external home IP address to /etc/hosts in the Mac with a simple to remember alias like "home" and then "ssh userid@home" would do it for you. If your userid is the same in both locations then just "ssh home" is all you need. You can also "scp" or "sftp" to copy files and so on - i.e. run any command that uses ssh protocol. 

If your ISP does not provide a fixed IP address, then the home IP can change randomly. In practice, this doesn't happen very frequently, but when it does it can be a big pain. To circumvent this problem, if you want to, you need to register with a free DNS aliasing service such as [http://www.dyndns.com/]("http://www.dyndns.com/"), and follow the instructions you will find there under the "Dynamic DNS" tab. The idea is that dynDNS gives you a logical DNS for your home machine, such as myname.homelinux.net, and you run a deamon on your home box that reports changes in your actual IP address to the server at dynDNS. You then use the logical DNS to login to the home box. The logical DNS never changes. You will need to install an update client (the deamon) on your home box, just pick one of the recommended ones ([http://www.dyndns.com/support/clients/]("http://www.dyndns.com/support/clients/")).

---

### Post by Oliver.BS on 2008-12-10
Thanks is it better to run SSH or something like VM all I want to do is get files but I wont always know the file name and I also sometime want to run Deluge but turn it on etc from my pc at work?

---

### Post by _mario_ on 2008-12-10
> **Oliver.BS said:**
> Thanks is it better to run SSH or something like VM all I want to do is get files but I wont always know the file name?
to simply access (copy) files it's best to install SSH, which also provides SCP:
```
sudo apt-get install openssh-server
```
by default you should be able to login as your normal user to gain access to your home directory. of course you might have to configure your router/firewall to allow to access your machine (port 22 for SSH).

to avoid the command line, you might also use graphical SCP clients running on OSX. though, i don't know a good one.

ciao,
Mario

---

### Post by cyberdork33 on 2008-12-11
> **_mario_ said:**
> to simply access (copy) files it's best to install SSH, which also provides SCP:
```
sudo apt-get install openssh-server
```by default you should be able to login as your normal user to gain access to your home directory. of course you might have to configure your router/firewall to allow to access your machine (port 22 for SSH).

to avoid the command line, you might also use graphical SCP clients running on OSX. though, i don't know a good one.

ciao,
Mario
SCP is also called SFTP.

cyberduck is FOSS and is a general FTP client that works quite well and supports SFTP/SCP.
[http://cyberduck.ch/](http://cyberduck.ch/)

Fugu is also a good client (only for SFTP/SCP).
[http://rsug.itd.umich.edu/software/fugu/](http://rsug.itd.umich.edu/software/fugu/)

---

### Post by hyperboloid on 2008-12-11
> **cyberdork33 said:**
> SCP is also called SFTP.

Actually, scp and sftp are two different programs. They serve the same purpose, but usage is somewhat different. See "man scp" and "man sftp" for details. 

The main difference is that scp is a remote copy program, similar to cp but spanning between file systems on different hosts, while sftp is *interactive*.

---

### Post by MedianMajik on 2008-12-11
> **Oliver.BS said:**
> I sometime want to run Deluge but turn it on etc from my pc at work?
Have you tried playing with the Webui (Web User Interface) in Deluge?  It is easy to configure (allow remote connections under preferences) and is accessible through any browser.  To get it working you'll have to portforward your router (once again) so you can connect to your torrents.  This is another reason to have a static IP address for your home computer/server.  [Here]("http://phorolinux.com/how-to-use-deluge-web-user-interface.html") is a somewhat out-of-date guide (the webui is now built-in and not a mere plugin) that'll show you what I'm talking about.  I hope this helps.

---

### Post by cyberdork33 on 2008-12-12
> **hyperboloid said:**
> Actually, scp and sftp are two different programs. They serve the same purpose, but usage is somewhat different. See "man scp" and "man sftp" for details. 

The main difference is that scp is a remote copy program, similar to cp but spanning between file systems on different hosts, while sftp is *interactive*.
my point is that they are often used interchangeably (even if incorrectly so) and if a client supports one, it likely supports both.

---

### Post by cyberdork33 on 2008-12-12
> **MedianMajik said:**
> Have you tried playing with the Webui (Web User Interface) in Deluge?  It is easy to configure (allow remote connections under preferences) and is accessible through any browser.  To get it working you'll have to portforward your router (once again) so you can connect to your torrents.  This is another reason to have a static IP address for your home computer/server.  [Here]("http://phorolinux.com/how-to-use-deluge-web-user-interface.html") is a somewhat out-of-date guide (the webui is now built-in and not a mere plugin) that'll show you what I'm talking about.  I hope this helps.
ah, just use screen and an ncurses bittorrent client in an ssh session :)

---

