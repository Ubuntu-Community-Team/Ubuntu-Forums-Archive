---
title: "Noobie2 wants to set up a server"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by noobie2 on 2006-10-05
Hi!  I am a new convert to Ubuntu and loving it.  I want to set up a home server and have attached a proposed architecture.  Here is what I want to accomplish...

Objectives:
1.	Host web based company file share/library for remote users.  Up to 10 remote users.  May or may not be logged in at the same time.  File revision control with ability to “Check In” and “Check out” files.
2.	Host multiple websites using one dynamically assigned IP from ISP.
3.	Provide remote secure admin control of the Ubuntu server from a remote pc, either within the home network or outside via the internet. (will I nees ssh etc?)
4.	Provide Firewall for home network.
5.	Provide web content filtering for children and young adult access to internet (Dansguardian)?
6.	Provide central file server for home network, music files/photos.

Also, should I put the Server behind the wireless router and let the router be the gateway and dhcp server?  Or is it better to have the Server be the gateway and dhcp server, and just use the router as an switch/access point?

Thanks for any advice.

---

### Post by xpod on 2006-10-05
:shock: 
You dont sound like you really need much help:D 
Wish i knew what you were even talking about so i could help you.:confused: 

Great first post...
Good stuff
Good luck

---

### Post by linuxmunky on 2006-10-05
Hello noobie2: this is my first post in the forums, and I'm glad I could help someone out.  I made a Pentium 2 a server using Ubuntu, and I love it.  I started by downloading the Ubuntu server image and burning it to a CD.  The benefits of the Ubuntu server is that it can install LAMP (Linux, Apache, MySQL, and PHP) all by default, which relieves a lot of headaches.  :) However, it can be daunting because it's CLI (command line interface) only. 
This site, however, can really help you out: [http://www.howtoforge.com/perfect_setup_ubuntu_6.06?](http://www.howtoforge.com/perfect_setup_ubuntu_6.06?).  

Anyhow, I'll try and tackle your questions specifically:
1.)  Not really too sure about this one: I might recommend FTP or SFTP, yet they might not have all the features / benefits you might want.  The guide helps you out with installing an FTP server.
2.) Apache!  :) Just follow the guide and you're up and running.  Behind a cable ISP, I use No-IP with the client running on my Ubuntu server.  Works great.
3.) SSH is great.  The guide also includes how to get that up and running.  If you want, you could also install a desktop environment and remote desktop in.
4.) Check out Firestarter at [http://www.fs-security.com/](http://www.fs-security.com/) and Shorewall at [http://www.fs-security.com/](http://www.fs-security.com/).  Your WRT54G provides a basic firewall, but if you are running services on your Ubuntu server, check out Firestarter and Shorewall.  If you feel comfortable enough, you could also try to research iptables.
5.) Not so sure, sorry.  :-# 
6.) Samba!  If your workstations are running Windows, Samba's the way to go.  Check out how to set it up at [http://www.ubuntuguide.org](http://www.ubuntuguide.org).

This last question is your preference.  I have my server behind my router, and just opened the necessary ports and forwarded them to the server.  Obviously, make sure the server has a static IP, regardless.  If you want to run your own DHCP server, the guide will also help you with that, too.

Good luck, and reply with questions or trouble!
:)

---

### Post by skymt on 2006-10-05
1. You probably want [Subversion](https://help.ubuntu.com/community/Subversion) for the revision control. As far as I know, there's no really user-friendly revision control system on Linux right now, so you may want to whip up a few wrapper scripts as needed.

2. See the documentation for Apache [Virtual Hosts](http://httpd.apache.org/docs/2.2/vhosts/).

3. SSH is what you want. If you want GUI remote access, use VNC or [NX](http://www.nomachine.com/) over an SSH tunnel.

4. I like [FireHOL](http://firehol.sourceforge.net/) for a firewall builder. Shorewall is also good.

5. Dansguardian is the best choice on Linux right now.

6. You can do this over [SSH](https://help.ubuntu.com/community/SSHHowto) (see section 2), [Samba](https://help.ubuntu.com/community/SettingUpSamba) or [NFS](https://help.ubuntu.com/community/NFSv4Howto). Whatever you do, make sure your file server is behind your firewall.

Note that if you put the server behind the router, making the router the gateway, someone could easily get around Dansguardian by deleting it from proxy preferences. If you make the server the gateway, you can block port 80 (web) to make all web traffic go through your DG.

---

### Post by NeoGreen on 2006-10-16
Noobie2 did you get your server working?  I am in the process of doing the samething.  Update us on your status please.:)

---

