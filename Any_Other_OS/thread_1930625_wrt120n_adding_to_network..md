---
title: "wrt120n adding to network."
date: 2012-02-24
forum: Any Other OS
---

### Post by networkhelp101 on 2012-02-24
this is for help using windows but since it networking I figured it didn't matter.

We have a current network from our ISP/cable company. We have a second WRT120n router. I've seen people say both direction about it. and I'm wondering how can we get a second computer to use the WRT120n to access the internet wirelessly through the other network.

We have cable/ISP router hooked directly to the first computer. it has wireless etc. it's an Arris something. the second computer has no way of being wired and I'm trying to get it hooked up so it can just act as a wireless transceiver for the second computer to the first router and out to the internet etc. 

I've seen back and forth on needing firmware, to not being able to, to just setting the settings correctly in the router and second computer manually. Can anyone help. What can the WRT120 be made to do. anything that will get it to allow internet will basically work. How can it be configured to. 

I can turn off NAT and lots of other stuff. I can even get it to say in network magic(the software it comes with) it access the internet. but the computer is not. Or it can be setup to access the computer but not the internet. I haven't gotten both thus far.

it's also now stuck where I can't access the routers setting from the second coputer while connected via it's ethernet cord. I reset the wrt120n router but still nothing. I'm getting pretty confused at this point. Unless I reset it wrong. I held reset till all the buttons flashed. did it earlier and it worked. I'm assuming it is now a problem with the network on the second computers static ip info conflicting. I probably need to set it back to dynamic till I have to do more.

---

### Post by networkhelp101 on 2012-02-24
Any ideas?

Just to clarify.. the Lynksis wrt120n is being added into an existing wireless network. I'm currently trying to manually set the modem to allow the second computer to work. I would think this should be possible regardless of the modems so called abilities. Can't you do it regardless with just modem/network setups?

I'm currently setting the Lynksis with the computer just hooked up to the computer through the #1 ethernet/Lan port with nothing using the WAN port. the computer is using a 100mpbs Lan card to do it. Am I missing anything like for the wireless part? or should the modem/router do all of that and just use the Lan connection. do I need some sort of wireless adapter? I was reading I didn't.

---

### Post by networkhelp101 on 2012-02-24
The first router is the ARRIS TG852. This is hooked manually to a first computer. The second computer is in another room and cannot be manualy hooked to the ARRIS. I have a WRT120n I'm trying to use to hook the second computer to the first router for internet access. How can this be done?

Nobody knows. I need a walkthrough to get unconfused. am I setting it up as a repeater or a bridge? Does it matter. 

I turned off firewall as far as I can tell. Unfortunately the things I read are all vague. I turned off firewall but it still has a second section of vpn passthroughs or something. Do I need to turn those off also? don't know what they mean by firewall. 

Should I have the router in the same network addresses as the first. AKA the first one is 0.x. Should the second router be 0.x or 1.x? Everything I've read is so vague and full of undefinable jargen(I've tried to search) I can't find enough info to practically apply this or even figure out which thing I'm trying to do?

the arris is using dynamic IP and has network finding on. Not sure what else I need from it. I turned off as much of the firewall dchp and other things I can find. What could I be missing.

It come with software called network magic or something. so far I've gotten one of two things to happen. It maps from the second computer to the router but no internet. or the router to the internet but with no working acess to the second computer. from the second computer though, which is odd. any ideas? What other info is needed?

---

### Post by Elfy on 2012-02-24
You'll be better off with a windows forum.

---

### Post by CharlesA on 2012-02-24
You'd need to set it up as a wireless bridge, and I am not sure if a consumer-level router will let you do that.

---

### Post by networkhelp101 on 2012-02-24
Can it be setup as a second network. I also heard of a firmware solution somehow.

I was reading this little tidbit. But wasn't sure if it would work.

[http://answers.yahoo.com/question/index?qid=20100115221651AAaIHku](http://answers.yahoo.com/question/index?qid=20100115221651AAaIHku)

Are there any work arounds?

---

### Post by CharlesA on 2012-02-24
Just hook it to a network cable and have it functioning as an access point.

---

### Post by networkhelp101 on 2012-02-24
I can't figure out how to do that either. 8) I'm a little too new.

would that alow it to use the internet wirelessly? I can't get the modems to work together. I've been trying but I can't get them to see each other or connect to each other.

I don't have any wireless capability on the second computer either. Just a normal ethernet connection.

Edit: OOH, the first modem already has wireless abilities if that is all the WAP does.

"Router one would be set up with DHCP enabled. You'll get your normal network. 
I would put a switch in the middle but you dont have too. Connect the  second router to the first. Turn off the DHCP, firewall and NAT  settings. Most N routers have an option called "access point" which is  exactly what you want.  if not, no worries. setup: as follows
R1: 192.168.1.2   sub: 255.255.255.0   <---your auto config will give you this or close to by default
R2: 192.168.2.2   sub: 255.255.255.0   < ---- you would staticly assign this info to router 2  
make sure the gateway matches for both routers. (using the default on r1)"

^Would that possibly work? I thought he was describing a way to use this like a bridge or repeater. Though I'm confused on that.

---

### Post by CharlesA on 2012-02-24
It would be on the same network, but allow wireless connection to the network using the new router's SSID.

---

