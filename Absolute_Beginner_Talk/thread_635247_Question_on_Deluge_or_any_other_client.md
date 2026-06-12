---
title: "Question on Deluge or any other client"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by bgast1 on 2007-12-08
Why am I only getting 5.5 KiB/s downloading a torrent using Deluge? Seeders says 2(20) Peers says 15(7). Up until now nothing else was consuming my bandwidth. I am  currently seeding one other torrent but no one is uploading from it at the time. 

Hope it isn't Comcast's fault.

---

### Post by ingvildr on 2007-12-08
Do you have your ports forwarded, if you have a router or firewall?, also are you using deluge from the Ubuntu repositories or from the deluge website?

---

### Post by bgast1 on 2007-12-08
I am using a route. A Network Everywhere NR041. I got my Deluge from Synaptic.

 I don't know how to forward my ports. In Windows,O actually had a program that did it for me. I used E-mule in windows and loved it. Also used Bit-Torrent a bit.

Also, perhaps I knew how to set my preferences would help as well. I haven't even a clue.

---

### Post by ingvildr on 2007-12-08
I would use the one from the official site [http://deluge-torrent.org/]("http://deluge-torrent.org/") i dont usually use packages outside of what is official ubuntu but i too was getting slow speeds with the deluge in the repositories.

About setting it up, go to Edit > Preferences > Network and change settings there. Attached is a screenshot of my prefs and i get around 450 - 500 (my max speed) on most popular torrents.

---

### Post by bgast1 on 2007-12-08
I have the new version of Deluge now. I think it was the same version as in the repos though. Still I went and got it from the site. Made sure my settings were the same as in the screenshot. My speeds are slower now. What about the other settings, do they make a difference. People can upload faster than I download.

---

### Post by pHreaksYcle on 2007-12-08
[www.portforward.com](www.portforward.com)
you HAVE to go there. I used it on my Belkin N1 and it worked like a charm. Beautiful setup with screenshots and such to make it idiot proof. It even shows what ports to forward for different applications like first person shooters and other games. Hope it works and have fun!

---

### Post by bgast1 on 2007-12-08
Deluge isn't listed there.

---

### Post by Arthur Archnix on 2007-12-08
It's probably comcast. They are known to be throttling torrents. Look for ftp, http, or perhaps tor based sharing options. Or another ISP. Deluge encrypts by default, but you may also want to look at trying other ports, or disallowing non-encrypted traffic.

---

### Post by bgast1 on 2007-12-08
I tried to go to [www.portforward.com](www.portforward.com) but go nowhere. Deluge isn't listed there. Linux isn't listed where I go to set up a static IP address. Only different versions of Windows. I have absolutely no clue what I am doing. Just that my downloads are very slow, and the when I do the test, my ports are closed.

---

### Post by Ub1476 on 2007-12-08
You will have to enter your local IP address into the address field in Firefox to access your routers settings page.

Type in "ifconfig" into the terminal and look for "inet addr: xxx.xxx.x.x"

Like this:

```
inet addr:192.168.1.1
```

If you are prompted for a username&password, it's usually blank in the username field and "admin" in password.  

Now navigate to something like "Applications and Gaming">Port forward. 

Enter a port you want to open.

In Deluge click Edit>Preferences>Network>Enter the port you opened. 

You can also control ports with Firestarter. It's in the repos.

BTW, when I test ports, mine says they are closed too. Yet I sometimes get a speed on about 100-500 kb/s. I suggest you use a popular movie as testing;)

---

### Post by Arthur Archnix on 2007-12-08
bgast, before going to the trouble of forwarding your ports, just try bypassing the router altogether. That is, disconnect the router connect directly to the net. Are your speeds better?

---

### Post by pHreaksYcle on 2007-12-08
Yeah dude, you are not opening a certain port, you are opening any port you select. There is no specific deluge port, you just open one and insert it into the deluge settings...very easy

---

