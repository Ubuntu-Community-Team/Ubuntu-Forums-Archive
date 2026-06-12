---
title: "KDE Core?"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by bullpen7979 on 2007-02-07
About 48 hrs into this Kubuntu thing. Out of the gate, KDE seemed a little slow, and I was reading this article on the psychocats site. 

[http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core)

Question is, what will this operation do? Will all my programs still be there when I get back? Will I have to reset preferences? What if I don't like the change, can I go back?  

Granted, older hardware, celeron 500, 256 mb ram, 20gb hdd. any thoughts here?

---

### Post by r4ik on 2007-02-07
Same guide,

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Good luck !

---

### Post by bullpen7979 on 2007-02-07
OK, right. I see the guide, but was wondering if this is a "speed things up" kind operation, or a "totally change what you see and where your programs went" kind of change.

---

### Post by aysiu on 2007-02-07
*kde-core* is a lighterweight KDE than *kubuntu-desktop* (the default set of Ubuntu KDE applications). It runs fewer services and thus is usually better for lower specs (less RAM).

I think your best bet is to just give it a shot. If you don't like it, you can just do ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` and you'll have everything back to the way it was before.

Also, the instructions remove individual programs. If you see programs in that list you would not like removed, take them out of the instructions. The instructions are basically just a list: remove... this program, this program, this program, this program, and this program. If you take out one of the programs to be removed, it will stay.

---

