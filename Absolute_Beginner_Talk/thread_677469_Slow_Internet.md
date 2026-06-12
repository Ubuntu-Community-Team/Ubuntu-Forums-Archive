---
title: "Slow Internet"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by motion parallax on 2008-01-24
I'm new to Linux and new to Ubuntu.  Just installed a dual boot with Vista and Unbuntu and I love it.  The community here is amazing, and I've already spent over ten hours reading here in the past two days.  

I'm having trouble with slow loading of web pages in Firefox, Epiphany, Opera, and Swiftfox.  I disabled Ipv6, changed various settings within Firefox, downloaded the Fasterfox Add-On, still nada.  

My download speed is terrific, with Synaptic downloads averaging 500kb, bittorrent downloads at one point reaching 1.2 mps.  Outstanding.  

I've read over thirty threads about this problem, and the only recommendation found that I haven't tried is changing the DNS settings, shown here:

[http://ubuntuforums.org/showpost.php?p=3796434&postcount=3]("http://ubuntuforums.org/showpost.php?p=3796434&postcount=3")

I'm not really sure how to do this.  Could somebody help me translate this?  Or tell me if it's the absolute wrong thing to do?

Thank you all.

---

### Post by blueridgedog on 2008-01-24
Well, if you think it is DNS, just open a terminal and type:

ping [www.coke.com](www.coke.com)

(or any other domain/website).  If you get an IP address immediately, it is not DNS.

Also, switching to the DNS servers referred to in your link may not work as they may not allow hosts outside of their network to use their services.

---

### Post by emarkd on 2008-01-24
You can edit the files by running

```
sudo gedit filename
```

from the terminal.  BUT!!:  before you go and start editing these important system files, MAKE SURE you have a backup.  For instance, before editing your /etc/resolv.conf file, you should

```
sudo cp /etc/resolv.conf /etc/resolv.conf.bak
```

That will make a copy of the resolv.conf file and name it resolv.conf.bak.  Now if you have a problem you can simply restore the file by running the command backwards:

```
sudo cp /etc/resolv.conf.bak /etc/resolv.conf
```

As for this being a good idea, I have no idea, but I hope it works for you.

---

### Post by motion parallax on 2008-01-24
Tried the ping and the result was almost immediate.  Now I'm stumped.

---

### Post by SomethingCronic on 2008-01-25
> **blueridgedog said:**
> Well, if you think it is DNS, just open a terminal and type:

ping [www.coke.com](www.coke.com)

(or any other domain/website).  If you get an IP address immediately, it is not DNS.



DNS is cached. If you've been to [www.coke.com](www.coke.com) before then this won't work. I don't know if ping is a good indication of DNS speed anyway.

I'd look up some alternative DNS servers and add them to resolv.conf if you think that's what the issue it.

---

### Post by blueridgedog on 2008-01-25
I deliberately suggested a site I doubted the OP had been to.  If ping resolves an IP more or less instantaneously and it is one that is not cached, why would you suspect a DNS problem?

---

### Post by Golem XIV on 2008-01-25
I had problems with slow DNS lookups on several Ubuntu systems that I installed.  Browsing is slowed down to a crawl, though download speed - once the connection is established - is fast and reliable.  The symptom that I noticed is that every time I would click on a link, Firefox would go "looking for site www.whatever.com".

I solved it by following [these instructions]("http://ubuntuforums.org/showthread.php?t=331850")

It's relatively simple both to implement and to get rid of in case it doesn't fix your problem or you don't like it.

Good luck!

---

