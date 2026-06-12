---
title: "can only load webpages with ip"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by mhl12 on 2007-01-29
I can only load web pages via ip address. [http://216.239.57.99](http://216.239.57.99) works but [http://google.com](http://google.com) doesnt.

I read here: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-1b12c0a8c765a0d0d623e3ee60daf197a5bf2b59-2](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-1b12c0a8c765a0d0d623e3ee60daf197a5bf2b59-2)
that it's a DNS issue. So I follow it's instruction:

```
cat /etc/resolv.conf
```

and I get:

```
nameserver 192.168.0.1
```

That happens to be my router ip as well. From there, I don't know what to do. Any help would be appreciated. Thanks.

---

### Post by sauravbhaumik on 2007-01-29
> I can only load web pages via ip address. [http://216.239.57.99](http://216.239.57.99) works but [http://google.com](http://google.com) doesnt.

I read here: [https://help.ubuntu.com/community/Wi...f197a5bf2b59-2](https://help.ubuntu.com/community/Wi...f197a5bf2b59-2)
that it's a DNS issue. So I follow it's instruction:

When type something like "http://google.com", you should have known the blunder you've done. It should have been [http://www.google.com]("http://www.google.com") instead.

---

### Post by Zzl1xndd on 2007-01-30
> **sauravbhaumik said:**
> When type something like "http://google.com", you should have known the blunder you've done. It should have been [http://www.google.com]("http://www.google.com") instead.

[http://google.com](http://google.com) also works. This is most likely as said a DNS error. 

Question mhl12 has this always happened with ubuntu or just started?

---

### Post by l951b951 on 2007-01-30
> **tweakedenigma said:**
> [http://google.com](http://google.com) also works. This is most likely as said a DNS error. 

Question mhl12 has this always happened with ubuntu or just started?

I agree, this looks like a DNS server problem.  The "www" is a 3rd Level Domain, and almost all DNS servers can point you to the website whether you add www or not.

---

### Post by Zzl1xndd on 2007-01-30
If it just started then its probably an issue on your ISP's End although you can change you DNS servers in your router by logging in and if its a Linksys router the DNS option should be on the first page. I use Open DNS as its independent of my ISP's DNS there server is 208.67.222.222

---

### Post by rccharles on 2007-01-30
> **mhl12 said:**
> 

```
cat /etc/resolv.conf
```

and I get:

```
nameserver 192.168.0.1
```

That happens to be my router ip as well. From there, I don't know what to do. Any help would be appreciated. Thanks.

You have found the correct file to change. 

You need to contact your ISP and find out the address of your DNS.  Sometimes they include the info on their web page. Sometimes your router gets the name dynamically and you can look there.

Do you have another machine that works?  If so, look there for the address.

To change, type:

sudo nano /etc/resolv.conf

change the 192.168.0.1 to what your ISP provides.  You can have more than one nameserver line in the file.

Robert

---

### Post by mhl12 on 2007-01-30
> **tweakedenigma said:**
> [http://google.com](http://google.com) also works. This is most likely as said a DNS error. 

Question mhl12 has this always happened with ubuntu or just started?

I had to install madwifi first to get ubuntu to recognize my card. After that, it does recognize it and I do get a signal but I cant connect to the internet.

[QUOTE=rccharles]You have found the correct file to change.

You need to contact your ISP and find out the address of your DNS. Sometimes they include the info on their web page. Sometimes your router gets the name dynamically and you can look there.

Do you have another machine that works? If so, look there for the address.

To change, type:

sudo nano /etc/resolv.conf

change the 192.168.0.1 to what your ISP provides. You can have more than one nameserver line in the file.

Robert
Reply With Quote[/QUOTE]

yes I have my desktop that runs Windows XP. That's hooked up directly to my router. My router is hooked up directly to my cable modem. Would I be able to find my dns address through that?

my isp is Optimum Online

---

### Post by linuxpimp on 2007-01-30
Hi

Have a look at 

[http://ubuntuforums.org/showthread.php?t=349292](http://ubuntuforums.org/showthread.php?t=349292)

Sounds like the same issue

lp

---

### Post by mhl12 on 2007-01-30
I already tried that. It did not solve my problem.

It seems I have to change my dns server. Is there a way to find my dns server using my desktop or do I have to call my isp?

---

### Post by highneko on 2007-01-30
> **rccharles said:**
> change the 192.168.0.1 to what your ISP provides.  You can have more than one nameserver line in the file.


That file has my routers address in there and i'm having no problems.

mhl12: If it's a router problem then you could maybe reset the router settings? I suggest password protecting the router so nobody can mess with the settings but you.

---

### Post by mhl12 on 2007-01-30
I already reset my router settings a whole bunch of times. And my network is protected with WEP.

Also, when I go to the wirless network properties and where it says network password, is that asking my for WEP key or my password I use to connect to the network?

edit: under my router settings, it does show my laptop connected to the network.

---

### Post by rccharles on 2007-01-30
> **mhl12 said:**
> 
yes I have my desktop that runs Windows XP. That's hooked up directly to my router. My router is hooked up directly to my cable modem. Would I be able to find my dns address through that?

my isp is Optimum Online

I do not have a working Windows system.  From what I remember, you have to go to the control panel.  There should be an icon for networking.  There are four or five panels.  Look around.  

I suggest you call your ISP to find out the DNS address.

...

I think whether or not your router provides a DNS service depends on how you configure it.

Robert

---

