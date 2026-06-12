---
title: "Frostwire connections"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-11-01
I finally got Frostwire installed after a huge difficulty and having to reconfig Java. Well, now that I finally have it installed correctly and running, it won't find any connection. It merely sits there and says "Starting Connection" forever. I have tried waiting, tried going into the preferences, but can't find anything about the connections. Please help. Oh and I'm using dapper.

---

### Post by rozojc on 2006-11-01
I'm having exactly the same problem. I also noticed it says that it's behind a firewall (It's NOT), help please? There are also another coupld of posts regarding this from other users!

---

### Post by skydivingbiker on 2006-11-02
this is happening to me too.  Only.. we have 3 logins for this PC.  All of our Java settings are the same, everything seems to be exactly the same.

With 1 login, it connects and works fine.

The other login... says its behind a firewall when its not.  Just says starting connection ](*,)

---

### Post by floridauser007 on 2006-11-02
> **skydivingbiker said:**
> this is happening to me too.  Only.. we have 3 logins for this PC.  All of our Java settings are the same, everything seems to be exactly the same.

With 1 login, it connects and works fine.

The other login... says its behind a firewall when its not.  Just says starting connection ](*,)

FWIW, I have been having the same problem but have yet to research or try to fix it much yet.  I believe it uses gwebcaches and needs to connect to these.  It is possible that the caches coming with the distribution are down.  PErhaps we should try updating them or manually specifying some?

---

### Post by rozojc on 2006-11-02
Only problem for me is that I don't even know what gwebcaches are (ooops)... If you try it pls post back with instructions :-)

---

### Post by floridauser007 on 2006-11-02
> **rozojc said:**
> Only problem for me is that I don't even know what gwebcaches are (ooops)... If you try it pls post back with instructions :-)

A gwebcache is used by the gnutella network (what Limewire and frostwire work over) basically to introduce you to others also on the network.  See you have to be able to connect to at least one other person or you will never get connected to anyone.  The webcahce keeps a list of all the IPs accessing it and when your computer connects to it, it will say give you the IPs and ports of the last fifty who connected.  (Actually it isn't this simple as it uses ultrapeers, but blah blah you get the point) 

[here are more details: [http://www.the-gdf.org/index.php?title=Bootstrapping](http://www.the-gdf.org/index.php?title=Bootstrapping)  You don't have to read this as it is beyond the scope of a user!  But if you are interested in what a webcache is, here you go.]

I'm not sure this is the problem though.  I went to their forums and looked and couldn't find any working solutions.  I have no firewall (software or hardware) or router, run other p2p programs like bittorrent just fine, and am also having the "starting connection" problem. I was looking through the options to see if there was an easy way of changing or updating the gwebcaches used, but couldn't find anything.  Sorry... :(  I will look into it later when I have more time.  Hopefully we can find a solution!  In the mean time you might want to check Synaptic (System -> Administration -> Synaptic package manager) for a program called Apollon which works over the same network as frostwire and limewire.

---

### Post by peterboy on 2006-11-20
Before you begin make sure frostwire is not running.  Navigate to the folder where you installed frostwire eg: /home/username/.frostwire (make sure you have show hidden files selected) you will find a file called gnutella.net If it is not there just create it (in my version of mepis you can do this by right clicking and select create new text file) add these files by copying and pasting them [http://mc3.electronicbox.net/gnutella.net](http://mc3.electronicbox.net/gnutella.net) then save and exit restart frostwire and you should be connecting in seconds. Hope this helps.  This is not my solution it is posted on [http://www.frostwire.com/forum/viewtopic.php?t=666&postdays=0&postorder=asc&&start=15](http://www.frostwire.com/forum/viewtopic.php?t=666&postdays=0&postorder=asc&&start=15)
Just thought I would rewrite it because some of it concerns settings for windows etc.

---

### Post by vierranet on 2006-11-21
Code:

sudo gedit /usr/bin/frostwire

and change 'sh runFrost.sh' to 'bash runFrost.sh'

this will solve your problem

---

