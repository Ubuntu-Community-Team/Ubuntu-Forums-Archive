---
title: "wireless help?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by doctrdev on 2007-03-19
Hi all,

I just installed ubuntu edgy on my pc... I'm very happy with how it runs.. although I don't understand how to do the 'coding' yet...

It's taken me a while to get my linksys WMG54G wireless card working... I found a utility that allowed me to get it running...

I'm assuming that since 'wireless assistant' is now finding all the available wireless networks in my apartment complex that now the card is working properly??

The only problem is that it won't hook up to my router... automatic DHCP is set... and I entered my WEP key... but it won't connect!  Any idea why it won't hook up?  When I launch wireless assistant it says I don't have adequate privileges and do I want to launch using 'sudo'... I have no idea what this means....

Is the issue with my pci wireless card install or just my inability to configure it?  I'm assuming that the wireless card is now running.. or perhaps I am missing something?

I'm usually pretty tech-savvy but this is a challenge!

---

### Post by doctrdev on 2007-03-19
I also get this error message when I try to configure wireless assistant manually:

File '/etc/resolv.conf' could not be opened for writing.
Nameserver(s) and/or domain are not set.

---

### Post by karactor on 2007-03-19
Hi

Sorry for hacking your thread, but could you let me know about the utility you used to get your linksys WMG54G wireless card working? I use a linksys wireless adapter and haven't been able to set it up yet. I suspect I'd probably face the same problem as you are now, once I get mine running. But before that, I need to make that first step to set up my wireless access, so any help would be greatly appreciated.

Thanks in advance!

---

### Post by stalkingwolf on 2007-03-19
are you selecting your connection?  Where I work at any given place on property I can
get between 2 and 6 connections, but usually only the closest will connect, IE the building 
I am in.

---

### Post by doctrdev on 2007-03-19
You need to download the linksys windows driver, then install ndiswrapper, it's pretty easy, follow instruction #5 below

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by doctrdev on 2007-03-19
Is there anything additional I need to do in order to point my linksys card to the router?  Wireless assistant is finding all the available networks.. it just won't hook up to ours...

---

