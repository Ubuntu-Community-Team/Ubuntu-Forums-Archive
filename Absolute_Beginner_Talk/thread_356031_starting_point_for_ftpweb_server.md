---
title: "starting point for ftp/web server"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by kraigory on 2007-02-07
Alright, well i've done quite a bit of research on this, but i find i'm still in need of a basic starting point because of my still relative impotence on the subject.

What I want is to run at least a ftp server from home, and hopefully eventually a basic webserver. I own hosted webspace and a domain name currently, but i only use it for personal stuff (not hosting big sites with lots of bandwith) so i'd like to just host it on my ubuntu box, with hopefully the domain name pointing to the box. 

I know that is a hair complicated with apache and stuff, so i'd like to start with a basic ftp server that allows me to access it from anywhere and upload/download files to and from it. 

Sooo, i've discovered the vast array of ftp programs, and i've kindof decided on vsftpd, 'cause it sounds secure and easy to use. My question is, how do i access this server from another computer? With an ip address? A ftp program? I know with some ftp stuff you can see a website that gives you links to the files hosted, how would one set that up? Is one of the ftp programs easier than the rest to set up the outside access? Also if i'm on a router, do i need to set a static ip? If so, how, and what ip do i make it? Just a random one?

Anyone that could provide some advice would be great. I just need a generic starting point. once I understand more about what I want to do I think i can figure stuff out. So don't worry, i'm not asking for a long HOWTO about this, I can search for that on my own :)

---

### Post by lloyd_b on 2007-02-08
> My question is, how do i access this server from another computer? With an ip address? A ftp program? I know with some ftp stuff you can see a website that gives you links to the files hosted,

Set up the FTP server.  If you've configured it to allow anonymous logins, then in any web browser, in the URL box enter "ftp://{ip address}".  This will give you the ability to see and download files from that server.

> Also if i'm on a router, do i need to set a static ip? If so, how, and what ip do i make it? Just a random one?

You will almost certainly need to forward some ports (port 21 at the very least) from the router to the machine in question.  Whether you need a static IP or not depends on the router - many DSL routers will not allow port forwarding without a static IP.

To determine what IP to use:  Go into the router's setup, and see what IP range it currently assigns (generally, home DSL or cable setups will use the 192.168.0.x or 192.168.1.x ranges).  In the router's setup, it will specify what address ranges it will use for DHCP.  Pick an address that is NOT within this range (or there is the chance that the router will give that same IP to another computer).

Note: To get into the router's setup, generally you just start up a web browser, and in the URL box type "http://{IP address of router}".  For instance, in my case it's "http://192.168.0.1"

For example, on my DSL router, it uses the range 192.168.0.x, with the router being at 192.168.0.1.  It assigns DHCP addresses starting at 192.168.0.64.  I have a machine that I sometimes use for Gnutella (which requires port forwarding like FTP), which have decided to use the address of 192.168.0.10.

As to how to set up a static IP, edit the file "/etc/network/interfaces", changing the lines
```
auto eth0
iface eth0 inet dhcp
```
to
```
auto eth0
iface eth0 inet static
   address {the IP address you selected}
   netmask 255.255.255.0
   gateway {the IP address of your router}

```
Note: there are GUI tools for doing this as well, but I'm an old command-line junkie, so I have no clue what they are.

So:
1.  Decide what IP you are going to use (by checking the router setup)
2.  Set the static IP for the machine in question
3.  Set the router to forward port 21 to that machine
4.  Install and configure the FTP server

At this point, you should be able to get files from the FTP server from any machine on the local network.  You *may* be able to get files from the FTP server from a machine out on the internet (be advised, the IP address you'll use from outside will NOT be the 192.168... address - it'll be an externally visible IP address.  Your router setup should tell you what it is).

To put files onto the server, you'll need a different FTP client (web browsers don't allow uploads, AFAIK).  Personally, I use "ncftp" (available from the repositories), but it's a command line tool rather than graphical.  Try running Synaptic and searching for "FTP client" if you want something prettier.

There are a number of potential pitfalls that may prevent you from accessing the FTP server from the internet.  I'd suggest get it working locally, then worry about those.

I can't give you much info regarding vsftpd, as I've never used that one (the last FTP server I set up was wuftpd, which is quite dated).  Hopefully if you post questions regarding the specific server software you've choses, somebody will be able to help you get it working.

Hope this helps.

Lloyd B.

---

### Post by kraigory on 2007-02-08
Hey thanks alot for the info- that pretty much covers it and gives me a general idea on what i need to do. I THINK my router will allow port forwards without a static ip address, as i've done it before with no problems But if not, now I know how! 

I won't really need to upload files to the server from the outside, and if i do, it'll be from my windows laptop and I can use filezilla or something.

Thanks again for the advice!

---

