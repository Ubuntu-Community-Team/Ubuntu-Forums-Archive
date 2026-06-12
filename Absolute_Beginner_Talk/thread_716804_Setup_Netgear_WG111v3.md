---
title: "Setup Netgear WG111v3"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by mikeypc2006 on 2008-03-06
How do I go about installing my Netgear WG111v3 USB wireless dongle on Xubuntu?  I had it plugged into my USB port when I installed Xubuntu and at no point did it give any recognition of it being there.

---

### Post by neurostu on 2008-03-06
These instructions are for puppy linux, but i imagine they will work for xubuntu:
[http://www.murga-linux.com/puppy/viewtopic.php?t=26222](http://www.murga-linux.com/puppy/viewtopic.php?t=26222)

but try googling "Netgeat WG111v3 USB Ubuntu" or something like that.

---

### Post by mikeypc2006 on 2008-03-06
Tried following the link but at the point where it says to put the two files into the /root directory, I can't do it as the file manager won't let me create directories or copy files into the /root folder.  How do I get around this?

---

### Post by liquidfunk on 2008-03-06
I have that exact card.

 I suggest you get NDISwrapper, install the following drivers [http://www.avengergear.com/upload/WG111v3.tar.bz2](http://www.avengergear.com/upload/WG111v3.tar.bz2) then it should hopefully work. I think you have to type in the name of your network though. 

 I'm using the Wicd Wireless manager though, it may be different.

---

### Post by mikeypc2006 on 2008-03-06
> **liquidfunk said:**
> I have that exact card.

 I suggest you get NDISwrapper, install the following drivers [http://www.avengergear.com/upload/WG111v3.tar.bz2](http://www.avengergear.com/upload/WG111v3.tar.bz2) then it should hopefully work. I think you have to type in the name of your network though. 

 I'm using the Wicd Wireless manager though, it may be different.

Thanks, that worked :)

---

### Post by liquidfunk on 2008-03-07
Out of interest are you using the Wicd Manager or the default Network Manager?

---

### Post by mikeypc2006 on 2008-03-07
> **liquidfunk said:**
> Out of interest are you using the Wicd Manager or the default Network Manager?

I am using the default Network Manager, which is good in that it allows me to create different profiles for different locations but it would be nice if it gave me single strength too.

What does Wicd Manager do differently?

---

### Post by liquidfunk on 2008-03-08
Wicd is good at roaming so you don't have to know the name of the network. Although sadly it doesn't work with this card :(

 It's also better at WEP.. apparently.

---

