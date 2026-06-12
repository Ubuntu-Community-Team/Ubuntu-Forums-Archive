---
title: "Ubuntu as a Home Server - Any tips or suggestions?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by chrigil on 2007-04-10
Hi I'm completely new to Ubuntu and virtually new to Linux (tried mandrake a few years ago but got frustrated/bored).
I want to set up a home server for use with my current XP/Vista computers and Macs for backup and file sharing etc, Media Server for watching films and music etc and also to be used as a Mail Server as well as a Web and Database server (MySQL) for small homepages and development etc. Essentially the computer will be used purely as a server and its unlikely I'll ever really sit in front of it and actually 'do' anything on it.

I've downloaded the Server Version of Ubuntu and just wanted your opinions on how suitable this will be for my plans. I plan to use an open source IMAP mail server (any suggestions?) and possibly MonoProject for open source ASP.Net hosting of 'in-development' projects.
I'll also want some decent, solid media software to enable me to play my large collection of DivX movies as well as my music (any suggestions?).
In the future I'll want some sort of home security software to monitor my house CCTV and/or control appliances etc. I'll either look into ready written stuff (any suggestions?) or write my own.

If any one has any suggestions as to what software would be ideal for this or hardware recomendations (video cards for video/drivers etc) would be appreciated.

Also, how easy do you think it would be for a technically competent beginner to set up a server using Ubuntu that meets my requirements?  I work in IT (mainly Windows based) and I'm willing to research/read books on the OS etc.

Thanks in advance for any advice you can offer.

Chris Gilbert

---

### Post by speeddemon8803 on 2007-04-13
> **chrigil said:**
> Hi I'm completely new to Ubuntu and virtually new to Linux (tried mandrake a few years ago but got frustrated/bored).
I want to set up a home server for use with my current XP/Vista computers and Macs for backup and file sharing etc, Media Server for watching films and music etc and also to be used as a Mail Server as well as a Web and Database server (MySQL) for small homepages and development etc. Essentially the computer will be used purely as a server and its unlikely I'll ever really sit in front of it and actually 'do' anything on it.

I've downloaded the Server Version of Ubuntu and just wanted your opinions on how suitable this will be for my plans. I plan to use an open source IMAP mail server (any suggestions?) and possibly MonoProject for open source ASP.Net hosting of 'in-development' projects.
I'll also want some decent, solid media software to enable me to play my large collection of DivX movies as well as my music (any suggestions?).
In the future I'll want some sort of home security software to monitor my house CCTV and/or control appliances etc. I'll either look into ready written stuff (any suggestions?) or write my own.

If any one has any suggestions as to what software would be ideal for this or hardware recomendations (video cards for video/drivers etc) would be appreciated.

Also, how easy do you think it would be for a technically competent beginner to set up a server using Ubuntu that meets my requirements?  I work in IT (mainly Windows based) and I'm willing to research/read books on the OS etc.

Thanks in advance for any advice you can offer.

Chris Gilbert

its not impossible..as long as you have your server up and connected to the internet..

first off..get you a GUI

sudo apt-get install ubuntu-desktop

is there a second? lol

(note to the wise:I havent dealt with server before...so if im missing and skipping parts PLEASE append to this! thanks!)

---

### Post by lamalex on 2007-04-13
for mail check out zimbra. it's great. same concept as exchange.

---

### Post by joeashcraft on 2007-04-14
I have recently (this month) setup a "home" server using Ubuntu Server. I used the [guide on howtoforge]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06"). I didn't install everything in the guide, just what I needed. I haven't installed a GUI, as I've found the command line to be sufficient. I'm new to Linux (I've only been using it for about 3 weeks) and therefore I'm relatively new to the command line, but I really like it. In my case, I'm using older hardware, so I don't really want to install a desktop. Here's what I've installed on my server:[LIST]
[*]First, everything that goes into a [LAMP]("http://en.wikipedia.org/wiki/LAMP_%28software_bundle%29") Server[/LIST]You said that you downloaded the Server edition of Ubuntu. You can choose "Install a LAMP Server" or you can install the packages individually.[LIST]
[*]Second, [OpenSSH]("http://www.openssh.com/") Server | Secure shell server, an rshd replacement[/LIST]This lets you use the command line (and access files thru a file manager, like nautilus) from another computer. This way you don't have to keep a monitor for your server. There are a few things you may need to do (like configure the network), but you're almost at a point of remote administration.
```
sudo apt-get install openssh-server
```After you have installed OpenSSH, you probably won't need a monitor again. To access your server from another computer running linux, you need the openssh-client
```
sudo apt-get install openssh-client
```Then in a terminal window type in
```
ssh [EMAIL="user@1.2.3.4"]user@1.2.3.4[/EMAIL]
```where 1.2.3.4 is the IP address of your server. After you login, you can do anything as if you were sitting at your server with a keyboard and monitor. Very handy.[LIST]
[*][phpMyAdmin]("http://www.phpmyadmin.net/home_page/index.php") | MySQL Database Administration Tool[/LIST]This basically gives you a web GUI for MySQL administration.
```
sudo apt-get install phpmyadmin
```[LIST]
[*][ProFTPD]("http://www.proftpd.org/") |      Highly configurable GPL-licensed FTP server software[/LIST]Let's you create an FTP server. Useful if you want to access files in a different way, or share access with other people. Also, if you allow it, others can upload files to your server in admin defined folders.
```
sudo apt-get install proftpd
```[LIST]
[*][TorrentFlux]("http://www.torrentflux.com/") | web based, feature-rich BitTorrent download manager[/LIST]TorrentFlux is a PHP based BitTorrent controller that runs on a web
server. It can manage all of your BitTorrent downloads from anywhere
through a convenient and easy-to-use web interface. I use this so that I don't have to worry about keeping my laptop on when downloading torrents, and I've also given access to some friends at school (their school doesn't allow torrenting).
```
sudo apt-get install torrentflux
```
If you plan on accessing your server from a computer outside of your LAN, consider getting [Dynamic DNS]("http://en.wikipedia.org/wiki/Dynamic_DNS") name for it. I use [DynDNS]("http://www.dyndns.com/") and [a client]("http://www.dyndns.com/support/clients/") that supports DynDNS to keep the IP address updated automatically.

---

### Post by chrigil on 2007-04-14
Ok thanks guys that info is really helpful.  I guess it is around this time that I should point out that had no idea that the server edition doesn't come with a GUI.  Guess I would have found out at some point!

Thanks again I'll let you know how it goes.

---

