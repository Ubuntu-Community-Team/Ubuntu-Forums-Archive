---
title: "MacBook MadWifi Sniffing"
date: 2007-08-19
forum: Apple Intel Users
---

### Post by Cheka on 2007-08-19
Hey All,

Has anyone else had any success with regards to packet sniffing (monitor mode) with the madwifi drivers on a MacBook? 

I've obviously managed to install the drivers ok and got wifi working...

Then i do 

wlanconfig ath1 create wlandev wifi0 wlanmode monitor

then

ifconfig ath1 up

And finally open wireshark, but no packets are ever captured....

Any clues?

Thanks

Cheka

---

### Post by jpincheira on 2007-08-21
That's kinda illegal dude. You won't find any answers about that here.

---

### Post by macbookmaster on 2007-08-21
bad boy!!!!

---

### Post by benanzo on 2007-08-21
The act of sniffing packets in itself is not illegal.  It's illegal to sniff *someone else's* packets.  For his purposes I am going to assume that he wants to test the security of his own wireless network and that no one's privacy is going to be violated in any kind of prosecutable way during his testing.

After all, [Ubuntu's community docs]("https://help.ubuntu.com/community/CrackingWEP") have contained information on how to monitor and crack the encryption on wireless networks since the Dapper days.

Cheka,

Your best source of information on this topic is going to be from the Madwifi folks.  I would look them up on IRC and follow their mailing list.

You can get some basic info about it [here]("http://madwifi.org/wiki/UserDocs/MonitorModeInterface").

---

### Post by reckless2k2 on 2007-08-21
or how about you just use backtrack to get the job done right.

---

