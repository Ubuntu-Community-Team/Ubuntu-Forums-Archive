---
title: "[SOLVED] Possible to install bypass censorship tools on Ubuntu?"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by al.adab on 2008-03-27
hello,

I'm wondering if tools such as Freshmeat or Hotspot shield are available to Linxu users (Ubuntu) e who live in internet censoring countries (like in parts of the Middle East where anything - be it a porno site or an academic article - cannot be access if it contains the word "Israel", for instance). I tried Tor, but it looks like this has too been blocked. 

Thanks.

---

### Post by Malta paul on 2008-03-27
Perhaps our Ubuntu forum is not the site to give details of how to bypass censorship.
The censor can usual be bypassed with any computer operating system. Just check the internet and you will find out how! Here is a site you can  also check out: [http://www.rsf.org/rubrique.php3?id_rubrique=111&id_mot=887](http://www.rsf.org/rubrique.php3?id_rubrique=111&id_mot=887)
Good luck anyway.

---

### Post by Dr Small on 2008-03-27
Unless they have blocked every tor node, (which is highly improberable) then Tor should work.

Dr Small

---

### Post by heartburnkid on 2008-03-27
> **Malta paul said:**
> Perhaps our Ubuntu forum is not the site to give details of how to bypass censorship.

Why's that?  Linux is all about software freedom, which depends on freedom of speech and freedom of information, right?  This should probably go in the Community Cafe forum, but other than that, I think it's a perfectly reasonable topic for us to discuss.

al.adab, you might try following [these instructions](http://en.wikibooks.org/wiki/Bypassing_Internet_Censorship/Proxy) to use Princeton University's proxy server.  Let us know if that works.

---

### Post by al.adab on 2008-03-27
Thanks both. Tor doesn't work in the UAE (at least on my machine, and the only test I run to see if Tor is running is to switch it on/off on firefox at [http://whatismyip.com/](http://whatismyip.com/)
And by the way, this forum might not be the place where by-passing censorship should be discussed, but it appears to be the place where software installation on Linux can be discussed (unless I got it wrong from the very beginning), and in this respect I feel that my question hasn't really been  discussed/answered.   
Thanks for the RWBs handbook anyway. It looks very interesting.

---

### Post by heartburnkid on 2008-03-27
Glad to help however I can.  Unfortunately, I can't speak to the particular software packages that you're talking about, or alternatives to them, as I'm fortunate enough to not need them.

Another option: have you tried running Freshmeat or Hotspot under WINE?

---

### Post by al.adab on 2008-03-27
Thanks both. Tor doesn't work in the UAE (at least on my machine, and the only test I run to see if Tor is running is to switch it on/off on firefox at [http://whatismyip.com/](http://whatismyip.com/)
And by the way, this forum might not be the place where by-passing censorship should be discussed, but it appears to be the place where software installation on Linux can be discussed (unless I got it wrong from the very beginning), and in this respect I feel that my question hasn't really been discussed or answered.   
Thanks for the RWBs handbook anyway. It looks very interesting.

---

### Post by MONODA on 2008-03-27
letmeby.com
proxy14.com
vtunnel.com

---

### Post by al.adab on 2008-03-27
thanks heartburnkid.

Could you please have a look at a screenshot of my connection settings on firefox. I tried to follow the directions given at [http://en.wikibooks.org/wiki/Bypassing_Internet_Censorship/Proxy#Mozilla_Firefox](http://en.wikibooks.org/wiki/Bypassing_Internet_Censorship/Proxy#Mozilla_Firefox) but it didn't work (maybe I did something wrong? I modified the line at HTTP proxies, but left the rest unchanged). 

Also I don't know how to download hotspot and run it under wine. I actually tried to download hotspot (I've got wine installed) but all I got in my home folder was some strange index file. 

And by the way, I can't get to freshmeat. The site is blocked...

---

### Post by al.adab on 2008-03-27
...sorry the screenshot hasn't uploaded. Here it is.

---

### Post by heartburnkid on 2008-03-27
Offhand, I'd say the problem is that you're trying to use localhost as a proxy.  Localhost is your computer, so your requests aren't really going anywhere.  This may have been a leftover from when you tried to use Tor; that does act as a local proxy, but since that's not working for you, we need to change it.

Make sure to use the address and port number given in the guide.  So, under http-proxy, put in planetlab-10.cs.princeton.edu, and in the port box next to that, put in 3128.  Clear the boxes for SSL Proxy and SOCKS Host, then click OK and try again.

---

### Post by al.adab on 2008-03-27
Thanks MONODA. 

FYI: 
letmeby.com and vtunnel.com are blocked sites. 
proxy14.com is seen as highly unsafe locally.

---

### Post by Malta paul on 2008-03-27
Try using Firefox [https://addons.mozilla.org/en-US/firefox/search?q=tor&cat=12](https://addons.mozilla.org/en-US/firefox/search?q=tor&cat=12)
Down load 'Tor-Proxy.net Toolbar'.
Try using the left hand Item first
Good luck:)

---

### Post by jordanmthomas on 2008-03-27
This may be a dumb question, but do you have tor and privoxy installed / running?
If not, you'll want to install them and add this to the end of /etc/privoxy/config
```
forward-socks4a / localhost:9050 .
```

@heartburnkid, this is how privoxy and tor work.  It sets up a local proxy to the tor network.

---

### Post by al.adab on 2008-03-27
heartburnkid, it doesn't work. I inserted the line at HTTP as suggested, got rid of everything else (although I'm still left with having to choose between socks v4 and v5 > I left v5 on) and the box under the HTTP line unchecked. 

Also thanks Malta paul, I downloaded the proxy bar, here are two screenshots of what I get if I try to click on the icon on the left (that which looks like an eye), the FAQ (on the right), and any of the two in the middle, respectively. That's life around here...

---

### Post by al.adab on 2008-03-27
thanks jordanmthomas  

I did what you suggested, and now I can't surf the net any longer if I have Tor enabled on Firefox. Is that good news or bad news? :) Is there anything I should now do?

---

### Post by al.adab on 2008-03-27
CORRIGENDUM: 

I included *forward-socks4a / localhost:9050* in the file end of /etc/privoxy/config (and not forward-socks4a / localhost:9050 .) and now I can surf through when TOR is enabled. The WWW around here remains as censored as ever, though...I'm going to re-post this elsewhere at Linux (can't remember where right now), as someone suggested.

