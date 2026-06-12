---
title: "Wireless"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by subtrakt on 2006-04-05
Hello, I'm new to the forum, and I'd like to say Ubuntu is the most appealing by far out of RedHat, Knoppix, and Mandrake.  I do, however, have a few minor problems. 

First Issue:
Installed ubuntu, ran fine, detected hardware perfectly, then I messed around with the wireless network settings.  I turned off the machine then booted it back up and it gets to the point where it's about to load gnome then it's just a black screen. 

Other things I noticed when ubuntu is loading is "Configuring network interffaces" pauses for awhile. 

As I typed this I disabled my wireless card on my notebook with the hard switch and it booted fine. So, it must be the wireless card causing the problem.

Different Issue: 
The wireless doesn't work unless I disable WEP on my router - then it works. I looked at some of the other forums here and found no solutions.  

Any ideas on what's going on here? For now I'll just leave my wireless adapter off.

---

### Post by The Mekon on 2006-04-05
Both issues are connected.

Your router appears to have a WEP set so you must set the same WEP in Ubuntu Network Connections.

To do this go  "System > Administratin > Networking (this will require your password) > Wireless Connection > Properties and enter your WEP key and ESSID here.  Tick Enable This Connection and you should be OK

To over come the delay in the loading sequence just enter Control C to skip it.

When your network connection is setup correctly this delay is much shorter.

---

### Post by subtrakt on 2006-04-06
I even went into sudo gedit /etc/network/interfaces and edited the key in there.  It shows up in Network Settings but I still can't connect.  It shouldn't be this painful to get the wireless adapter to work.  I'm using a Lan Express wireless adapter on a sony pcg k23 if that helps.

---

### Post by subtrakt on 2006-04-06
Keep in mind, ubuntu will not boot into gnome with the wireless switch on. I did boot and when network configuration showed up in the boot screen I hit ctrl C (as you said) it skipped the network configuration phase but I still just got a black screen when ubuntu finished loading.  

I think it has something to do with my wireless adapter, I could be wrong.

---

