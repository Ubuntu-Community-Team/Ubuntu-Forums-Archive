---
title: "unsure of how to install program (xampp)"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by LOMhawkeye on 2007-04-22
Hello,

I was excited to get the new ubuntu 7.4, (didn't want to waste ubuntu bandwidth so I used bittorrent, and it took a while). I have a laptop that's using windows and I installed the new Ubuntu on a desktop (a bit older but still respectable specs).

I want to teach myself php, so I downloaded xampp (I got the linux version) and put it on a usb stick. It transferred wonderfully onto my desktop with ubuntu, and I left-clicked to "unpack" the file. I tried finding instructions to install xampp, and it talked about the "terminal," so I found that in accessories, and tried typing in the commands specified ([instructions link here](http://www.apachefriends.org/en/xampp-linux.html)). I guess the "su" command tries to log me on as the administrator, but I only have one password for my account, and that password didn't work. Is there another admin password? (I installed Ubuntu7.04 on top of an un-updated version of 6.10, no internet connection on the desktop I'm using, would it import the admin-password from that? I don't remember what it would be).

I haven't ever really used linux before, so I'm unfamiliar with the command-line interface, but with a little assistance I think I could figure it out quick. I would strongly prefer gui instructions though.

---

### Post by AAM on 2007-04-22
> I guess the "su" command tries to log me on as the administrator, but I only have one password for my account, and that password didn't work. Is there another admin password?
actually the command is **sudo**, not *su*.

So from your link document, the following portion:
> [LIST=1]
[*]Go to a Linux shell and login as the system administrator root: su
 
[*]Extract the downloaded archive file to /opt: tar xvfz xampp-linux-1.6.1.tar.gz -C /opt
[/LIST]
would be rendered in Ubuntu as:
> sudo tar xvfz xampp-linux-1.6.1.tar.gz -C /opt
when you enter this is will ask you for a password, give them your user password [the first user at installation is the administrator].

Anywhere you are asked to do something as *root* or *admin* or *su*, just put **sudo** in front of each and every of the required commands.

Let me know if that solves the problem!

---

