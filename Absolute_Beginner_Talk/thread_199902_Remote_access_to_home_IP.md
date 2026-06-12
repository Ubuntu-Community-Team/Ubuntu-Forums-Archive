---
title: "Remote access to home IP"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by Fnord5 on 2006-06-19
Normally I would search for a thread on the topic, as I am neither a vBulletin n00b, nor a forum n00b(other than here) but being completely new to linux, I wouldn't begin to know the terms for a proper search.

I work for a company that severly neuters the internet connection, even for managers(which I am) and I was wondering if there is a way to access my own IP through theirs, so I have unlimited access using my  desktop. I am using Ubuntu 5.10 Breezy Badger.

I have a XP laptop that I use for most of my day to day activities, and the linux comp is mainly for a learning experience.

If there is a way to set this up without changing any of the settings on their computers that would be awesome.

Oh, they have two programs that run in unix(through Windows), but those are for inventory, employee maintinance, LAN printing, and some customer records. There is no way that I know of to access the terminal, it's a pretty straighforward program, with no options.

Thank you,

Fnord5

---

### Post by deja2004 on 2006-06-19
If they don't have port 22 blocked, you could try ssh.

---

### Post by Fnord5 on 2006-06-19
Whoosh, right over my head.:confused:

---

### Post by tim.n9puz on 2006-06-19
Re: ssh

"Putty" is a common Windows ssh client program. Using it you may be able to get a text mode login to your home machine if your office network does not block traffic on TCP Port #22. 

You don't have to know anything about the ports to try it. 22 is the default port for ssh (Secure SHell.) Do a search for Putty, then install and run the program. If the ssh server is running on your home computer (it probably is) and Port 22 is unblocked you should get a login prompt  if all is working. Use the same name and password you log in with at home.

Tim

---

### Post by deja2004 on 2006-06-19
LOL. Sorry about that. Here's a link:

[http://en.wikipedia.org/wiki/Ssh](http://en.wikipedia.org/wiki/Ssh)

Basically SSH allows you to (via command line) access your terminal remotely. The best way to go about this is (on the ubuntu machine):

```
sudo apt-get install ssh
```

Then, head over to no-ip.com, install the linux version of their software, and set up a ddns for yourself (so you won't have to recall the ip, and in case it changes). After you're done with that, if the ubuntu machine is behind a router, forward port 22 to that machine.

Now, when you're at work, download this program (PuTTY):

[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

Type in the ddns name you used @ no-ip, enter your user/pass, and you should be good to go! :D

---

### Post by Fnord5 on 2006-06-19
Ok, that makes a bit more sense.
I assume that I enter my IP address in "putty" to prompt the login?

In my home comp, do I need to allow access to other users to see and use my desktop?  I figured out how to do that much, but I believe that it only allows linux users to gain access.

Im totally new to linux, but am a quick learner once I get headed in the right direction.

---

### Post by uzi09 on 2006-06-19
i'm not sure if you want to log into your computer from work or log into work computer from home (this one is probably illegal :D)

assuming you want to log into ur linux computer from work, you can do it 2 ways:

1) log into the command line part only (the terminal)
u can use ssh (program) for which the above few posts provide pretty much all the info you need.
basically install the server on your linux machine and use putty to ssh into it.

2) if you want a graphical version, you can turn on "remote assistance" from ubuntu (check under system > admin menu, but i'm not entirely sure because i'm not at a linux box currently)
then basically, you can give a password and go to any browser and type the following:

[http://192.168.1.1:5800](http://192.168.1.1:5800)

BE ABSOLUTELY SURE YOU HAVE THE "HTTP://" IN THERE AND in place of 192.168.1.1 enter YOUR IP address and in place of 5800 enter the port number for VNC (thats the program that allows remote assistance on ubuntu machines).
i believe 5800 is the default to log into through the web, but you MUST HAVE JAVA ON THE COMPUTER YOU'RE TRYING TO CONNECT FROM.

cheers

EDIT: if you want to learn more about VNC, check out [www.realvnc.com](www.realvnc.com). basically you  need a server running  on the machine you want to connect to remotely. in ubuntu, this is built in. to access it remotely (without having to install a viewer), check out this site:
[http://www.realvnc.com/javavncviewer.html](http://www.realvnc.com/javavncviewer.html)

also, don't forget to forward any ports if you're behind a firewall at home :D

---

### Post by dvarsam on 2006-06-20
This thread is really good too:

[http://ubuntuforums.org/showthread.php?t=186063](http://ubuntuforums.org/showthread.php?t=186063)

Read it till the End...

Good Luck!

---

