---
title: "firewall?"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by TrevorRS on 2007-07-04
how many people have fireawalls on ubuntu and what 1 do you reccomend?

Cheers!

p.s i still cant get my bloody wireless to work from some update i downloaded!

Trevor

---

### Post by ubuntu.daemon on 2007-07-04
**firestarter** is a great app not just for ubuntu but for other linux distros as well, other than that i had issues with ubuntu and my wireless so im on xubuntu, anyways point is what wireless program you using? the regular networking one??  Wifi-radar is pretty good and easy to use.

---

### Post by TrevorRS on 2007-07-04
cheers!

well i am using the 1 that came with ubuntu when i loaded on ubuntu EVERYTHING works perfectly for 2 months there now my wireles is bust! and its not my laptop as it works fine on windows!

and ideas?

cheers ill install that firewall now!

Trevor

---

### Post by TheRingmaster on 2007-07-04
Ubuntu comes with a firewall built-in. It is called ip-tables. Firestarter is only a GUI configuration app. You don't need it unless you need to do some changes or just like to monitor things. Ubuntu, because of ip-tables, has NO open ports by default.

---

### Post by TrevorRS on 2007-07-04
the more i ask the more i am impressed with linux! :D

CHeers again!

Trevor

---

### Post by steve.horsley on 2007-07-04
> **TheRingmaster said:**
> Ubuntu, because of ip-tables, has NO open ports by default.

This is not strictly true. iptables by default is completely open - as though there is no firewall running. The no open ports is because there are no services started by default that listen for connections from other machines - no need to use a firewall to close off services you didn't really want to offer in the first place. If you choose to install a listening service, then you may want to configure the firewall to only allow certain authorised hosts to talk to it.

---

### Post by TheRingmaster on 2007-07-04
> **steve.horsley said:**
> This is not strictly true. iptables by default is completely open - as though there is no firewall running. The no open ports is because there are no services started by default that listen for connections from other machines - no need to use a firewall to close off services you didn't really want to offer in the first place. If you choose to install a listening service, then you may want to configure the firewall to only allow certain authorised hosts to talk to it.
Ubuntu has a "no-open-ports" policy which is discussed [here]("http://lxer.com/module/newswire/view/65927/index.html"). If you look around the forums for firestarter related treads, you will find people mentioning this fact as well.

---

