---
title: "Can Only surf one website"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by rrkryder on 2006-04-13
I have an 8 year old Presario laptop. 
Recently, my windows 98 crashed and I lost my backup copy.
A friend of mine had given me a copy of Breezy, so I installed it.
Now it seems I can not surf the 'net except for this forum site. 
I am using a PCMCIA wireless card. 
It took me a while to even find and activate my wireless network connection, but I did. It says it is active, and that I have 75% signal.
But this forum seems to be the only site that doesn't time out.

---

### Post by echo $USER on 2006-04-13
[QUOTE=rrkryder]I have an 8 year old Presario laptop. 
Recently, my windows 98 crashed and I lost my backup copy.
A friend of mine had given me a copy of Breezy, so I installed it.
Now it seems I can not surf the 'net except for this forum site. 
I am using a PCMCIA wireless card. 
It took me a while to even find and activate my wireless network connection, but I did. It says it is active, and that I have 75% signal.
But this forum seems to be the only site that doesn't time out.[/QUOTE]

That's wierd.  Try pinging other sites by name and by ip, see what happens.  And other PCs in your network.

---

### Post by rrkryder on 2006-04-13
I do not know how to ping a site with Linux.
Also, I don't know any of the IP's for the webites that I frequent.
There is another computer that I could log on to that uses Windows....It is my roomates. I will boot his computer, and find his IP address.
After that, I don't know how to ping.

---

### Post by dermotti on 2006-04-13
Try setting a static DNS address.

---

### Post by rrkryder on 2006-04-14
I know where to go to do that, but I don't know *how* to do that.
When I select the static option, It seems to want me to fill in some IP addresses in some blank fields.

---

### Post by enopepsoo on 2006-04-14
To ping a site just use the ping command 

```
ping ubuntulinux.org
```

But it helps to use a -c switch so that it wont ping forever, so

```
ping -c 2 ubuntulinux.org
```

Other ways of getting the ip exist, like whois and nslookup:

```

whois ubuntulinux.org
nslookup ubuntulinux.org
```

---

### Post by rrkryder on 2006-04-14
ok, I pinged a number of sites.
each time, two packets transmitted, two received.
I tried a whois on my friends website, wow that gave me a lot of info.
Anyways, I still can't navigate to any sites other than this one.
It just times out.

---

### Post by Qrk on 2006-04-14
The terminal, which is Applications->System Tools->Terminal

---

### Post by rrkryder on 2006-04-14
ok, I have pinged a number of sites successfully in the terminal.

This forum site is still the only site that doesn't time out on me here in Firefox.

---

### Post by Mustard on 2006-04-14
It's an interesting problem. I'm sure I have seen it talked about before.  If you do a search around on the forum you might get lucky and stumble on a thread that deals with the same issue (and I can certainly recall reading something about this before).

---

### Post by Qrk on 2006-04-14
It could be a Firefox issue only. Try going to the "add/remove Applications" at the bottom of the applications menu, and install Epiphany web browser.

---

