---
title: "how do I configure an nternet connection"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by ljbirns on 2006-11-18
I just loaded Ubuntu 6.06 as the sole OS on an old computer.
The computer's ehthernet card is connected by cable to a D-Link 624 router. I use Verizon FIOS ( My laptop running XP is also connected to this router)
I went to Applications > accessories > terminal typed 
  sudo pppoeconf
it asks for my password(and I am not sure WHAT password it wants) BUT won't let me enter anything.  Black box is there but won't accept key stroke.  
In System> Administration >Networking I enabled  Wired Connection
properties> Auto Config DHCP  If I go to the Firefox window on the computer and type in the router IP address I do not connect to the router.
The  Ethernet card is lit when the cable is plugged in. I tried two  different cables.

I would appreciate some insight.

Thanks

---

### Post by turbojugend_gr on 2006-11-18
It reads what you type, but doesn't show asterisks (****), security (stupid) thing. Just type your login password there.

---

### Post by turbojugend_gr on 2006-11-18
Oh, try "ping ROUTERS_IP_HERE" what do you get?

Note you need to press CTRL+C to stop pinging.(to stop terminal tasks in general, actually)

---

### Post by ljbirns on 2006-11-20
Thank you  Gentlemen
My router  connects directly to the incoming jack ( No Modem) then my computers to the router.
I plugged the Ubuntu computer directly to the jack, by passing the router and in terminal   did   sudo pppoeconf  I led me through a series of steps and I was then connected to the internet.  E-mail works too. However That cuts out my XP Laptop and my wife's  computer from the ISP. Must find a way to configure the router for Ubuntu

---

### Post by turbojugend_gr on 2006-11-20
ljbirns, hi it's only me so gentlem**a**n it is.

