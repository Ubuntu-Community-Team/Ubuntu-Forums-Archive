---
title: "First thread, Terminal Server question"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by megamark16 on 2006-11-22
Hey everyone, first time poster, long time reader :)  Here's my newbie question, I've just started using Xubuntu (although when I setup my server I'll probably be using Ubuntu or Kubuntu) and I am really enjoying learning all about it.  I have Xubuntu installed on a very old laptop and it's running very well, but here's what I want to do:
I'd like to setup a Linux Terminal Server on one of my faster desktop machines that will allow me to connect to it through some older computers that I have via thin clients, but I don't want to boot to the server, I want to install Xubuntu on the slower computers so that they are standalone but than have the ability to connect to the terminal server to run a seperate xwindows session on the faster machine.  This might sound a little backwards, but I really don't want to have to mess with the PXE boot disks and everything.  Anyone have any suggestions?

Thanks!
Mark

---

### Post by awbassett on 2006-11-22
You could try SSH X Forwarding, thats generally what I do. The downside is you don't have a 'session' per se, but it will sort of accomplish what you want to do.

In a terminal, type:
ssh -X hostname /path/to/app

---

