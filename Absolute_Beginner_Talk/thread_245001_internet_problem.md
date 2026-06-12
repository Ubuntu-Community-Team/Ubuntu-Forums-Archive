---
title: "internet problem"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by moon_dog on 2006-08-27
i've been having a weird internet problem lately.  after a random amount of time on the net, my computer just stops accessing the net.  the modem and router are on, and the internet icon on the desktop still shows that i'm connected, but my browsers won't access any websites, and other net dependent apps like GAIM and AZUREUS lose their connection.  i have to shutdown, not restart, my computer and leave it off for 15-20 minutes before i can restart it and access the net again.  i solved the problem once by pinging the broadcast address but after 10 minutes i lost the connection again.  yet the internet icon says that i'm still connected to the net.  and all the other computers here don't have a problem, it's just mine.

---

### Post by nickpaton on 2006-08-27
If you are using Firefox browser try following:

In your Address box type:

about:config

Scroll down to network.dns.ipv6disable and double click to set it to "true".

---

### Post by moon_dog on 2006-08-27
ok, just did it.  what does this do?  how about the other internet apps, does this setting somehow affect them?  it's not just the browsers that loser their connection, but everything that needs an internet connection.

---

### Post by nickpaton on 2006-08-27
> **moon_dog said:**
> ok, just did it.  what does this do?  how about the other internet apps, does this setting somehow affect them?  it's not just the browsers that loser their connection, but everything that needs an internet connection.

It does a number of things like allowing Firefox to access all websites, regardless of their FTP address; also it can speed up accessing sites.

So you cannot access your email browser?

When this happens have you tried seeing if you can access your router via your browser using the router's IP address?

Since you have to wait for a while, it almost sounds like a hardware fault.  What is the make/model of the router?

---

### Post by deadspeak on 2006-08-27
i'm having a similar problem, one minute i'm okay the next i can't connect, all hardware is fine, if i boot into windows thats fine, tried the above and it's set to true, sometimes when i boot i have to deactivate then reactivate my adapter, and sometimes that solves the problem.
this is driving me crazy, just when  i tink i've got all the problems ironed out somthing else crops up. 
Any ideas
Thanks

---

### Post by moon_dog on 2006-08-27
when this happens, i can still access the router via the browser.  i've got a linksys wrt54gs.  i thought it was a hardware problem too, but it doesn't make any sense that i can still access the router when it acts up, and the internet icon remains on.  so then i thought that it was a problem with the router and modem but other computers can still access the net.  right now i think it's some sort of software bug/malfunction, when i try pinging the broadcast address the computer says that 100% loss of packets, so i think that means that i'm connected to the ISP but can't get any return on my requests.  does this make sense?

---

### Post by nickpaton on 2006-08-27
Not sure at the moment Moondog - have you got the latest version of Firefox?

I completely understand your problems, but cannot think what else to suggest at the moment.

Anyone else??

---

### Post by MaximB on 2006-08-27
I'm just guessing here , cuz I had a similar problem with my adsl.
config the networking (DNS , IP etc...)
and with **no delay** - make the .conf file "read only"
try it and see if it helps.

---

### Post by moon_dog on 2006-08-27
actually i'm using swiftfox, the firefox build that came with ubuntu was really slow.  i'm about to do a clean install of Dapper since i'm still using breezy badger, we'll see if the problem will stop with that.

maxddark, can you run me through the process of doing that?  i'm still a bit of a newbie with linux.

---

### Post by MaximB on 2006-08-27
ok
in the terminal type :
sudo pppoeconf
and configure your networking/router/DNS/IP/etc...
after that with NO delay type this command in the terminal :
sudo chattr +i /etc/resolv.conf

hope it helps

---

### Post by lynxus on 2006-08-27
might be worth trying a traceroute to see where your getting kicked.

If its the router then check the security settings etc as it may be  blocking your ip for some form of violation.

if it doesnt even get out of your pc, then check your default gateway / route . Maybe worth disabling DHCP if its enabled and giving yourself a static IP.

---

### Post by moon_dog on 2006-08-27
i've switched to the default init, since i was using initNG, and the problem seems to have disappeared.  not sure yet, i'll leave my pc on for a few days as a test.  i also ran nickpaton's fix, so either one could be responsible for the fix.  i've checked the router and there are no restrictions on IPs.  i'll run a traceroute the next time it happens (hopefully there won't be one.).

---