Why did you altered your network state before runnning pppoeconf (which from what I know doesn't need the lan card to be directly plugged to the net, on the contrary it looks for  ADSL hardware to configure your connection), I believe you shouldn't do so. Plz do as I say in my second post, oh and please define your knowledge state so I can adjust advice according to it.

It would be helpful if you pinged the router (in a terminal type "ping 10.0.0.12" where 10.0.0.12 pout YOUR router's IP. Also plz post the output of pinging your LAN card, and if it is possible ping [www.google.com](www.google.com) for example too-"ping http://www.google.com")

PLease reset the state of your network to its previous state, and do the above suggestions. Post back here the output and I will hit back asap.

Hope we'll get this sorted out, Cheers TJ.

---

### Post by ljbirns on 2006-11-20
ok turbojugend_gr
my knowledge state = zero in Linux.
I will follow your  posted advice tonight when I get home
and let you know the results.  You also said :
PLease reset the state of your network to its previous state, and do the above suggestions. Post back here the output and I will hit back asap."  How do I do that ?

 Thank you for your help

Lew

---

### Post by turbojugend_gr on 2006-11-20
That is : setting up your home network as it will usually be, I can't see it so I am guessing, you have a router and a couple of pcs wired to it, while the router is of course also wired to the plug. So set your network as it should be not worrying for now if the ubuntu machine will be able to reach the web. That's our (you+me+all the other great guys in here) job to make sure it will.

---

### Post by ljbirns on 2006-11-20
ok  Network back to normal  I am on windows laptop now
results of pings as follows
ping  192.168.0.1   (router)    = network is unreachable
ping ROUTERS_IP_HERE   =  ping unknown host
ping [http://www.google.com](http://www.google.com)  = ping unknown host
Lew

---

### Post by ljbirns on 2006-11-20
The pings, of course, were on the Ubuntu machine.  I have contacted
D-Link ( the router people) and described the problem. Maybe they will have some insight as to the problem.
Lew

---

### Post by turbojugend_gr on 2006-11-20
Can you ping your lan card for me too plz? oh btw ROUTERS_IP_HERE means put the 192.168.0.1 there.

---

### Post by ljbirns on 2006-11-21
How do I ping the lan card ?

---

### Post by turbojugend_gr on 2006-11-21
in a terminal "ping *PUT_YOUR_LAN_CARD_IP_HERE*" it is usual thing that the lan card's ip is something like 10.0.0.10, so "ping 10.0.0.10" in that case, if not do as it suits. Post back asap.

---

### Post by ljbirns on 2006-11-21
Will do  I won't be home to do this until 7:30PM  . I think that is 2:30 AM tommorrow for you.

Thank you  I appreciate your help very much.

Lew

---

### Post by ljbirns on 2006-11-21
> **turbojugend_gr said:**
> in a terminal "ping *PUT_YOUR_LAN_CARD_IP_HERE*" it is usual thing that the lan card's ip is something like 10.0.0.10, so "ping 10.0.0.10" in that case, if not do as it suits. Post back asap.

turbojugend_gr

SUCCESS !!!  I am on the net using Ubuntu .  I pinged the LAN card ( I think )  127.0.0.1  It ping-ed fine.  The D-Link router people told me to check to see if the router filter was set to allow this machine to connect.  It wasn't.  I entered the MAC address into the proper filer section in the router, updated and Voila  I'm in.

I really thank you for taking all the time to help me. I could not have gotten this done without you.

Now I have to start to experiment and get to see how Linux works
and to learn.  I am sure I will call on you in the near future if you do not mind.

Thank you again.


Lew

---

### Post by turbojugend_gr on 2006-11-21
I am very happy for you Lew, feel free to buddy list me or contact me via Instant Messenging for whatever reason.

Btw, so as for you to learn, I was aksing you to ping the network card so i could be sure ubuntu recognized it and it was working fine, then the only thing we could do, would be you calling for the appropriate MAC address since the card is up and running yet the router was not reachable. You did  so anyway, so "GREAT job" to you m8.

As for the time, don't worry I just came home after celebrating a great soccer win : AEK Athens - AC Milan 1-0 ! History was re-written tonight!

Cheers, TJ.

---

### Post by tribeone on 2006-11-21
In my own search I came upon this thread and must saw it is very pleasing to see that there are those out there who will genuinely help their fellow man in time of need. Glad it al worked out for you.
TribeOne

---

### Post by ljbirns on 2006-11-22
TJ
Thank you.  I will take you up on your offer of help.

Go AEK Athens !!!

Lew

---

### Post by impakt on 2006-11-28
im having almost the exact same issue. But everything i have tried hasnt worked. 

i been using it on this same network for a year with no problems at all. Same router the above poster has with it working 100% of the time. I think my cat unplugged the verizon box and it rebooted the system here. All my settings stayed exactly the same, with wireless and everything. ALl my windows machines are working fine on both wired and wireless network. but my ubuntu box will not work at all. please Help:)

---

### Post by impakt on 2006-11-28
just to add to above. I pinged my network with no success. 

not sure what lan ip i needed so i used the same one the above poster used:) 127.0.0.1. and it worked with that just fine. 

not sure where to go from here. 


my ubuntu knowledge=very limited. I been using this box for just internet browsing and music.. worked great until now

---

### Post by impakt on 2006-11-28
just a little more info. I spend most of last night trying to get this going. 

I also checked the filter. and i have IP filters disabled and Mac filters disabled(although you can only check one or the other)

firewall in the router is not even selected or anything(no defining rules, everthing is blank. 

in ubuntu if i searched for the network using dhcp it hangs and finally says "eth0 active" but still in the network status it has a yellow exclamation point and no connectivity.

---

### Post by bobbyboy on 2006-11-28
Hi everyone, I just now registered to mention that I am having similar issues with setting up my internet connection on my new Ubuntu 6.1 box (desktop ed). 

My existing system consists of a DLINK  ADSL modem / router, which is connected to a DLINK 8 port switch. All computers on my network connect through the 8 port switch. My ADSL modem / router is also the DHCP server and issues leases to 3 different XP pro machines. This is all working fine.

The issue is this when I introduce the Linux box into the equation, it recieves a lease just fine from the DHCP server and sets the default gateway to the same IP as in the XP machines, but for some reason dns doesn't work on the linux box. 

Note - that I can surf to ip adresses in the address bar of firefox, but it cannot resolve names.

Also note - that I can set a static IP and specify my ISP DNS IP's and the linux box browses just fine.

Now that I write this down, it almost appears that I don't have a problem - but I ask these questions because I don't understand why the linux box won't work using the DHCP server as all the other boxes do.

Thanks in advance for any help recieved,
Cheers,
Bobby

---

### Post by turbojugend_gr on 2006-11-28
Hi bobbyboy, I can't answer your queries, I can only assume some reasons for this behavior. Check for ipv6 disabling, there are threads on this forums about it, I ain't sure that will solve it, but some users seem to believe so so give it a try.

My suggestion though would be, you using a Static IP. It is faster sometimes, and also required for torrents as well p2p netowroks. Since it solves your issues to, I can't see no reason for you not setting a Static Ip. As for the security risk, that's absent cause Linux has the greatest tools of protecting it self by default.

Best Regards, TJ.

---

### Post by impakt on 2006-11-28
Hey turbojugend, Its great to see people helping like this. Any idea what my issue could be? It drove me crazy last night, Im sitting at work running on 2 hours of sleep:D

---

### Post by turbojugend_gr on 2006-11-28
Let me do my research on it, then if i come up with anything, I let you know, ;).

---

### Post by turbojugend_gr on 2006-11-28
Can you ping, your lan card, you router and a website for me? post back the results plz. You can see how to do those by checking my earlier posts, on this thread.

EDIT: By the way, you should re-inform me with your issue, plz be as short and comprehensive as possible. The better we understand, the better the help you 'll receive.

---

### Post by impakt on 2006-11-28
thank you for your help. just to re-iterate

This computer with the same setup has worked fine for a year. my verizon box got unplugged and rebooted. everything else came on fine, didnt even see a hickup, everything else meaning wireless network with the same ssid and encryption, internet up and going on my windows desktop with no issues. i come to find the the ubuntu machine can not connect.  

here is what i have tried. 
Reboot,reset the modem, unplugged the ethernet cable from the back of the ubuntu box and plugged it into the windows box(windows connected instantly) I double checked the settings of the modem to make sure no unnecessary firewalls/filters are activated. restarted all computers.

that narrows it down to the ubuntu computer. So I went to network settings, activate eth0.it will after a while state that "the interface eth0 is active" but will not connect to the internet. I tried playing with the properties and trying static IP just to see with no luck.. So here I am. Lost without my linux:(

ping 192.168.0.1: network is unreachable
You ask that i ping the lan. Im not sure what that is or where i can find it. But since the other poster had that lan number i tried that. And from what i see it seems to be pinging(is that a word>:P) "i had to control c" to stop it

Ping [http://www.google.com](http://www.google.com) 
ping: unknown host [http://www.google.com](http://www.google.com)

thanks for all your help. This is a great site.

Edit. I also found somewhere to run "sudo pppoeconf". I ran it and instantly got a message.
"sorry, I scanned 1 interface, but the access concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running PPoe process  which controls the modem "

---

### Post by turbojugend_gr on 2006-11-28
Here's what I want you to do, set a static Ip, that means giving your lan card an ip (try 10.0.0.10), give your DNS server there and also give the ip of your router. IF you can't be sure for a value there or anything similar ask first.

---

### Post by impakt on 2006-11-28
Im sorry. Im actually not sure what that means. How do I give my lan card an IP? in the device info on my router it has this info.I apologize im not sure how to do somethings you mentioned. I have also attached some screen shots of the dlink setup 

Lan:
MAC Address  00-15-E9-D4-BD-64  
IP Address  192.168.0.1  
Subnet Mask  255.255.255.0  
DHCP Server  Enabled  

Wan:
MAC Address  00-15-E9-D4-BD-65  
Connection  PPPoE Connected    
IP Address  71.241.157.79  
Subnet Mask  255.255.255.255  
Default Gateway  71.241.157.79  
DNS  68.237.161.12 71.250.0.12

---

### Post by turbojugend_gr on 2006-11-28
Nice, that's helpfull info there, for now let's skip my previous post, we may not need to set up a static ip.

Open a terminal and type "pppoeconf" it's a tool that will help you with your router, follow it's steps, if needed google it up for a walk through though it should not be needed. 

After you are done you may need to restart your pc (so you won't have to manually turn of your lan and bring it up again), then post the results plz.

---

### Post by impakt on 2006-11-28
I tried that. I get 

"sorry, I scanned 1 interface, but the access concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running PPoe process which controls the modem "

---

### Post by turbojugend_gr on 2006-11-28
Can you please clarify to me if you use a cable or wifi to connect to your router?

Also check if there is actually another application using your router. (a firefox,etc could do that, it's unlikely but maybe..)

---

### Post by impakt on 2006-11-28
Its verizon Fios with a Dlink router. The ubuntu computer is on a direct ethernet cable 10 feet away from the router. a windows desktop is connected as well. Also a wireless windows laptop is connect and that is what im typing from now. even my PSP connects to the wireless fine.

---

### Post by turbojugend_gr on 2006-11-28
hmm, go for setting up a static Ip.

open networking from system>>admin menu. choose properties for your lan connection, there change the first field to static IP.
IP address (Lan card's ip actually): 192.168.0.1
Subnet Mask: 255.255.255.0 
I can't be sure for your router's ip (Gateway address), it shouldn't be the Wan ip, try giving my your exact dlink model... I 'll hit back asap.

---

### Post by impakt on 2006-11-28
Thanks for responding so quick!

unfortunately i tried as you suggested. I get "could not enable theinterface eth0. 

This is so wierd. Its been working without a hitch for a year. nothing changes, the white box in my garage that the router hooks up to just rebooted

---

### Post by turbojugend_gr on 2006-11-28
your routers ip should be anything like 192.168.0.2 and up, can't be 100% sure, but that's what I understand did you use that?. If yes lease ping 192.168.0.1, 192.168.0.2 and [http://www.google.com](http://www.google.com). Post back the output (you should let it at least transmit 4-5 packages then CTRL+C it), copy paste the output for each one and post it, I 'll hit back asap.

EDIT: THis has faults, check my following post for the corrections, plz.

---

### Post by turbojugend_gr on 2006-11-28
Pardon me I made a mistake, you routers ip is 192.168.1.1, your local area network card, though I can't be sure, it should be there by deafult anyway.

EDIT: So shortly, replace 192.168.1.2 in gateway address with 192.168.1.1 and then replace 192.168.1.1 in ip adress to what it was there by default. That is of course if your other "cabled" pc is not using 192.168.1.2, if it is select any address starting with 192.168.1.? (1-10 should do it)

---

### Post by turbojugend_gr on 2006-11-28
m8 another thing is, change "[http://www.google.com](http://www.google.com)", to "google.com' plz. You should ping that instead.

---

### Post by impakt on 2006-11-28
thanks again. 

Ping google.com
ping: unknown host google.com
I pinged also everything you mentioned and got connect:network is unreachable

also i have another attachment
 thanks

---

### Post by turbojugend_gr on 2006-11-28
That picture, answered a lot of questions m8, let'stry again, go  setr a static ip, use :

ip address: 192.168.0.156 (156 is just a shot in the dark anything from 100-199 shold do, unless you are unlucky and it matches the one windows pc is using)
subnet mask: 255.255.255.0
gateway address: 192.168.1.1

then in a terminal, type: "ifup eth0", then type "ifdown eth0". This should restart your netwrok interface.

Try pinging your roputer lan, and a website, open up a firefox, and please post results, if that fails, check the freaking cable, it might be damaged (happened to a guy I was helping yesterday). Finally if that fails too, plz try posting the above info in your routers config tables (the pages in the screenshot), maybe that damn router, overrides Linux settings... plz post back how it went, asap.

---

### Post by impakt on 2006-11-28
I tried everything you suggested down to the T. still no luck. 

Sorry bro I think this one is hopeless:) 

It just drives me crazy because i have grown on this computer/os in the year i been using it. It always worked without a hitch:-k

---

### Post by turbojugend_gr on 2006-11-28
If you even tried setting up a static ip, through the config page of dlink, then I guess I am not the one for the job.

I would suggest you creating a new thread, title it cautiously (sth describing your situation, not your feelings, or what happened before, you can put those in your post, not the tittle). Create a describing, comprehensive and rather short post, with all that is going on, maybe what you've tried this far (though i would suggest it, you may loose advice from someone that knows better than I do, so please make sure you say you are keen on advice on what you already tried too). Following this guidelines you will receive good help.

For example this user named it's post ho do I configure an internet connection, you might use sth like: Lost connection to my Dlink router after a restart". This will atract users that are aware of this situation, and you can further explain what exactly happened, and what is you are experiencing at moment in your post.

I hope you 'll get this solved m8, I am sorry I couldn't help much.

---

### Post by impakt on 2006-11-28
You helped alot. Just didnt work in this case. 

I thank you for everything. Hopefully i can get it going sooner than later. For shits and giggles i broke out a brand new netgear router, hooked it up and im having the same exact issue. Hopefully somethings not jacked up in my computer. thanks again

---

### Post by raublekick on 2006-11-30
impakt, i notice you are using the same ISP and DNS servers as me, and i have been having MAJOR issues with them lately. have you noticed your connection being crappy lately in general?

---

