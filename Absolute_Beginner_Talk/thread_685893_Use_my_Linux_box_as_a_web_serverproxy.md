---
title: "Use my Linux box as a web server/proxy"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Indystev on 2008-02-02
I am very new to Linux/Ubuntu so bear with me if you will.

I would like to use my linux box as a web proxy so I can access my home PC's while I am on the road AND skirt the web "nanny" that work puts in place.

I have a domain name, dynamic DNS enabled so my system will update the servers with my current IP, and it sends me an email upon update.

Now, what I want to do is configure the system for access and secure it....

Are there any tutorials floating around out there that I might use???

---

### Post by jan quark on 2008-02-02
I don't know but perhaps this will help you

[http://janquark.fatfreehost.com/tutorial2.html](http://janquark.fatfreehost.com/tutorial2.html)

once I set up my pc as a server and I could access the files I put into the folder through the internet, in this summary I explain what I have done
but unfortunately this worked only when the pc set up as the server was on power

---

### Post by wormser on 2008-02-02
Using ssh would accomplish this task.  You will need to install openssh-server and firestarter.  Use firestarter to open port 22 for the ssh server.  You will also have to [port forward]("http://portforward.com/routers.htm") your router to port 22.  You did not say what type of computer you would be connecting from.  If it is a windows machine then you need putty.  In linux you can use the shell (terminal) and the ssh commands.  Give us some more information and details of what you are exactly trying to do to get more specific answers.

---

### Post by Indystev on 2008-02-02
Wow! Thanks for the responses...

What I am trying to accomplish is twofold.
I want to be able to access my Windows boxes while I am traveling.
I have multiple files that are a huge help to me while I am away, but I do not want to have local copies on my laptop.
The laptop is a windows box as well...

Secondly, I would also like to use the linux box as a web surfing proxy.
The network at work is protected by websense and it does not allow certain websites to be accessed... ie fox sports... ebay.. cnn.. ubuntu.org  etc.

I would like to tunnel into my own network to reach the net from work.

Apache.. Openssh... squid... I have heard all the terms but am unfamiliar with their capabilities and uses.
I am open to all.
I may want to even use this box as a web page host too.
As I stated before, I have a domain name, and a domain dns updater, so I think I may be a third to half way there.

Thanks for all the help!!:guitar:

---

### Post by wormser on 2008-02-02
I can help you with the proxy part.  There are a bunch of steps but this will get you in the right direction.  You need to set up your Ubuntu box at home with firestarter, ssh server and port forward the router.  I am assuming this is an XP box at work.  You will have to install putty on the XP box.  You will have to figure out how to input the command into putty.  The command in linux is ssh -D 9999 user@domain.  In firefox (not sure where in IE) Edit> Preferences> Advanced> Network tab> Settings> Manual proxy configuration> SOCKS _v_5, SOCKS Host: localhost and No Proxy for: localhost, 127.0.0.1.  Now you are surfing the net with a tunnelled connection.

---

