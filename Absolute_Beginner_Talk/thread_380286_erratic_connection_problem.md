---
title: "erratic connection problem"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by mcmillanje on 2007-03-09
while not exactly a new ubuntu user, I'm new to this subject so I'm posting here...

I have dsl internet, I access it through a local network.

my problem:
we pages randomly refuse connection,
i.e.:
google NEVER works, (i had to adblock google-analytics for this page to work)
this page sometimes works
synaptic sometimes works

resetting sometimes helps (does this reset my ip or something? I'm using DHCP)
does ubuntu generate weird ip adresses?

anyway, any help you guys could offer would be excellent, I don't really even know where to start (actually, i do: forum search. but searching the forum didn't yield results...)

thanks in advance...

edit: just tried synaptic, refreshing the repositories returns:
[http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

should it be connecting to localhost? or something else? for LAN shouldn't it go through 192.168.0.1?


edit: this just gets more confusing,
ping works for google... however a traceroute has no reply about halfway through...
why would ping work but not firefox or synaptic?

btw, I have 6.10 EE...

---

### Post by SactoBob on 2007-03-14
I had exactly the same problem (no google, erratic or non on some others) when I was expanding my home wireless network.  It started when I went to WPA encryption, and I suspect it had something to do with a mismatch between the WPA implimentation and defaults between my router and the bridge I was connecting.

Anyhow, I returned to WEP 128 for that and other reasons for the time being.  Are you using WPA?  If so, go back to WEP temporarily and see if that solves your problem.

Bob

---

### Post by mcmillanje on 2007-04-02
Eh... sorry I read this so late, but I didn't really understand your post.

I'm not really any good at networking.

I have an actiontec dsl modem/wireless gateway that is connected to my router, then my computer through cat5's.

How do I check if my router is using wep or wpa?
I'll try just using a crossover cable to go directly to the modem, and if that doesn't work than It's not the router's problem... hmm...

---

