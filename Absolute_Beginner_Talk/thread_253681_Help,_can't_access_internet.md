---
title: "Help, can't access internet"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by jcaulley on 2006-09-08
I am a brand new user to Ubuntu.  Downloaded it this morning.  I have installed it on my computer and everything was going good till I tried to get to a webpage in Firefox.

I have an connection.  I opened a terminal window and I was able to ping my router, my DSL modem, the DNS server and a couple different web pages.  I can ping anything.  But when I open up Firefox it will not find any web pages, everything times out.  I tried using the synaptic package manager as well to see if it would download anything, but it timed out also.  Someone please help, i'm getting frustrated.

---

### Post by JNowka on 2006-09-08
Sounds like you need to setup the computer to use proxy servers.
Don't know how to do it personally, but I hope this helps.

---

### Post by jcaulley on 2006-09-08
So long as proxy servers are the same between Windows and Linux, I don't use a proxy server.  The computer connects to my router and then to the internet.

---

### Post by jcaulley on 2006-09-08
anyone got any suggestions to help me out here?

---

### Post by Paul41 on 2006-09-08
Try to disable ipv6 in firefox.  Type about:config in the address bar.  Then filter for ipv6 and disable it.

---

### Post by goatflyer on 2006-09-08
It might be your connection is pppoe?  Many ADSL/ethernet modems work with that.  If so, you need to do pppoeconf before you can use any internet.  You need your ISP username and password.

The command:
cat /etc/resolv.conf

will show you the IP address of the host which does your DNS lookups.  After pppoeconf has done its magic, you may find the contents change.

---

### Post by Stephen_A on 2006-09-08
I had exactly the same problems. They were resolved nicely through the information at: 
[http://ubuntuforums.org/showthread.php?t=183062&highlight=pppoe](http://ubuntuforums.org/showthread.php?t=183062&highlight=pppoe)
I hope it works for you.

---

### Post by jcaulley on 2006-09-09
Ok, still haven't gotten anywhere.  IPv6 didn't do it.  I have Qwest DSL, it's a PPPoA service, not PPPoE.  The username and password is handled by my modem/router unit.  All a computer has to do is DHCP from the router and it should work.  And on top of that I can ping from the terminal and get responses from IPs beyond the Modem, so correct me if I'm wrong but if I had a problem with the PPPoA I wouldn't be able to get that far.  I don't think it is a problem Firefox, I have tried other apps that connect to the internet and none of them work either.  I tried to check for updates and it timed out.

---

### Post by YeahBuntu on 2006-09-09
What model ADSL are you using?

Read some posts about Linux *IN CONJUNCTION WITH SOME OF THEIR ADSL ROUTERS*-not playing with the Qwest DNS servers.

This would certainly allow you to ping by IP and not bring up a web page.

Some said solution.. do not use Qwest'd DNS servers.. here are a few:

# ns1.phx.us.opennic.glue (Phoenix, AZ, US) - 63.226.12.96
# ns1.sfo.us.opennic.glue (San Francisco, CA, US) - 64.151.103.120
# ns1.co.us.opennic.glue (Longmont, CO, US) - 216.87.84.209
# ns1.ca.us.opennic.glue (Los Angeles, CA, US) - 67.102.133.222 

Listed from [here.]("http://www.opennic.unrated.net/public_servers.html")

---

### Post by jcaulley on 2006-09-09
I tried changing the DNS servers.  Still no go.  I did a ping from the terminal again, only this time I pinged the web address ([www.ubuntu.com](www.ubuntu.com)) and the ping resolved the web address to the IP address and I got good responses.  I tried several other web addresses and all of the came back with good responses as well.  I would think that this tells me that I am talking to my DNS servers.  Anyone got more ideas?  I really want to use Linux but this is driving me nuts.

---

### Post by jcaulley on 2006-09-09
Any one else got some ideas?

---

### Post by jcaulley on 2006-09-10
I still can't get to the internet.  I'll try to sum up everything I have found out so far.

Qwest DSL
Actiontec GT701-WS moden
Linksys WRT54GS router
Dell I9300 w/Intel 2200 wireless

I can access the admin page of the router.
I can access the admin page of the modem.
I can ping any IP address and recieve responses.
I can ping a web address and it resolves through the DNS servers to the correct IP address and returns responses.
It is not limited to just Firefox, Synaptic can't download packages, and the update can't either.
The only thing that seems to be able get past the modem is a ping.
I have tried using alternate DNS servers and that didn't work.
I don't use any form of proxy server.
The modem uses PPPoA and the username and password is stored in the modem.  All the other computers that have attached to my network only needed to DHCP from the router and had instant connection.

Can someone please help me?  Loading windows back up so I can come here to get help is getting old.

---

### Post by jcaulley on 2006-09-10
Anyone, Please?

---

### Post by kilou on 2006-11-28
Same issue here: I can ping an IP but not a name. Any news on that?

---

### Post by turbojugend_gr on 2006-11-28
Both try and set up a Static IP address. system>>admin>>networking and there select static ip and provide the needed information, ask any question and post back results, so others can benefit if that works.

---

### Post by powerhouse on 2006-11-28
I initially couldnt browse either and follow the advice above to change the IPv6 setting in Firefox (about:config) as described above.  That seemed to sort out my browsing problem. 

I then had some problems getting the repositories to work, even though I could browse and ping addresses ok.  I changed to Static IP and configured the PC with nameservers of my ISP which sorted out my update problem.

Hope this is of some help.

---

### Post by dileepk on 2006-11-28
I had the same problem - I use Qwest DSL as well and was able to ping but could not get firefox to work.  Per your instruction, i filtered (and toggled) ipv6 and now its working fine.  I thought i had DNS problem as some of the websites i could not ping - example [www.hp.com](www.hp.com).   From firefox try putting ip address say google 66.102.7.99 if that works try once again ipv6 filtering.

hope this helps.

---

### Post by Le Rob on 2006-12-19
For some reason, when Ubuntu autodetects Qwest's settings, it adds 192.168.0.1 to its list of DNS lookups. Most of the problems were solved when I removed this from menu->system->administration->networking|DNS, and added the backup (205.171.2.65). The problem is sometimes that 192.168.0.1 replaces the backed-up one. Why is that, I wonder?

Try that and see if it works. I'm currently in a middle of a battle trying to fix my mother-in-law's Qwest, and things have been absolutely miserable so far. Best of luck to you, and hope things work out.

---

### Post by Le Rob on 2006-12-19
For some reason, when Ubuntu autodetects Qwest's settings, it adds 192.168.0.1 to its list of DNS lookups. Most of the problems were solved when I removed this from menu->system->administration->networking|DNS, and added the backup (205.171.2.65). The problem is sometimes that 192.168.0.1 replaces the backed-up one. Why is that, I wonder?

Try that and see if it works. I'm currently in a middle of a battle trying to fix my mother-in-law's Qwest, and things have been absolutely miserable so far. Best of luck to you, and hope things work out.

---

