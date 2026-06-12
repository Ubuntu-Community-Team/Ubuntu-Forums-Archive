---
title: "how do I make ethtool settings persistent?"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by cnkbrown on 2006-05-15
In looking at the ethtool man page, and searhcing posts, I can't tell if changes made using ethtool are persistent, or do I need a script to force them on each boot?

    ethtool -s eth0 speed 100
    ethtool -s eth0 duplex full

I am using these because under ubuntu my NIC defaults to 10BaseT instead of negotiating up to 100BaseT.

Is there a more correct way to accomplish this than ethtool?

thanks.

--cb

---

### Post by dcstar on 2006-05-16
[QUOTE=cnkbrown]In looking at the ethtool man page, and searhcing posts, I can't tell if changes made using ethtool are persistent, or do I need a script to force them on each boot?

    ethtool -s eth0 speed 100
    ethtool -s eth0 duplex full

I am using these because under ubuntu my NIC defaults to 10BaseT instead of negotiating up to 100BaseT.

Is there a more correct way to accomplish this than ethtool?
[/QUOTE]
Might be able to put commands in the module when it loads, but the easiest way may be to add a small script with those commands in your /etc/rcS.d directory that runs late in the piece.

---

### Post by chedlin on 2006-05-21
I found this thread looking for the same information myself.  Having not found a great solution (I am stil looking)  I have taken and recomend the following:

I created a script called ethtool in /etc/network/if-up.d containing:
#!/bin/bash

if [ $IFACE = "eth1" ]; then
 ethtool -A eth1 rx off tx off
fi

It is crude and could use refinement, but you should be able to adapt this script to your needs.  Just create the txt file with the above contents and chmod it 755.

---

