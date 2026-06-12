---
title: "Network connection works, internet doesn't"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by loneprairie on 2006-06-27
Hi all,

I've read through alotta threads but none seem to hit on this problem exactly.  I set up 6.06 with no trouble, I can connect to my Win2k server, I can print over the network, but the internet does not work.  The net works on all the Windows machines on the network also.

PC <-> Dell Powerconnect 2016 switch <-> Linksys WRT54GS wireless router (DHCP off) <-> Cisco 837 DSL router (the DHCP server)

Any ideas?

Thanks,
e.

---

### Post by Apple 101 on 2006-06-27
So you've set a static IP address, then?  Anyway, open the Network Manager (called network-admin in a terminal).  Deactivate your wireless connection, and then activate it again.

---

### Post by drtvasudevan on 2006-06-27
disabled ipv6 in browser.?
i had this problem.

tv

---

### Post by wych77 on 2006-06-27
How do you do this?

---

### Post by drtvasudevan on 2006-06-28
type about:config in the url box in firefox
type ipv6 in the filter box (cursor will be there already)
right click on the value you see to toggle to true.
done

tv

---

### Post by loneprairie on 2006-06-28
Thanks for the replies!

Apple101,

This system uses a wired connection all the way through.  I tried setting a static IP but it did not help and it receives an IP from the DHCP server just fine (I even used the one it receives as its static IP when I tried that).  

drtvasudevan,

I tried the IPv6 trick in Firefox to no avail.  I set it back after I tried and it didn't work.

Any other ideas (hopefully)?

Thanks,
e.

---

### Post by Apple 101 on 2006-06-28
[QUOTE=loneprairie]This system uses a wired connection all the way through.  I tried setting a static IP but it did not help and it receives an IP from the DHCP server just fine (I even used the one it receives as its static IP when I tried that).[/QUOTE]Oh, I thought it was wireless because of the wireless router.  Nevermind ;) .  I take it that Firefox gives you the "cannot find server" error?  Open Synaptic and uninstall Firefox, and then install it again.

---

### Post by loneprairie on 2006-06-28
Heh, I used 'Add/Remove' in the Apps drop down menu to remove Firefox and reinstall.  That did not solve the Firefox problem and now the 'Add/Remove' entry has disappeared from the menu.  if there is a quick fix for that, Id be much obliged to the advisor.  Otherwise I may just reload ubuntu to at least be back at baseline.

Any ideas on either of my issues?

Thanks again for all the help - what great forums!

e.

---

### Post by loneprairie on 2006-06-28
Well, reinstalling ubuntu fixed my menu problem but not the internet issue.  I wonder if connecting through the wireless router is causing me trouble.  I can connect directly to the Cisco if y'all think that might be better.

Thanks,
e.

---

### Post by Apple 101 on 2006-06-29
Try connecting directly to see if that fixes the problem.  Then, a user may be able to suggest something, as I'm out of ideas.  My system crashes - unrepairably, so I need to reinstall...

---

### Post by drtvasudevan on 2006-06-29
[QUOTE=loneprairie]Thanks for the replies!
drtvasudevan,

I tried the IPv6 trick in Firefox to no avail.  I set it back after I tried and it didn't work.

Any other ideas (hopefully)?
[/QUOTE]

sorry none

tv

---

### Post by loneprairie on 2006-06-29
Thanks for sticking with me folks - you're the best!

Well, I recabled so that the ubuntu box connects like this:

PC <-> Hub <-> Cisco 837 (DSL Router/DHCP server)

Still nothing.  Is there perhaps some sort of network/internet config file that could be edited?  I doubt this could be, but could Gnome be the culprit?  Are folks having this problem with kubuntu or xubuntu?

Brainstorming,
e.

---

### Post by drtvasudevan on 2006-06-29
perhaps this Q should be taken to networking.

i imagine people have thier own specialities and hang around in that forum.
this being for newbies....

tv

---

### Post by ifican on 2006-06-29
You stated earlier that your machine pulled a dhcp address correct? If so can you ping your gateway, then past it i.e. any other IP on the internet. If that goes through then i see if you can ping via name, thereby showing you can resolve DNS. It may be something as simple as your machine is have trouble with your DNS passthrough by your router, just a hypothesis right now.

---

