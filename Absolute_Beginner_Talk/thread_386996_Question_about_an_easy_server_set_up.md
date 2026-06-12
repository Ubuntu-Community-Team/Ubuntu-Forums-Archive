---
title: "Question about an easy server set up"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by djlyx on 2007-03-17
Greetings all,

Though I consider myself a newbie, I have been using Ubuntu since mid last year.  I use it at home for desktop things, like surfing the net, and writing reports/email.  

I don't know much about servers, but I was wondering if it is possible for me to make some type of folder (directory) where I can store info, and then make it accessible through the Internet.  So in other words, I want to access my stuff from work, or some other location that is away from my home.

Like I said before, I have no knowledge of servers or anything like that.  I just want a very simple and secure way of accomplishing what I outlined above.  And I'd like to do it via GUI.

I apologize if this topic has been brought up before, but I didn't find anything simple enough when I did a search.

Thanks in advance.

BTW, I'm running Ubuntu 6.10 on x86, connected with a router.

---

### Post by BarfBag on 2007-03-17
Can't give you specific instructions, but I can tell you this.  If your IP address isn't static (not changing), then it wouldn't be possible to turn your PC into a server.

What you could do is connect to your PC with a remote connection.  It's pretty cool.  You see your desktop pop up in a window, and if you make it full screen; it feels exactly like you're sitting at your PC.  You can do this from virtually anywhere you're allowed to install software.  It's fairly secure as well.  Unfortunately, I can't give you specific instructions on this, either.

---

### Post by djlyx on 2007-03-17
You mean if I have a dynamic IP address it isn't possible?  I believe I have static.

So I'm good to go

---

### Post by annda on 2007-03-17
would you like to just share some files or remotely run your system?

i think the easiest way to make some files accessible from anywhere is to setup apache server, put all the files you want to share in your apache document root and get [dyndns]("http://www.dyndns.com/") to take care of forwarding connections to your computer.

another option is SSH:
[http://users.bigpond.net.au/hermanzone/p11.htm](http://users.bigpond.net.au/hermanzone/p11.htm)

---

### Post by djlyx on 2007-03-17
> **annda said:**
> would you like to just share some files or remotely run your system?

i think the easiest way to make some files accessible from anywhere is to setup apache server, put all the files you want to share in your apache document root and get [dyndns]("http://www.dyndns.com/") to take care of forwarding connections to your computer.

another option is SSH:
[http://users.bigpond.net.au/hermanzone/p11.htm](http://users.bigpond.net.au/hermanzone/p11.htm)

 I do not want remote admin, I just want to get stuff off my computer. I know it is possible, because I had friends who have done this under windows 2000.  All I had to do was type in an IP address, and I had read-only access to a specific folder in their computer.  I know they didn't pay for any type of service either.

Thank you for the links, I tried out ssh, but I believe the literature is too advance for me and it doesn't explain how to access the server from outside of the LAN.

---

### Post by General_Ts0 on 2007-03-18
Sounds like you want an [FTP]("http://ubuntuforums.org/showthread.php?t=79588").  Just know that FTP (the protocol itself) is not secure.  You can use wireshark/ethereal to easily capture usernames/passwords (I'm an IT Security student).  If you've got the FTP setup for read-only, shouldn't be an issue.  I had a Windows FTP setup via IIS for a while and never had a problems (except for IIS problems).

Refer to the first part of the article for ez setup, and read the rest as you get more adventurous if you want to go the more secure route.

---

### Post by djlyx on 2007-03-18
I installed gproftp (easy way), but i have no clue how to set it up.  I have to be honest, I am totally lost.

---

### Post by General_Ts0 on 2007-03-22
I don't need one or I'd help you.  Jump on that thread and go to town.  Trial and error, dude.  I blew up Windows so many times it's not even funny.

My advice, just stick with what's intuitive.  Setup a folder, put some fake junk in it, don't forget about permissions and opening both TCP and UDP port 21 on your router/firewall.  Once you get to what's not so intuitive, make one change at a time and test, baby step till your golden.   I chose Ubuntu v. other distros cuz the community has reputation for being so helpful, hopefully this holds true for you too.

---

### Post by cowlip on 2007-03-22
--sorry

---

### Post by steveneddy on 2007-03-22
I have done the same thing you are wanting to do. 

I have an always on DSL connection that goes through a Linksys router that supports DynDns services. Go to DynDSN.org to get more details. You use this service when you have a changing, or dynamic IP address. Your router reports to the website when your IP changes so others, including yourself, can type in a simple address, like 

djlyx.dyndns.org

and the address will point to your IP address.

NOW - you must open up some ports for the type of service you want to use to access your PC on the inside network, your PC at home.

Try getting vnc4server on the home PC off of Synaptic and put xvnc4viewer on the laptop or whatever linux machine you want to view from. Using this method, you will need to open up port 5901 on the router so the outside world can see it.

After doing this, from inside the network, type in a terminal:

```
v4vncviewer localhost:1
```

and you should see a log on screen. This way you know it works. 

To connect from a remote location, in your terminal, type:

```

xvncviewer address_of_pc.dyndns.org:1

```

This is after you do the DynDNS website stuff. 

The ":1" tells the PC at home to log you in to a new session. Someone can be on the same PC at home and you can log on remotely and unless you are running a system heavy application, they shouldn't even know that you are there. 

Please search the forums for VNC. I think that this is what you are looking for. It works for us all the time. I have a Samba server, an HTTP server for a simple web page for friends and family and the VNC server so I can remote into the machine. It's just like I am sitting on my machine at home.

For an extra cool log on to freak out your friends do this:

```

xvncviewer -fullscreen address_of_pc.dyndns.org:1

```

This will give you a full screen log in screen and really make you feel like you are at home.

[Go here]("http://ubuntuforums.org/showthread.php?t=191564&highlight=HOWTO%3A+Set+up+VNC+server").

Cheers - SE

---

### Post by djlyx on 2007-03-25
I'm sorry, I don't want remote admin.  I just want a read-only directory that I can access from another machine outside of my LAN, using firefox, safari, or IE.  I don't want to "use" my computer from another machine, per say.

I tried to install and use gproftpd, however it is saying that I am not root and it automatically closes. :( 

Attached is a screen shot of what I want, however I want to access this directory through the world wide web

thanx for the replies

---

### Post by steveneddy on 2007-04-29
The pic is from a Samba server on a local network. Why don't you set up an apache server on this machine and put this file in the /var/www folder?

Also, being able to log on remotely is the way that I believe everybody else does it. This is how I access my machine, is through VNC. It's easy and you get access to the entire machine, even the folder that you want to get files from.

I really don't know of anything else that would let one remotely access a folder over the internet.

---

