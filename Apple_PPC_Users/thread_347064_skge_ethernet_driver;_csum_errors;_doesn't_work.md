---
title: "skge ethernet driver; csum errors; doesn't work"
date: 2007-01-26
forum: Apple PPC Users
---

### Post by Senor Hubris on 2007-01-26
I have a Blue & White G3 that I use as a firewall/dhcp server/caching-nameserver.  

I recently installed Ubuntu (it was running Debian).  I also installed a new D-Link DGE-530T gigabit ethernet controller.  This controller uses the skge module.  When I use this module I get all sorts of errors that look like "hw csum error".  I also get a lot of stack traces dumped to messages and kern.log.  I can turn off checksuming using ethtool (ethtool -K eth0 rx off).   The 'hw csum error' messages go away but the problems continue.

The problem(s): I can ping other machines, other machines can ping me.  Other machines can use the DHCP server.  However, I can't ssh to or from this machine.  No other machines can contact the nameserver (I can use netstat to see that the SEND-Q for named is filling up).  

When I changed back to the older 100Mbps ethernet card everything  was fine.  

Is this a known problem?  Is there some way I can resolve this?  I was running Edgy's 2.6.17 kernel, but then upgraded to Feisty's 2.6.20 kernel.  Both exhibited the same problems.  Interestingly Debian exhibited some of the same symptoms (hw csum errors and stack traces), but everything appeared to work fine.  That was with Debian's 2.6.18 kernel.  

Thanks for any advice.

---

