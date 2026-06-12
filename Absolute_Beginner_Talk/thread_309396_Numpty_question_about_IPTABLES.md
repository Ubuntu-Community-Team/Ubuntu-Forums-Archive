---
title: "Numpty question about IPTABLES"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by Hercules on 2006-11-29
I'm starting to mess about with iptables but am already a little confused...

I've seen lots of examples where the default rules are set along the following lines:
> $IPTABLES -P INPUT DROP
$IPTABLES -P FORWARD DROP
$IPTABLES -P OUTPUT DROP

And then in section 6.5.3 of [this article]("http://www.faqs.org/docs/iptables/targets.html") it says the following:
> **6.5.3. DROP target**

The DROP target does just what it says, it drops packets dead and will not carry out any further processing. A packet that matches a rule perfectly and is then Dropped will be blocked. Note that this action might in certain cases have an unwanted effect, since it could leave dead sockets around on either host. A better solution in cases where this is likely would be to use the REJECT target, especially when you want to block port scanners from getting too much information, such on as filtered ports and so on. Also note that if a packet has the DROP action taken on it in a subchain, the packet will not be processed in any of the main chains either in the present or in any other table. The packet is in other words totally dead. As we've seen previously, the target will not send any kind of information in either direction, nor to intermediaries such as routers.

So to me that implies that as soon as the script comes across those DROP atatements, that will be the end of it, and no more rules will be processed...

Yet obviously that's not the case, as all the scripts have lots more to them. So how does it really work? Am I missing something?

---

