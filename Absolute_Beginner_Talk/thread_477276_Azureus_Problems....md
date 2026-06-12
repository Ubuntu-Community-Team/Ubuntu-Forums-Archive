---
title: "Azureus Problems..."
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by onero on 2007-06-18
Hi, I'm using Azureus 2.5.0.4 on Feisty. Azureus used to work perfectly, but a few weeks ago, seemingly out of the blue, I couldn't connect to any tracker at all. I keep getting Connection Error (Timed Out). I can still download files because of DHT, but that's the only way I get to download torrents.

I'm pretty sure the port it uses is open, and I have port forwarding set up. NAT is also OK. As mentioned, my setup was working previously and I haven't really changed anything. I ignored it for some time since I was still able to download most torrents with reasonable speeds, but it's getting a bit annoying because there are certain sites wherein I can't download anything at all.

Is there any bug or issue similar to this documented for Azureus? Or could you suggest a way I can diagnose what's wrong with my network? Thanks!

---

### Post by fakie_flip on 2007-06-18
I don't use Azureus, but you could try Ktorrent.

sudo apt-get install ktorrent

---

### Post by onero on 2007-06-18
Hi, I tried KTorrent and configured it to use the same port for TCP and UDP, but it still doesn't connect to the tracker. I get the error: "Timeout on server: Connection was to ******* on port 6969". The 6969 port isn't the one I have configured, though. Are there any other settings I need to change? Will it make a difference if I try another port?

---

### Post by onero on 2007-06-21
Meh, it is a firewall problem after all, everything worked almost immediately once I turned the router firewall off. Ah well, I guess I'll have to dig around to see what I did wrong. Any tips on what I need to check for? I mean, I just have to open the ports I use for Azureus right? But they're already open, so I don't know what to check next. I guess I could just disable the firewall, but I'd rather not :)

---

### Post by neo.patrix on 2007-06-21
there are many unknown problems with azerus, secondly more important azureus is java-based, always troubled with memory-bottleneck and many java applications are not good with reading / writing files. 

Since downloading torrents is file operation intensive task , it is best to avoid anything java based. Also azureus does not does not give reasonable speeds. I would advice you to use BitTorrent Client or BitTorrnado both are present in ubuntu repository. Gui is not good for this applications like azureus but it is upto the task and much stable.

You can also try Deluge , bu it is not stable , atleast for me, it worked very well for few days and then one fine afternoon crashed and never worked again. You can download it from
[http://www.deluge-torrent.org/](http://www.deluge-torrent.org/) . I think they have got debian packages for edgy and feisty

---

### Post by onero on 2007-06-21
I tried KTorrent yesterday, and it also exhibited the same problem as Azureus, so I don't think it's a client-specific problem. And when I turn off my firewall the problem disappeared. Ah well. 

Anyone want to recommend some utilities to help check what's being blocked when the firewall is on? Networking isn't really my strong point :D

---

### Post by diatribe on 2007-06-21
I guess you could maybe download a portscanner and see what is open when your firewall is up?

---

### Post by kelvin spratt on 2007-06-21
Do a port forwarding check in Azureus that will tell you if the ports are open its easy to change the ports
but there is 1 they tell you not to use i use 61401 and max out most of the time its the same port i used for the Blue Frog. if you are using a router you don't need a fire wall. if your not then your firewall is blocking the port, don't ask me about the firewall settings as i use a router if you use a router goto,
[http://portforewarding.com/](http://portforewarding.com/) search their site you will find every router listed and all the clients with step by step instructions.

---

