---
title: "I want to control my Ubuntu server with my Ubuntu desktop."
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by kavon89 on 2007-08-12
I am brand new to servers and the like. I really just want to be able to fully control the server I put together with spare parts through my Ubuntu desktop PC.

Server specs: 

Pentium III 700Mhz
128MB RAM
20GB hard drive
10/100 Nic, I am pretty sure it works without extra drivers. It's simple and older PCI one.
Ubuntu 7.04 Server Edition

Yay for having enough spare parts for a decent personal home server. :guitar:


I have it connected to a network switch/hub. No routers in my LAN. I also have a Windows XP computer on my network. I want to resize the ext3 partition and make a peice Fat32 so it can read it. I'll work on that in a separate issue I guess.


I'm pretty average with the terminal, I don't mind doing everything through it. I just need to know the command to view all the files in that current directory, like a tree.

---

### Post by llamakc on 2007-08-12
On the server: sudo apt-get install openssh-server

On the Desktop:

ssh serverusername@serverIPaddress

Then, use the "ls" command to view files and directories. 

Or, are you looking for a graphical solution?

---

### Post by annda on 2007-08-12
there's lots of info here to help you along:

[http://users.bigpond.net.au/hermanzone/p11.htm](http://users.bigpond.net.au/hermanzone/p11.htm)

---

### Post by kavon89 on 2007-08-12
> **llamakc said:**
> On the server: sudo apt-get install openssh-server

On the Desktop:

ssh serverusername@serverIPaddress

Then, use the "ls" command to view files and directories. 

Or, are you looking for a graphical solution?

I'm not looking for a graphical solution. Apart of the deal with this server is I learn a lot about the terminal and how to use it well.


I have hit a slight snag, it is asking for the CD, and I took the CD drive out because I didn't think I would need it any more. It is my only CD drive and I have to steal it from my desktop.

Can I install openssh-server through the internet with a package manager?

---

### Post by annda on 2007-08-12
comment out the cd-rom in /etc/apt/sources.list and you should be good to go:

```
sudo apt-get update
sudo apt-get install openssh-server
```

---

### Post by kavon89 on 2007-08-12
> **annda said:**
> comment out the cd-rom in /etc/apt/sources.list and you should be good to go:

```
sudo apt-get update
sudo apt-get install openssh-server
```

How do I open that text file? Gedit doesn't work obviously.

Also, how do I go up and read a long print-out in the terminal? I'm use to the scroll bar and page up/down don't work. ;)

---

### Post by annda on 2007-08-12
to edit the file:

```
sudo nano /etc/apt/sources.list
```

hit ctrl+o to save the file ctrl+x to quit.

p.s. in order to just read long files comfortably, you can use the 'less' command.

---

### Post by kavon89 on 2007-08-12
Hey, thats awesome! I connected to it with the Connect to Server thing in Ubuntu. Very easy file management!!

I set up Teamspeak on my server, and now I need to open a port to allow others to connect. How would I do this with a terminal command?

---

### Post by annda on 2007-08-12
hope this helps:
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by arron on 2007-08-12
There is a lot of cool things you can do with a old server. www, email server, web based email, fetchmail to get pop and other email types, web galery, print server, file server, vpn hub... a pc like that has a lot of juice for a server.  Im doing the same thing, the list goes on.  All via the terminal, no gui with it.  It rally helps when im remote and need to get something.

Welcome to true geekness.

```
cowsay You are a geek!
```

---

### Post by stalker145 on 2007-08-12
Sometimes I feel like a parrot for saying the same thing over and over, but I shall continue nonetheless :rolleyes:

I use [WebMin]("http://www.webmin.com") on my server at home. It's secure enough for me and you can do anything through it that you can do sitting in front of the box - all through a web interface.

SSH is probably better if you know and are comfortable with the command line, but if you're not then I would suggest this to get you started.

> There is a lot of cool things you can do with a old server. www, email server, web based email, fetchmail to get pop and other email types, web galery, print server, file server, vpn hub... a pc like that has a lot of juice for a server. Im doing the same thing, the list goes on. All via the terminal, no gui with it. It rally helps when im remote and need to get something.

Welcome to true geekness.


```

cowsay You are a geek!
```

Don't forget to ```
sudo aptitude install cowsay
```:lolflag:

---

### Post by kavon89 on 2007-08-12
Thanks so much annda!

---

### Post by kavon89 on 2007-08-12
I have SSH working nice. I set the box to download something with a command, but I want to shut this computer down and go to bed. When I close the terminal it stops what it is doing.

How do I get it continue it's work although the terminal is closed on my desktop or the desktop is off?

---

