---
title: "IP block"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by rockinlinux on 2008-02-04
I am looking for a way to block my IP address. something like this: [http://phoenixlabs.org/](http://phoenixlabs.org/) but for linux...

any hep would be great! thanks in advance!

---

### Post by LowSky on 2008-02-04
this link might help

[http://ubuntuforums.org/showthread.php?t=10825&highlight=tor](http://ubuntuforums.org/showthread.php?t=10825&highlight=tor)

---

### Post by rockinlinux on 2008-02-04
I found this : [http://www.ubuntugeek.com/ipblock-graphical-ip-blocker.html](http://www.ubuntugeek.com/ipblock-graphical-ip-blocker.html)

Im not sure if it what i want though....
I like that link you gave me...i just worry it will mess wth my lamp stack i use for a test server.

---

### Post by mikewhatever on 2008-02-04
> **rockinlinux said:**
> I am looking for a way to block my IP address. something like this: [http://phoenixlabs.org/](http://phoenixlabs.org/) but for linux...

any hep would be great! thanks in advance!

Hope you are not serious. Why would you want to block your own IP?

---

### Post by stchman on 2008-02-04
> **rockinlinux said:**
> I am looking for a way to block my IP address. something like this: [http://phoenixlabs.org/](http://phoenixlabs.org/) but for linux...

any hep would be great! thanks in advance!

Are you wanting to do this while surfing the web?  If yes then you need a proxy server.  I warn you, most free proxy servers are very slow.

---

### Post by rockinlinux on 2008-02-04
there are reasons i dont really want to get into for blockin my IP, but one reason is simply safty and secutiy. Not really while surfing the web, im not woried about that...more about uploading and downloading files.

---

### Post by billgoldberg on 2008-02-04
Using encryption for p2p and torrents is a must.

If you want to block ip's, I suggest you try to find out what ip's pheonixlab's program blocks and add those to:

/etc/hosts

That way they are blocked.

---

### Post by rockinlinux on 2008-02-04
Yes, that is a mian reason i need this...what about the link i posted?

---

### Post by stchman on 2008-02-04
> **rockinlinux said:**
> Yes, that is a mian reason i need this...what about the link i posted?

Then a proxy is what you want.  Unless you pay for a good proxy be prepared for slow transfers.

---

### Post by rockinlinux on 2008-02-04
found this too...anyone used it?

[http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

---

### Post by rockinlinux on 2008-02-04
what would be a good proxy?how much are they? and would it mess with my LAMP stack I use on my computer as a test server?

thanks :)

---

### Post by billgoldberg on 2008-02-04
this link might be usefull

[https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

it seems you can't use it if you use firestarter.

---

### Post by max renn on 2008-02-04
I plan to switch my p2p box to Linux this week and have spent some time to research p2p ip blocking.  Several alternatives are currently available.

1. moblock is the official phoenix labs version of peerguardian.  The linux version of peerguardian is not supported anymore, so they invited the moblock dev to replace it.  To me, it does not look like a simple install, but it does do what it is supposed to do.

2. Relakks and other such servers are available that offer true p2p proxying (hide your ip by using theirs.  These cost a monthly fee (US$10 - $30).

3. Get a p2p friendly shell acct and p2p to that server, then download to your local drive.  Personally, if I went the shell route, I would also setup my own proxy.

Additionally, I figured it would be best to go with a server solution offered outside the US, since ISP's, etc. are doing their best to bend over backwards and offer privacy information to the authorities.

Good luck.  Let me know how it goes...

---

