---
title: "Network problem, probably me being a total newbie"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by torgeir89 on 2007-11-04
Been searching through forums/google'ing for hours now..

I'm new to linux, but got it installed properly and so on. Now, the problem: I can't get connected to the internet. 

I've got a wired connection, and I get green lights on my ethernet card when I connect the wire. 
My ISP uses DHCP, so I've put my connection to that under "network settings", and added the two DNS servers I got from my ISP under "DNS".

Still, no internet connection (tried to ping, firefox, etc etc). 
When I use the same wire on the computer I am posting from, which has Windows XP installed, it works without any problems.

Any help would be highly appreciated (please don't make me go back to Windows :( ) , just let me know if you need any output from any commands or something like that

---

### Post by mdpalow on 2007-11-04
hi,

Right off the bat I'm thinking you're overdoing it in Ubuntu. A wired connection in Ubuntu doesn't require you to enter anything; it just works.

Two things:

Are you sure you have the LAN turned on in your bios for the computer with no connection. If it's turned off, you won't get anything.

Did you install 7.10 with the CAT5 cable already plugged in? You should always.

Take out all the DHCP stuff as I don't think you need to be putting that in...

I've installed 7.10 many times and never done anything but plug the CAT5 in BEFORE install and it comes up after install with a working connection...

...

---

### Post by torgeir89 on 2007-11-04
If only it "just worked" : /

Yeah, LAN is enabled in BIOS (it's never been a problem to get on the net with it, pre-Ubuntu).

I really do think I had the CAT5 plugged in while installing, but I'm not really sure.. Know what, I'll just reinstall. Thanks for the advice, hope it works : )

If anyone has any other suggestions, as I fear it was plugged in even during installation, feel free to tell me : )

---

### Post by mdpalow on 2007-11-04
not a bad idea to reinstall 'cause if you didn't there will be some problems later down the road because Ubuntu does install stuff/drivers/etc... during installation.

Buddy of mine didn't have cable plugged in and had all sorts of problems... re-did it with cable in and everything worked fine second time around...

I'll keep an eye out for your response after re-install; shouldn't take but 15 minutes top...

---

### Post by HermanAB on 2007-11-04
The network debug process is much the same as in Windows, just watch the spelling of some utilities.

Usually things are configured automatically by dhclient.  So try restarting it:
$ sudo dhclient eth0

See if things now work.  Here is how to set things manually. 

Let's say you should have the following parameters:
IP: 192.168.1.10
Netmask 255.255.255.0
Router address: 192.168.1.1
DNS: 142.59.19.115
DNS: 142.59.19.120

First see whether the ethernet port is happy:
$ sudo ifconfig eth0
(Windows ipconfig)
If the IP address is bad, set it manually:
$ sudo ifconfig eth0 192.168.1.10 netmask 255.255.255.0

Then see whether you can ping your router:
$ sudo ping 192.168.1.1

If that works, check the default route:
$ sudo route

There should be something like this:
default         192.168.1.1   0.0.0.0         UG    10     0        0 eth0

If not, add a default route:
$ sudo route add default gw 192.168.1.1

Now check the DNS:
$ sudo nslookup [www.yahoo.com](www.yahoo.com)

If it won't resolve, check file /etc/resolv.conf and add the DNS addresses.

Cheers,

Herman

---

### Post by torgeir89 on 2007-11-04
Reinstalled now, with the cable plugged in, still no internet connection.

I'll try all the stuff you wrote Herman, thanks for the help. Willl post when I tried.

---

### Post by amingv on 2007-11-04
Hello,

There's some ISP's that will set your broadband with a preconfigured router, others will give you a username (that looks like an email address) and a password and others (as I was able to see some time when I was in Dominican Republic, using Codetel/Verizon) will require you to use some IP/DNS settings. If you say your ISP gave you some DNS server IPs, I guess your case is the last. You can do this:

