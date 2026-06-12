---
title: "Port Forwarding. Am I doing something wrong?"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by TekMuzik on 2007-03-12
I've been using uTorrent on Windows for quite a while with no problems with the port forwarding, but now using Deluge on Ubuntu 6.10, it says it can't open any of the ports for listening. 

I have Ubuntu set to a static IP of 192.168.1.3 which seems to be working fine. I have deluge set to try ports 45456-45456 TCP. I have my Linksys WRT54G router set to forward port 45456 TCP/UDP to 192.168.1.3. The setup worked fine in Windows, but apparently not in Ubuntu. Is there another step I need to do for Linux that I'm missing?

---

### Post by TekMuzik on 2007-03-12
*One bump*
No one?

---

### Post by pt123 on 2007-03-16
You could try uTorrent on Wine works perfectly for me. You have to turn of UnP though.

---

### Post by dannyboy79 on 2007-03-16
bittornado is the greatest bittorrent client, windows or linux for me anyway. you can even use automatix to install it if you're  not comfortable installing from source. BUT you do have a point, port forwarding is pretty easy and you have stated everything pretty much right on the money. are you sure that your iptables doesn;t have any rules blocking you?

sudo iptables -L

will show you any rules.

bittornado is easy to use, you simply double click on a torrent and it opens a window asking where to save files and that's it. then if you want another torrent, you just double click another one, and it opens a new bittornado download window. they look like this:


[IMG]http://img241.imageshack.us/img241/5332/bittornadopr4.png[/IMG]

[http://www.bittornado.com/](http://www.bittornado.com/)

---

### Post by zanglang on 2007-03-16
Can't open any ports for listening? Is that the actual error message, or just an error you get if you try to NAT test Deluge? That sounds more like you have another application hogging the port.

Also if you liked uTorrent a lot you might want to try running it on Wine. It runs quite well. ;)

---

### Post by pt123 on 2007-03-17
The problem with Bit Tornado it creates individual windows for each torrent. It is also banned on many private torrent sites.

---

### Post by dannyboy79 on 2007-03-19
what's the problem with individual windows? also, it's NOT banned on the awesomest hottest torrent site that always has the best downloads!! invite only sorry, and I am not suppose to tell anyone what the site is so please don't ask. good luck with whatever you chose.

---

### Post by dorcssa on 2007-03-19
> **pt123 said:**
> You could try uTorrent on Wine works perfectly for me. You have to turn of UnP though.

Well, it is almost perfect, I cannot become activ, no matter what I try(I portforwarded the port on my router and on firestarter too). I think the router is not quite good, but it worked with upnp port mapping(and only with that, if I turned it off, there was a NAT problem) on windows.

---

