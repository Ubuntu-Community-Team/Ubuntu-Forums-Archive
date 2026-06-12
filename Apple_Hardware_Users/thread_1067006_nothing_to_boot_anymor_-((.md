---
title: "nothing to boot anymor :-(("
date: 2009-02-11
forum: Apple Hardware Users
---

### Post by tobiokanobi on 2009-02-11
Hallo,

this is my first post, so thank you for your help.

I've tried to install Kubunto 8.10 on my macbook 2.0Ghz (5.1).

* I've done a backup via timeware (happily)
* I've installed rEFIt

With Discutilitly I created a 12Gb Partition (sda4), MS DOS

First problem that I encountered was, that I the kubunto disc wasn't shwon in rEFIt, solved with -c during startup.

Second was ,that Gparted wasn't installed (or I couldn't find it in (System -> Administration -> Partition Tools, nor elsewhere)

So I tried to install it anyway on the 11Gbyte Partition, worked fine, but then I forgot to push the ADVANCE button. Stupid I am.

Now nothing is bootable, rEFIt doesn't show up. Famous question mark comes.

I can boot into Kubunto if I start booting from CD and then use the option, "boot from first HD".

With Leopard installation CD I can start the Disc utillity tool, everyting looks normal, I repaired "Main Disc (Leopard). No success. I tried also a complete system recovery from Time Machine, no success.

No, what's the best way to on? Installing rEFit on a bootable disc and use the partition tool? (will this be usefull?) Or shall I install OS X completly new, do then the Time Machine backup to recover data? 

Any idea, solution, what's the best way?

Thank you,

Tobi

---

### Post by cyberdork33 on 2009-02-11
create a refit cd and use it to sync your partition tables.

---

### Post by tobiokanobi on 2009-02-12
Do you have any recommandation to burn the rEFIt.cdr image in 
XP? 

I tried ImgBurn, which regocnizes the format but tells me then that it can't open it.

thanks

-tobi

---

### Post by tobiokanobi on 2009-02-12
Tried also k3b on ubunto, says
"seems not to be a usable image"

Renmed it to *.iso

Doesn't work either. 

Any idea?

-tobi

---

### Post by tobiokanobi on 2009-02-12
Okay solved it -

renamed it to *.iso

burned it anyway with k3b

booted from cd

sync mbr

os x starts normal

thanks - 

tobi

---

