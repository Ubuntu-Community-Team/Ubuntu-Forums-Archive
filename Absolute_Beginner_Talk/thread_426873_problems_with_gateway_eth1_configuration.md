---
title: "problems with gateway eth1 configuration"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by c0rv0 on 2007-04-28
hey! I'm new in this whole free-software experience, and barely know anything about computers. My problem is this: when I installed ubuntu (dapper) in my lap-top the system authomatically recognized mi wireless card in the eth1 gateway (as could be seen with the "ifconfig" command); but one day and without reason, the eth1 device was no longer active and I cannot connect to the internet via my wireless anymore. Can anyone explain me why this happened? Or how can I re-configure my card?

---

### Post by toddward on 2007-05-01
It sounds like you disabled your hardware somehow.  In order to re-configure your card, it sounds like you may have to apt-get all the packages for wireless again.  Can you attach up to a wired connection?

You *may* be able to issue the command below and see if the card is listed elsewhere...it's almost like ifconfig, only specific to wireless: 

```

iwconfig

```

---

