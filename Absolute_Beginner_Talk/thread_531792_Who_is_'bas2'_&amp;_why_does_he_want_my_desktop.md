---
title: "Who is 'bas2' &amp; why does he want my desktop?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by stevelasvegas on 2007-08-22
[SIZE="4"]I clicked 'Refuse' but I'd like to know;
1. what is causing it.
2. what it means to me.
3. how I should respond.
4. how to prevent it in the future.
I would appreciate any help.[/SIZE]
Thank You

[IMG]http://farm2.static.flickr.com/1100/1200031652_e8a98df84b.jpg?v=0[/IMG]

---

### Post by callan79 on 2007-08-22
> **stevelasvegas said:**
> 
1. what is causing it.
2. what it means to me.
3. how I should respond.
4. how to prevent it in the future.



Hi Steve,

That's someone trying to use a remote desktop connection. You can disable this via System >> Preferences >> Remote Desktop.

Generally if you have your Broadband connection via a router of some kind, your computer is hidden from the world and this must be someone on your network.

But if you just use a regular modem (not a router) then it's quite likely that your computer is directly exposed to the Internet, in which case there are people everywhere scanning computers to see if they can break in.

If you don't use remote desktop features, best to turn them off.

And, if your computer is directly exposed to the 'net, might be worth looking at a router / firewall device.

Cheers
Callan

---

### Post by davidsrsb on 2007-08-22
System - preferences - remote desktop
The security default is ask fo permission as happened in your case.

Someone can see your computer

---

### Post by stevelasvegas on 2007-08-22
I have a router connecting my desktop computer by ethernet and 2 other wireless computers on the network, but I control all of them. So no other computer user is asking for connections to to computer that displayed the message.
The message displayed on my wireless laptop. The other wireless laptop and the ethernet connected desktop are running Windows at the time of the message.
And who is 'bas2'?

---

### Post by callan79 on 2007-08-22
> **stevelasvegas said:**
> I have a router connecting my desktop computer by ethernet and 2 other wireless computers on the network, but I control all of them. So no other computer user is asking for connections to to computer that displayed the message.
The message displayed on my wireless laptop. The other wireless laptop and the ethernet connected desktop are running Windows at the time of the message.
And who is 'bas2'?

Well, bas2 would be the hostname of the computer that's trying to connect to you. If you're sure that the other two machines aren't trying to remote desktop into you, then I'd be checking :

  - is someone breaking into your wireless network (check wireless encryption, etc)
  - is there a virus on one of your Windows machines, and has this virus opened a hole in your router's firewall via uPnP or something?
   - confirm that you don't have any port forwarding settings on your router, specifically port 5900 pointing to your Ubuntu box

Good luck :)
CD

---

### Post by stevelasvegas on 2007-08-22
Wireless encryption is on (WPA)
I do have Upnp on.
My results from Shields Up says:
GRC Port Authority Report created on UTC: 2007-08-22 at 16:19:06

Results from scan of ports: 0-1055

    0 Ports Open
    0 Ports Closed
 1056 Ports Stealth
---------------------
 1056 Ports Tested

ALL PORTS tested were found to be: STEALTH.

TruStealth: FAILED - ALL tested ports were STEALTH,
                   - NO unsolicited packets were received,.
                   - A PING REPLY (ICMP Echo) WAS RECEIVED.

Although when I speifically check port 5900, it is open. But, from what I understand,  it needs to be open for me to be able to connect to my Windows desktop machine through MS Remote Desktop. Shields up says it is open; VNC access.
All computers have anti-virus apps running (NOD32).
I unchecked the 'allow ping' in my router configuration.
I also turned off Upnp now. 
All computers have anti-virus apps running (NOD32).
I unchecked the 'allow ping' in my router configuration.
I also turned off Upnp now.

---

### Post by Taino on 2007-08-22
> **stevelasvegas said:**
> 
TruStealth: FAILED -
- A PING REPLY (ICMP Echo) WAS RECEIVED.


What happened seems pretty straight forward, your werent invisible online, someone else saw your system and decided to see if they could access it, so they asked nicely if they could.

(system --> preferences --> remote desktop)
Security default is to ask permission, just turn it off,
and also dont answer pings to truely be invis.

> **stevelasvegas said:**
> 
I unchecked the 'allow ping' in my router configuration.


and seems you covered that, so should be just fine.

Hey at least you "refused" right? :)
So they didnt hack you, just asked if you would let them in.. ha! :KS

---

### Post by callan79 on 2007-08-22
> **stevelasvegas said:**
> Although when I speifically check port 5900, it is open. But, from what I understand,  it needs to be open for me to be able to connect to my Windows desktop machine through MS Remote Desktop. Shields up says it is open; VNC access.


Hi Steve,

Okay, so port 5900 is open on your router. Firstly, this is VNC's port ... so if you're running VNC server on your Windows box then yeah you'll need this open. But if you're using Windows Remote Desktop, then port 3389 is your man.

Can I ask if all your machines have statically-assigned LAN IP Addresses?

If I had to guess what's happened, I'd say that at some time in the past your Windows machine has had an IP Address, let's just say X is the IP. Your other WIndows machine is Y, and your Ubuntu machine is Z. So you've gone and set up Port 5900 to forward to X, which is your Windows box, all good so far!

But then if the IPs aren't statically set, then at some stage more recently your router may have assigned X to your Ubuntu box, Y and Z to your Windows machines. This means anyone scanning port 5900 gets straight to your Ubuntu machine, hence the remote desktop question coming up.

I might be wrong with all that, but just in case you are using "automatic" IPs, this is probably not a good idea if your network has any port forwarding.

Cheers
Callan

---

### Post by Aishiko on 2007-08-22
I tell each copmuter what IP addy to get from the Router if I want the PC to have a static IP.

---