---

### Post by Malta paul on 2008-03-27
Now I'm at home from work I can answer you better!
I meant click on 'by JAP/jonDos' sorry to mislead you. When the proxy server works it takes some time as it routes all over the place. You should be able to brows normally without using the proxy.
Here is some info you might like  to read :
[http://www.torproject.org/overview.html.en](http://www.torproject.org/overview.html.en)
[http://www.freeproxy.ru/en/](http://www.freeproxy.ru/en/)
You can test your IP adress with:
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)
[http://www.all-nettools.com/toolbox](http://www.all-nettools.com/toolbox)
Have fun :)

---

### Post by al.adab on 2008-03-27
many thanks Malta paul for your support. I really appreciate this.

I'm afraid also the two links

[http://www.torproject.org/overview.html.en](http://www.torproject.org/overview.html.en)
[http://www.freeproxy.ru/en/](http://www.freeproxy.ru/en/)

are blocked over here...any suggestion? I checked the other two (check your IP) but don't really know if they're useful at all at this stage (since I don't know what the above sites suggest).

If I click on "by JAP/JonDos, I get the following

CGIProxy Error
The target URL cannot contain an empty host name.

I'm really lost at this stage. What do you advise? Thanks again.

---

### Post by Malta paul on 2008-03-27
Just a thought, Did you put the web site you wished to visit tn the slot to the left of 'by JAP/jonDos'  before Clicking?

---

### Post by al.adab on 2008-03-27
NO! I DIDN'T!!! Now it works!!! Thank you so much!!! I feel a bit stupid I couldn't figure that out myself - hope I'm excused since I couldn't access the relevant info. Now I can even access the FAQ on the toolbar. Thanks tons again.

---

### Post by Malta paul on 2008-03-27
Hi, Thanks also for your private message, keep in touch.
I am very happy you cracked your problem, thats what our community is all about! :guitar:

---

