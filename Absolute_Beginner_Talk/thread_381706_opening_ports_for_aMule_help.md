---
title: "opening ports for aMule help"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by lastredoubt on 2007-03-11
Hello there,

I am attempting to suckle on the allegedly exquisite pleasure of aMule (I'm trying to get the thingy to work properly) and have encountered a problem.  After the install and general set up and connecting to a server I cannot download or upload anything.  The connection arrows are yellow and red, telling me i have the low i.d. (which is offensive), so I looked for resources on how to get high id.  

I was told in many different places to go into the terminal and write:

sudo iptables -A INPUT -p tcp --dport 4662 -j ACCEPT
sudo iptables -A INPUT -p udp --dport 4665 -j ACCEPT
sudo iptables -A INPUT -p udp --dport 4672 -j ACCEPT

which is fine and dandy, yet this did not solve my problem.  The port numbers are indeed the ones that are in my aMule's preferences, connections tab.  I've looked high and low for information that might help me, and I've probably passed by the solution not understanding it, so could anybody please help me out in beginner's language?  Thanks!  

If it helps solve the problem at all, I'm on a wireless laptop that connects to a BTHomeHub and have firestarter installed.  I've read numerous posts in these forums about opening ports for bittorrent clients, and tried that for KTorrent (since Azureus has some java problems that seem complicated) which didn't significantly help the download speed -- but I guess that is neither here nor there.  

Thanks again for the help, in advance,
Daneil

---

### Post by sad_iq on 2007-03-11
Have you opened these ports on the router ? That's why you don't get High Id with aMule....don't know how to do it with your router so I can't explain...maybe this site is the one: [http://portforward.com/english/routers/port_forwarding/BT/BTHomeHub/eMule.htm](http://portforward.com/english/routers/port_forwarding/BT/BTHomeHub/eMule.htm) 
...it's for emule...but it makes no diference!

---

### Post by lastredoubt on 2007-03-11
thanks for the info, I wasn't sure if the homehub 'counted' as a router or not, but I guess that's pretty dense of me.  

I'll check out the link and see if it has Bt's hunk of junk in it.  

Thanks again, and any further advice from anybody else would be appreciated!

---

### Post by lastredoubt on 2007-03-11
I followed the steps involved in the link you gave, which appeared to help -- however, now I'm stuck with a different problem.  Instead of low id due to 'firewall' it now says I have low id due to 'no kad', so the arrows haven't changed their lovely color to a more pleasing green yet.  Any tips or advice?  

Thanks

---

### Post by sad_iq on 2007-03-11
"no kad"??? where does it say it? if I'm not mistaken kadmelia should not interfere with the ED2K network...so you should have High Id in ed2k network :confused: anyway try to update the kad nodes (click the kad tab in the upper left corner and click the little blue arrow beneath it)...and if that doesn't work try disabling  kad and see how that works(preferences->connection and uncheck kadmelia). Also when I start amule I have to wait a few minutes before i get high id in ed2k and connected in kad...before that both arrows are yellow!

---

### Post by lastredoubt on 2007-03-11
sad_iq,

I had to disable uPnP for my router to get things working sluggishly, It still shows little yellow arrows saying in brackets now (Kad: Firewalled), but I'm downloading at a whopping 2.6 kb/sec from ed2k.  Not sure if that's the norm for aMule; I hear it's slow.  Still warning: LowID in my log.  I'll give it some time and see if it warms up to me though ...  Oddly, though, when I test the port with [http://www.amule.org/testport.php](http://www.amule.org/testport.php) it gives me this:

Error: TCP port 4662 is unavailable. Make sure your firewall or router is allowing/forwarding this TCP service port and your ED2K client is running (i.e. aMule, eMule).

Detailed Error Message
TCP Error 110 Connection refused
Explanation
The connection timed out, meaning the port is being blocked or incorrectly forwarded by a firewall or your computer is turned off :) 


Thanks again for the help, if you have any further advice let me know.

---

### Post by sad_iq on 2007-03-11
Maybe you failed in opening your ports on the router...double check it again...and I think (I'm not sure though) that you also have to reboot your router for the changes to take effect(should be in **System**). Also make sure that you set the port forwarding on the router to point to your computer.  Also I assume that your ISP doesn't block these ports....if it does you should change them to something else(on aMule and router also).

---

### Post by YigalB on 2007-03-14
I have a similiar problem. I am running aMule for a long time on Ubuntu, so far so good.
I opened the relevant ports in the touter, and I had green arrows all the time. The donkey was happy.
Lately I started to get lowID, and the KAD was showing firewalled and disconnected after a while.
I verified the router ports configuration, restarted it, and restarted aMule, and still, KAD is showing firewalled, and the arrows are yellow. The donkey also looks pale, so I guess he needs some oxygen.
I would apprciate any help, if not for me, then for the donkey.

---

### Post by qbproger on 2007-03-19
I have the same problem.
I have a high ID.  I think i've openned all the ports on my router.  I've double checked a few times.  The amule testport page says everything is fine.  I connect to kad and it starts out firewalled, and then after a while it eventually turns off.

---

### Post by YigalB on 2007-03-20
I think the problem is partially solved. I am not sure I understand why, but I can describe what I did:
-  I have Edimax router, which apears to have several options for port forwarding. Don't ask me why, but this is what the manual says.
So far I used the "port forwarding", obviously.
Then I tried something else: I deleted all port forwarding options, and used the "virtual server" menu. Not a big success yet, but then I added the IP of the aMule to the DMZ menu.
Thena miracle occured, and I got "KAD ok" instead of the "KAD firewalled" which was disconnecting all the time. 
This solution is working for 2 days now.
But it's not all good: I get green arrow down, but yellow up, the mule is still pale, and the prorts testing are good only for the 4662. The 4665 and 4672 are still bad.

The only advice I have for aMule is:
- get as input the router type, and guide the user what to open there. There not that many routers out there.
At first I was thinking the aMule should program the router directly, but I guess this is a security hazzard.
Hope I helped

---

### Post by qbproger on 2007-03-20
I have a netgear router.  I'd rather not put my computer in the dmz.  I guess I can try it to see if it works.  I'm fowarding all the appropriate ports though, so i don't understand why it would work and this not work not.

I'll post my progress.

---

### Post by qbproger on 2007-03-20
DMZ didn't work for me either.  I'm not DMZ right now and I'm Kad: ok.

I went to this website: [http://nodes.soultcer.net/](http://nodes.soultcer.net/)
Right click the big list, and use that as your node list for the Kad network.

[http://nodes.soultcer.net/nodes.php?old=1&count=200](http://nodes.soultcer.net/nodes.php?old=1&count=200)

I used that url for my nodelist.  Fixed it for me.

---

