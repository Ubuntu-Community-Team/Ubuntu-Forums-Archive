---
title: "Getting Gmail through MoBlock"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Drillbit on 2007-10-24
Can anyone do a point by point account of how to get gmail working with Moblock? I've read the main MoBlock page but can't understand the whole "whitelisting" thing.  I can get my gmail through both Evolution and Thunderbird when MoBlock is off.

Any help would be great. Thank you.

---

### Post by Drillbit on 2007-10-25
Anyone?

---

### Post by Drillbit on 2007-10-25
Not even one person? :(

---

### Post by Drillbit on 2007-10-28
One last shot. It's the only thing left to fix.

---

### Post by MrEgg on 2007-11-16
Hi,

What you have to do is enable ports 995 (pop) and 587 (smtp) to go through moblock.

Open terminal and edit  moblock.conf
```
sudo gedit /etc/moblock/moblock.conf
```

Under the Whitelist ports section, edit the following line :
```
WHITE_TCP_OUT="http https"
```

to

```
WHITE_TCP_OUT="http https 587 995"
```

If there is a hash sign (#) in front of the line, remove it.
Restart moblock

```
sudo moblock-control restart
```

That's it.

Cheers,
Egg

---

