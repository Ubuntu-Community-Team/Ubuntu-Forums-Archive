---
title: "Server 6.06 grown a new NIC?"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by sweetie on 2007-07-01
I've a little experience with Freebsd & a little with Windows. I installed Ubuntu 6.06 server on a dual HP proliant as I'd  heard good things about it.
I have a number of issues with this install

1. I seem to have gained a second eth interface - I now have eth0 & eth2. Oddly, eth2 has the IP which i put on eth0. 

2. Prior to this mysteriously gained NIC, I installed Shorewall using APTITUDE. Whenever I try to invoke Shorewall, it complains about the lack of 'zone' info and 'policy' info, but after running around the man pages and googling madly, I can find nowhere to put this info, or the syntax to use.

3. Thinking I may have installed an old version of Shorewall, I  decide to update the contents of APTITUDE - but despite having a valid DNS server in resolv, both APTITUDE and apt-get both fail to connect to anything. I can ping externally, by IP, quite happily - I just can't download anything.

4. So, in a bit of a mood, I decide to install 7.04 - except that when I look on the Ubuntu site, 6.06LTS has support several years beyond 7.04, which implies to me that 7.04 is an older version than 6.06 - and, again, I seem to be able to find nothing informative on the net.

Now I'm faced with several existential questions ( am I just senile? Am I pre-senile but the victim of a south Park plot? etc) and some practical ones ( should I reload Freebsd?  Ubuntu 7.04?  re-install 6.06 & hope it behaves better?  Search the Net for clues another few days? )
I am lost with this install - a little bit of wisdom would be more than welcome

Sweetie

---

### Post by wolfen69 on 2007-07-01
7.04 is the latest incarnation of ubuntu.

---

### Post by sweetie on 2007-07-01
Thanks. I sort of thought it should be later than 6.06 but was thrown a bit by the timescale.
Any ideas about all my other ( non-existential ) issues?
cheers
sweetie

---

### Post by sweetie on 2007-07-02
OK
Is Ubuntu prone to developing extra NICs?
Is there any sane way of reversing this?
If I can't reverse this behaviour, is there any stable way of accomodating it?
cheers
Sweetie

---

