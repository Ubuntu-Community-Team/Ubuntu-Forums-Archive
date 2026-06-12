---
title: "Allow traffic from only selected ports"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by Blagomir on 2006-10-14
Hello :)

I`m sharing my internet connection with my friend but i`m pretty shure he use many torrents to download staff. This takes almost 90% of my internet connection speed. My question is: how can i allow my friend to use only ports that i specify - 80+8080(web), 6667(irc), FTP and some other ususal ports?

P.S. Someone will say Firestiter but i`m not shure it works 100% correctly so please gove me another way.

---

### Post by JonahRowley on 2006-10-14
How is your internet connection being shared?  Through your Ubuntu machine, or a home broadband router perhaps?

---

### Post by Blagomir on 2006-10-14
From my Ubuntu machine.
Internet > Ubuntu > Friend

---

### Post by JonahRowley on 2006-10-14
I know how to do it manually with iptables, if you're interested in such advice.  Though I haven't used it in quite a while, I could point you in the right direction, but be aware it'll involve reading from a large, scary manual page.  If you want a GUI program...  wait for someone else to help perhaps.

---

### Post by Blagomir on 2006-10-14
Tell me your way. I`m not afraid to read & learn new staff.

---

### Post by JonahRowley on 2006-10-14
OK, first thing is to look at the **iptables** man page.  First, take a look at your existing rules with **iptables -L**.  You should see some MASQ or DNAT rules in there.

You need to add some filtering rules now.  There are two ways; a blacklist and a whitelist.  With a blacklist, you're specifying which ports you want to block, and to allow everything else.  A whitelist is just the opposite; you specify the ports you want to allow, and it blocks everything else.  I recommend a blacklist for this.

To add the filtering rule, the command will look something like this.  Remember to look in the man page for these options, I haven't use iptables in a while (I've switched to pf on OpenBSD).

**iptables -A input -i eth0 -p tcp -m tcp --dport <bittorrent port> -m state --state NEW -j DROP**
Replace eth0 with the interface facing your friend.  This should drop all connection attempts made to that port.  You can also do port ranges like **10000-11000**, in case bittorrent uses a range of ports.

That should get you started at least.  Oh, and there's an even simpler solution, tell him to knock it off!  Technology doesn't solve every problem, after all :P

---

