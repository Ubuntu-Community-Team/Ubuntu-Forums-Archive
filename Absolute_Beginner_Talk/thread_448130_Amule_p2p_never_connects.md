---
title: "Amule p2p never connects?"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by discmaster on 2007-05-18
I have been working with Amule for several days, & no go; It always says - Not Connected: Kad off. & "No valid servers found in server list".

Anyone else have this problem?

---

### Post by earobinson on 2007-05-18
This seemed to happene every once is a while with amule so I switched fo frostwire.

---

### Post by discmaster on 2007-05-18
> This seemed to happene every once is a while with amule so I switched fo frostwire lol

Yeah, well my frostwire isn't working either! Guess I am striking out there...
Running beryl, seems to conflict w/ frostwire. I am using gtk-gnutella, but the return search results aren't very good.

---

### Post by earobinson on 2007-05-18
Hum, when it happened to me im pretty sure it was a server issue not an amule issue since I had to boxes that would have the problems at the exact same times.

---

### Post by discmaster on 2007-05-18
I was looking at DC++, but looked too complicated for a new linux user like me!

---

### Post by dodgePT on 2007-05-18
You've got a modem/router right?
Did you port forward it?

---

### Post by earobinson on 2007-05-18
DC is easyer imo

---

### Post by discmaster on 2007-05-18
> You've got a modem/router right?
Did you port forward it? Cable modem & router... Don't quite know what U mean by "port forward". I thought it would be configured to run right from the start like most others...

---

### Post by discmaster on 2007-05-18
Ok, it appears the prob. was all PBKAC, lol!

After reading [this,]("http://www.amule.org/wiki/index.php/Getting_Started"), particularly the part about getting/connecting to servers...

If U are having probs., u may want  to check out the link!


Thanks for all the replies!
:)

---

### Post by earobinson on 2007-05-18
hehe, looks like I learned something. Thanks

---

### Post by discmaster on 2007-05-18
But now I goofed something up; I accidentally clicked "file" instead of "download" & now the names that I click on appear in red instead of blue, & the file doesn't seem to download...back to the drawing board...:(

---

### Post by mills on 2007-05-18
these are the servers i use 

[http://ocbmaurice.dyns.net/pl/slist.pl?download/server-best.met](http://ocbmaurice.dyns.net/pl/slist.pl?download/server-best.met)   ,for ed2k

[http://nodes.soultcer.net/nodes.php?old=1&count=200](http://nodes.soultcer.net/nodes.php?old=1&count=200)   ,for kademlia

just paste them in and hit the button see if theyre any better

---

### Post by discmaster on 2007-05-18
Hi mills, 

Thanks for the info. I was messing around with the ports/settings & got things goofed up so it wouldn't connect. So at this point I uninstalled & reinstalled, but the re-installation kept the old settings.

Maybe I should reboot before re-installing?

---

### Post by mills on 2007-05-18
what nonstandard settings d you have?
what colour are the arrows on the globe?

also did you specifically assign either TCP or UDP to the relevent ports,  assigning *any* to the port wont work with kademlia as i understand it,

i changed a few ports
standard client tcp = 50020
extended udp port = 50025

---

### Post by Hallvor on 2007-05-19
> **discmaster said:**
> Hi mills, 

Thanks for the info. I was messing around with the ports/settings & got things goofed up so it wouldn't connect. So at this point I uninstalled & reinstalled, but the re-installation kept the old settings.

Maybe I should reboot before re-installing?

There may be a config file in your .aMule folder that survives uninstallation which keeps your old settings. Make sure you delete the directory after uninstall, and then try reinstalling.

---

### Post by Hallvor on 2007-05-19
> **discmaster said:**
> I have been working with Amule for several days, & no go; It always says - Not Connected: Kad off. & "No valid servers found in server list".

Anyone else have this problem?

You just need to add servers. Click a ed2k server.met serverlist file or add a server manually. But be careful with what servers you use. There are a few servers out there controlled by RIAA/MPAA, which give no results when you search and gets your whole list of shared files.

The serverlist at gruk.org is safe, and I recommend one of the large dutch Donkeyservers. Stay away from servers in the US, since 99% of them probably are fake servers controlled by evildoers.

You should be able to connect to Kad once you have found enough sources from servers to bootstrap. Once you have done that, you can turn off server connection if you want to.

---

### Post by dodgePT on 2007-05-19
> **discmaster said:**
> Cable modem & router... Don't quite know what U mean by "port forward". I thought it would be configured to run right from the start like most others...

With a modem/router you usually need to forward the ports in order to use them, because you have two ips when using one of these babies, internal and external ip. External would be your "true" ip, and the internal would be something like 192.168.1.2.

But since this is not your case, i'm glad you solved it :)

---

