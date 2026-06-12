---
title: "port mapping?"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by mills on 2007-03-26
please help

iam trying to use amule but kad is firewalled and i just dont know what else to to
i've opened ports
	4661
	4662
	4665
	4672
	4711
	4712
in both firestarter and in my router but still get [errors]("http://www.amule.org/testport.php") 
i have turned of the firewall in my router and firestarter but kad is still firewalled and the errors
keep coming.

the only thing i can think of that might be causing a problem relates to this;

4672 UDP (outgoing and incoming): Extended eMule protocol, Queue Rating, File Reask Ping, Kad. **Kad will be 'firewalled' if NAT (Network Address Translation) remaps this port number.**

How do i know if this port is getting remapped?
and how can i change it so it doesn't remap?

ps; could there be another reason for the firewall?

pps; iam getting a high id (in case that means anything)

---

### Post by mills on 2007-03-26
ok iam _almost_ certain it has to be something to do with this

 [B]Why does Kademlia still say it is "firewalled?"

If you are using Kad and your router is doing NAT (Network Address Translation), you should prevent your router from remapping the port of outgoing UDP port 4672 packets. This might help if you have a high ID but Kad status is 'firewalled'. [/B]

but how can i make absolute certain?
and how do i prevent the router from remapping?

this is basically a bump with hopefully a little more info

---

### Post by Hallvor on 2007-03-27
High ID means that you are not firewalled. If the arrows on the little green globe on the lower right corner of the screen are green, everything should be fine. If they are yellow, you are firewalled.

You could also change the ports from the standard ones and see if it helps.

---

### Post by FUbuf on 2007-06-22
> **Hallvor said:**
> High ID means that you are not firewalled. If the arrows on the little green globe on the lower right corner of the screen are green, everything should be fine. If they are yellow, you are firewalled.

Ahem. **High ID** means that emule/ed2k/data transfer port **is reachable** using** TCP** from internet.

But **Kad/Kademlia** tells that it's **firewalled**, because **UDP** traffic isn't coming trough. So there is still a problem. System cannot receive replies to Kad queries directly.

IMHO

---

### Post by Hallvor on 2007-06-22
> **FUbuf said:**
> Ahem. **High ID** means that emule/ed2k/data transfer port **is reachable** using** TCP** from internet.

...which means you are not firewalled... ;)

Kad may give indications that it is firewalled even when it is not, if you have too few sources to bootstrap it properly. Changing default ports is always a good idea.

---

### Post by FUbuf on 2007-06-23
> **Hallvor said:**
> ...which means you are not firewalled... ;)
Kad may give indications that it is firewalled even when it is not, if you have too few sources to bootstrap it properly. Changing default ports is always a good idea.

At least with emule, it's very clear that both ports TCP and UDP need to be open so system will work properly. If kad is firewalled then you're partly firewalled and Kad wont work as well as it should. It's just as with the TCP port. It doesnt matter if you're firewalled or not, you still can download. But it will degrade performance (in some cases).

Reason why I expect that firewal works is that after bootstrapping kad so it's online (but still firewalled) it'll die after lets say few minutes. I havent ever seen this problem with emule, only with amule.

I have used only Kad for years with emule, not ed2k servers so I know it should work pretty well. 

There are two options, either UDP port is closed and Kad cant work as it is supposed to. Or aMule is totally broken? I don't have knownledge which is the case.

Firewalled kad might seem to be working because immediate replies to queries will come trough. But as time passes there should be more incoming than out going Kad traffic, so thats the point where being firewalled starts to create a problem. My node seems to be dead to everyone else.

This seems to be a definition problem. How do you define if amule is firewalled or not?

eMule in Windows tells me clearly:

```

Kad Network
Status:	Open
IP:Port:	88.112.XXX.XXX:13122
ID:	1483735239
Buddy:	None

```

Status: Open, aMule says firewalled.

I guess that it's more probable that aMule is broken than that Firestarter would be broken.

So I'll simply use eMule with Wine.

I always though that Un*x programs would be somehow better than Windows programs but that doesnt seem to be so. ;( But to fix that I need to say that Wine works amazingly well. (7-zip, uTorrent, eMule)

---

### Post by Hallvor on 2007-06-23
Funny you should mention that. I used KAD only in eMule too without any problems, but KAD in aMule is very hard to run alone. Have no idea why, but it just seems to work better in eMule. 

Last time I tried eMule with Wine, it was not without glitches. I could only see one line in the log at a time, and had to click back and forth every time I made a new search. Any idea if it works better now?

---

### Post by FUbuf on 2007-06-25
Yep. It seems tat KAD works when I'm connected to server, and then it bootstraps from clients it concated using contacts found via ED2K server / files I'm downloading.

When trying to run KAD standalone, it won't bootstrap. (doesnt load saved nodes?!?) When I bootstrap it using ED2K network, it seems to be running fine. (but always firewalled, I don't know why) Until I disconnect ED2K server, because I shouldn't need it... After let's say something like 15 minutes KAD has already died. No contacts anymore. So aMule might be broken. I wont do more investigation. I'm sure someone in devteam already knows about this problem. It's so bad... ;(

---

### Post by cemptor on 2007-07-07
I have the exact same issue as mills, even though I have ports different than default. Port forwarding is set up correctly in my router, and I have those three ports opened using firestarter.

I tend to buy the theory that NAT is remapping the outgoing UDP port, and neither aMule nor firestarter is broken.

Any help apreciated

---