Open your windows PC, go to Start>Control Panel, select network connections and the NIC you use as default; right-click>properties>TCP-IP (or IP settings, or something like that)>right click>properties. Here you'll get some values (IP address, subnet mask, default internet gateway, primary & secondary DNS servers) make a note of those and go to you Linux system.

I don't use Gnome very often, so bear with me: go to the System Menu and look for "Network" or "network settings" (not "network tools") there you will see all your NICs, double click on the one you have the cable connected to. Here, if you have "enable roaming mode" activated, disable it and under configuration select "static IP address" here you will put three of the values you've got: IP address, subnet mask and default gateway, click on OK. Then go to DNS and click on ADD, add the two DNS servers here.

That should get you going, if my guess that your network settings go like this it's true. In any case you don't loose anything with trying, just make sure to get the values right.

Regards.:KS

PS: If you have such values in windows, do not modify them, least you loose your windows connection too; just make a note of them.

---

### Post by torgeir89 on 2007-11-04
Tried your suggestions, Herman, no connection : /

Now, amingv, I think you're onto something! I will try what you suggested, and report back.

The DNS IP's weren't exactly given to me, though, I found them on the ISP's website, but it's still something, I'll try.

One more think that came to mind, we've got a dynamic IP, could this be of importance?

---

### Post by torgeir89 on 2007-11-04
Aw, I checked the TCP-IP thing under control panel in windows, it's on "recieve IP-adress automatically". Same with DNS.. 

Now I really have no idea what to do.. 

I think our router is preconfigured, as you talked about, maybe the problem is there?

---

### Post by amingv on 2007-11-04
Just a wild guess: open your web browser and type "launchmodem"

---

### Post by torgeir89 on 2007-11-04
You really got my hopes up there.. But nope, nothing. Doesn't open anything.

---

### Post by amingv on 2007-11-04
My, that's weird.
Talk me about your network, how is it set up? Is it a router and a switch/hub? A connection shared through a computer? Do you have any means to check if your NIC is functional (for example, can you access windows shares through samba?)?

---

### Post by torgeir89 on 2007-11-04
My computer goes into a switch, and then into a router. (I guess it's a router, fiber optical-stuff, I know next-to-nothing about those things :/ )

I see no reason that my NIC shouldn't be functional, the computer I'm having problems with had no problems connectiong before I installed Ubuntu on it. Should I try connecting to it with samba anyway, just to be sure?

EDIT: Checked the "router" (always assumed that's what it was), it says "CPL residential gateway".

---

### Post by Mellon on 2007-11-04
you can try a static ip,

---

### Post by amingv on 2007-11-04
Well, I was expecting you would use samba to see if you can access your internal network or nothing at all. On windows, what do you get from typing ipconfig on cmd?

---

### Post by torgeir89 on 2007-11-04
> **Mellon said:**
> you can try a static ip,

Hehe, that's what I tried first, doesn't work. Thanks for the advice anyway : )

About to give up on this thing, now.. Suspecting it's that weird router/modem "gateway"-thing that screws it up, I've never been able to open ports or anything on it either (you have to do that on the ISP's website -.-)

---

### Post by torgeir89 on 2007-11-04
> **amingv said:**
> Well, I was expecting you would use samba to see if you can access your internal network or nothing at all. On windows, what do you get from typing ipconfig on cmd?

On this computer IPCONFIG gives me (no windows on the computer with the problems, but the numbers would probably be the same?)

(translated from Norwegian, so I don't know if I get the exact terms right, but you'll understand anyway)

DNS-suffix: lyse.net
IP-adress: 10-36.18.136
Networkmask: 255.255.255.240
Standard gateway: 10.36.18.129




I'll try samba now.

---

### Post by torgeir89 on 2007-11-04
You know what, I'll have to do that some other time, it's 5 in the morning here..

Thanks for the help so far, guys :)

---

### Post by amingv on 2007-11-04
Agreed, I must get to sleep too if I pretend to go to work tomorow, but I'll keep checking on that and see what I can do.

---

