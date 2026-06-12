---
title: "Hosting my own Ubuntu server using LAMP for noobs"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by Error47 on 2008-01-14
I have an old computer that I want to use as a server. I have been paying for hosting for a while, and I figured I have a good enough connection. I am a complete Linux noob though. I want to install an ubuntu server on my computer. So I would appreciate a few links to tutorials on this subject. 

I have heard of this LAMP server, is it easy to use and maintain? I am going to be connecting to it through remote desktop or vnc because it is not attached to a monitor. I dont know how to use that putty ssl thing. I want to be able to have the same features as my regular web hosting company that I pay for. They gave me cpanel for managing my web hosting. Re-selling hosting would be cool, I want FTP accounts too. I want to host a blog too so I need php. 

I have no clue how to set all of this up on ubuntu linux, but I bet it would be nice. I would assume that installing ubuntu would be better than installing windows server edition.  So I would really appreciate if you guys could point me in the right direction. 

Thanks a lot.

---

### Post by amingv on 2008-01-14
The [Ubuntu Server Guide]("http://doc.ubuntu.com/ubuntu/serverguide/C/") may be a good place to start. Granted it's not the almighty guide of all services, but it can get anyone started.

---

### Post by farscape on 2008-01-14
Go Here: [linuxreality.com]("http://feeds.feedburner.com/linuxreality-ogg")

Check out episode 57. Then check out the rest of the web/pod casts. Good stuff.

---

### Post by xelapond on 2008-01-14
First off, 

Ubuntu is hte RIGHT choise for noobs on servers, Ive got a multi user FTP server funning in my garage.

Some basic things:

You wan to be OK on the command line(understand sudo, nano(or vim), init.d, and probably ssh)

Because the LAMP installation does not have an X server preinstalled(And we don't recommend installing one because it leads to security and stability problems) you should use SSH to control it.  All SSH is is a basic command line forwarded to your client terminal.  Openssh is a great tool for doing this.

There is a graphical web configuration tool called Webmin.  It can be found at [www.webmin.com](www.webmin.com), and I also think it is in the repositories.

The guide I used to install the server was:

[http://www.debianadmin.com/ubuntu-lamp-server-installation-with-screenshots.html](http://www.debianadmin.com/ubuntu-lamp-server-installation-with-screenshots.html)

And then to get everything up and running:

[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

Good Luck!

Alex

---

### Post by Error47 on 2008-01-15
I am really terrible with the command line. I havnt used linux in a long time, and literly the only command I know is ? and help

---

### Post by xelapond on 2008-01-15
Hmm, If you could get webmin running that would really help you.  Otherwise you either have to install a graphical interface, which probably won't help, or learn the command line.

Do you know how to use apt-get?

Alex

---

### Post by Error47 on 2008-01-15
No I really don't know how to use the command line at ALL. I don't even know how to install programs. I am not really that bad in computers, I can do almost anything in Windows, I just cant remember all of the commands in linux and what they do, maybe I can get used to it if I use it for a few years, but I doubt I have patience that will last more than a year to learn. I would really love to run a server on the command line though, a gui would be very helpfull to me. Or else windows server would be my best bet.

---

### Post by farscape on 2008-01-15
Good beginner site: [a podcast for the new user]("http://www.linuxreality.com/")

---

### Post by hyper_ch on 2008-01-15
the perfect howtos over at howtoforge.com are step by step guides... all you need to do is be able to read as well as copy'n'paste ;) that's manageable I think.

---

### Post by JoshuaRL on 2008-01-15
Hey man, I'm gonna try this soon and from what I've seen these are the benefits of running in a mostly CLI server system:

1).  Speed.  Because you don't need to run the graphics, then the speed is incredible.
2).  Security.  Many less bugs and although linux is really stable, less vulnurabilities.
3).  Ease of use.  I know, this seems ridiculous.  But once you get used to it, the console can be much easier and faster than a GUI.  And try a couple months till you can consider yourself a poweruser, not years.  You can do it man!

I've subscribed to this thread because I'll need these tips very soon.  So maybe we can do this thing dude.  It seems really cool.

---

### Post by Error47 on 2008-01-15
Joshua im glad I found someone else to help me get started on this. I dont know about the ease of use part for right now, learning the console has been tough for me. I am going to have to go through those tutorials for days to even get to the basics. Like the most important thing I need to learn is to set it up, and mange it remotley, because I dont have enough monitors to use for my extra computer. But I guess this may turn out usefull in the end.

---

### Post by JoshuaRL on 2008-01-15
Cool man.  I love this community.  So many people, and almost everyone is extremely helpful.

Try this for the command line:  [http://www.linuxcommand.org/](http://www.linuxcommand.org/)  Really good explanations.

---

### Post by Error47 on 2008-01-19
I still have not yet installed ubuntu. I was just curious about something. I am running this server from my house, I have 3 other computers connected to my router all with the same external IP address. So my question is would I be able to connect to it from a location other than my home network?

---

### Post by JoshuaRL on 2008-01-22
From what I've seen you should be able to, it will take a little bit of work but I think there's a couple different ways.  Please correct me if I'm wrong anyone:

Personal URL addresss linked to a static IP and a secure site login.
VPN
Samba?

---

### Post by emarkd on 2008-01-22
Does your router support port forwarding?  For me, that's the easiest way.

---

### Post by Error47 on 2008-01-22
I just got the computer to install Ubuntu on today. I have been thinking, and I decided that I really need a GUI. Even with the GUI I still find it hard to do things, I can't imagine how I will install utorrent or an ftp server through a command line. At least untill I learn linux, I want to be running on easy mode. 

So basically I am looking for a good guide to help me with a GUI installation of ubuntu lamp server. I don't have an extra monitor, so I would like to learn how to remote desktop connect to it. 

Thanks!

---

### Post by JoshuaRL on 2008-01-22
As far as the GUI, I would suggest setting everything you need up in the CLI and then installing:

```

sudo apt-get install xubuntu-desktop

```

That will give you the XFCE-based ubuntu desktop.  Lightweight, and yet full-featured.  It should make things easy for you.

---

### Post by Error47 on 2008-01-22
I understand what you mean, but wouldn't it be the same if I installed xubuntu directley or would there be a difference?

---

### Post by JoshuaRL on 2008-01-23
No, it would be the same.  From what I've seen in the tutorials they all say how to install a CLI system (Ubuntu server).  But if you just wanted to go with a GUI from the start that would be okay too.

---

### Post by imon9 on 2008-01-23
u will be be to acess ur computerr from outside the home network... use port forward by configuring ur router 

btw, LAMP is a bit complex to configure... but not so hard to installl...

if u plan to use php, then u will need LAMP,
else, run HFS (HTTP file server) through wine..it is simpler to configure it

if ur ISP use dynamic ip, u will need free dns like dyndns.com

lots to learn if u never run LAMP from windows before

---

### Post by Error47 on 2008-01-23
Wait, so what should I install now? Does the xubuntu have LAMP already installed? I am somewhat confused. The only reason I want lamp is because I want to host my own blog or forum, which I think requires php. So what exactly should I download to install now?

---

### Post by louieb on 2008-01-23
After you install xUbuntu there an application called tasksel. To install a working lamp server it as easy as ```
sudo tasksel install lamp-server
```
or just run sudo tasksel and it will list the diffrent stuff you can install.
[Lou's Home Server Stuff]("http://louieb.isa-geek.net/") is running on a Ubuntu desktop in my den. I'm using the dyndns service and port forwarding on my router.
More good stuff on LAMP
[ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

