---
title: "[SOLVED] Dyndns: help me please :("
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-06-12
Okay, so with dyndns i set up an account and directed it to my dynamic ip.
I came out with this link [http://techaspect.dnsalias.net//](http://techaspect.dnsalias.net//)
but I am sure that whenever someone clicks it it will take them to THEIR ip, not mine...  :(

I really want to use the computer at my house as a wordpress server. So any tips would be appreciated. I already set up wordpress and LAMP, so I just need to get it secured and connected.

Thanks in advance.

---

### Post by lazyart on 2007-06-12
Why would it take someone back to their own IP?  I doubt that is happening.  If you are trying to use the link from your own machine then it won't work.  It just doesn't work that way.

Have you set up a dyndns client on your machine to keep the address updated when your ISP changes it?

---

### Post by tdrusk on 2007-06-12
> **lazyart said:**
> Why would it take someone back to their own IP?  I doubt that is happening.  If you are trying to use the link from your own machine then it won't work.  It just doesn't work that way.

Have you set up a dyndns client on your machine to keep the address updated when your ISP changes it?

No I haven't. This is my first time doing all of this. Can you please explain more?

---

### Post by freebeer on 2007-06-12
I'm not sure that I understand... is the entry for that dynamic IP address pointing to your current IP address?  If so, then it won't take them to any other address.  

Also note that if your computer is behind a router, you'll probably need to set up port-forwarding rules in the router.

---

### Post by tdrusk on 2007-06-12
What I did was set up a dyndns account, and set up dynamic dns server. When it asked for my ip, i put in 192.168.1.100, which is what my ip listed as under the network manager. I highly doubt that is correct. I am pretty sure that's just my routers ip.

---

### Post by lazyart on 2007-06-12
[This page]("https://help.ubuntu.com/community/DynamicDNS") should give you all you need to know.  Your IP address changes periodically (unless you're paying extra for a static IP but I doubt that).  Your web address points to an IP address.  When your IP changes the web address will be pointing to the wrong place.  A dyndns client will check if your IP has changed and update your dyndns provider so that the hits keep coming to your page.

The address you shouldve given you'll find at [www.whatismyip.com](www.whatismyip.com)

---

### Post by phr0ze on 2007-06-12
Dynamic DNS is asking you to manually enter your IP? isn't that the point?... anyways, the IP would be the public IP from your ISP, you can get it by logging into your router and looking for WAN settings. This should list the IP. Note: it does not start with 192.168, 10.100, 255, etc.

---

### Post by tdrusk on 2007-06-12
> **lazyart said:**
> [This page]("https://help.ubuntu.com/community/DynamicDNS") should give you all you need to know.  Your IP address changes periodically (unless you're paying extra for a static IP but I doubt that).  Your web address points to an IP address.  When your IP changes the web address will be pointing to the wrong place.  A dyndns client will check if your IP has changed and update your dyndns provider so that the hits keep coming to your page.

The address you shouldve given you'll find at [www.whatismyip.com](www.whatismyip.com)

I replaced the router's ip with my ip in the dyndns setup. I got this. Can someone tell me if it is working?
techaspect.dvrdns.org

---

### Post by freebeer on 2007-06-12
With regards to the updating, think of it like this:  DynDNS has an entry for you that currently points to your current IP address.  If your ISP should change that address (it is dynamic, not static, after all) the entry in DynDNS no longer is pointing to your machine (because your machine's address has changed).  DynDNS has links on their website for scripts that you can run.  Basically, the script takes a look at your IP address and if it has changed, informs DynDNS what it has changed to.  That way DynDNS always has a valid entry for your current IP address.

The script that I use checks every 10 minutes, I think.  I really haven't been able to confirm for myself that it actually works because my IP address hasn't changed in over 6 months.  :D  If your doesn't change often, make sure that you log into dynDNS at least once every month to re-confirm your current IP address.  I believe DynDNS will drop you after 35 days if it doesn't get a confirmation.  (Makes sense... they'd have litterally thousands of dead links if they didn't clean house in this fashion.)

I hope that helps.

---

### Post by lazyart on 2007-06-12
Now you have to tell your router to forward traffic on port 80 to your server.

---

### Post by wthanna on 2007-06-12
You are halfway there..  Install ddclient using synaptic.  It will run on your computer, periodically checking to see if your ip address has changed. (which it will, if you have a "dynamic" ip address). When your ip address changes, it will automatically update the address with dyndns.

---

### Post by freebeer on 2007-06-12
So far it's not working... but it does take time for a new URL to propagate through the system.

---

### Post by tdrusk on 2007-06-12
how can I do this?

---

### Post by tdrusk on 2007-06-12
> **lazyart said:**
> Now you have to tell your router to forward traffic on port 80 to your server.

how can i do this?

---

### Post by Rocket2DMn on 2007-06-12
If you have a linksys router you go to the 192.168.1.1 to get into the setup page (default pw = "admin", no username. Go to Applications and Gaming -> Port Forwarding
Set port 80 to forward to your internal IP address (192.168.1.xxx).  Save.
Also, changes to dyndns may take a few minutes to take effect.

---

### Post by tdrusk on 2007-06-12
> **Rocket2DMn said:**
> If you have a linksys router you go to the 192.168.1.1 to get into the setup page (default pw = "admin", no username. Go to Applications and Gaming -> Port Forwarding
Set port 80 to forward to your internal IP address (192.168.1.xxx).  Save.
Also, changes to dyndns may take a few minutes to take effect.

Okay I think I did it.

Can someone check this 
[http://techaspect.dvrdns.org](http://techaspect.dvrdns.org)

---

### Post by lazyart on 2007-06-12
Be patient while the changes make their way around the web.  Who is your ISP btw?  Some of them won't allow you to use port 80 (they block it so people won't host web pages from home).  There is a workaround if that is the case, but we'll wait and see for now....

---

### Post by tdrusk on 2007-06-12
> **lazyart said:**
> Be patient while the changes make their way around the web.  Who is your ISP btw?  Some of them won't allow you to use port 80 (they block it so people won't host web pages from home).  There is a workaround if that is the case, but we'll wait and see for now....

I have alltel.

---

### Post by freebeer on 2007-06-12
how do you forward your ports in your router?  The exact steps are dependant on the model of your router.  Usually there's a list of forwarding rules within the router's software.  

If your server is listening on Port 80, you'll need to create a rule in the router that passes Port 80 to the INTERNAL IP address of your server.

For instance, your external IP address might be 219.134.24.24.  (This would be the number that DynDNS has for your URL).  So if I were a user, I point my browser to techaspect.dvrdns.org and the great Traffic Cop of The Internet routes me to your IP address.  However, at this point I've only gotten as far as your router... not your server.  Your server is dutifully listening for traffic on Port 80 and is getting really bored because no one will talk to it.  That's because you haven't told your router to forward these Port 80 requests on to the internal IP address of the server.  If your internal IP address is 192.168.1.101 then that's the rule you tell your router... forward Port 80 requests to 192.168.1.101.

Hope that helps some.

---

### Post by tdrusk on 2007-06-12
> **freebeer said:**
> how do you forward your ports in your router?  The exact steps are dependant on the model of your router.  Usually there's a list of forwarding rules within the router's software.  

If your server is listening on Port 80, you'll need to create a rule in the router that passes Port 80 to the INTERNAL IP address of your server.

For instance, your external IP address might be 219.134.24.24.  (This would be the number that DynDNS has for your URL).  So if I were a user, I point my browser to techaspect.dvrdns.org and the great Traffic Cop of The Internet routes me to your IP address.  However, at this point I've only gotten as far as your router... not your server.  Your server is dutifully listening for traffic on Port 80 and is getting really bored because no one will talk to it.  That's because you haven't told your router to forward these Port 80 requests on to the internal IP address of the server.  If your internal IP address is 192.168.1.101 then that's the rule you tell your router... forward Port 80 requests to 192.168.1.101.

Hope that helps some.
wahoo!
[http://techaspect.podzone.net/](http://techaspect.podzone.net/)

works!

Now how can I secure this so the other computers in the network can't be messed with. I really need this to be secure.

---

### Post by freebeer on 2007-06-12
Well, security is a whole other aspect.  Since you're behind a router, you've got pretty good security as it is.  Assuming that your only port-forwarding rule is Port 80, all your other ports are shut down, so that one machine (the server) is the only machine on your local network that is vulnerable to the outside world.

That's not to say you're completely safe, but you've got a hardened bunker.  You might want to do some further research on security - it's a realy big topic.  :D

---

### Post by lazyart on 2007-06-12
You still need to install the client on your server so that it can update the ip address for that web address.  As long as the server is running it will continue to update and you'll be set.
High Fives all around.

---

### Post by tdrusk on 2007-06-12
I installed that program. Hopefully it is working correctly.

Now how can I set up a site for my wordpress?

---

### Post by lazyart on 2007-06-12
Try the [Community Documentation Pages]("https://help.ubuntu.com/community/WordPress").  Tons of howtos directed specifically at Ubuntu.

---

### Post by tdrusk on 2007-06-12
Something stupid just happened... The electric went out.

The server is running, but I can't connect to it with
[http://techaspect.podzone.net/wordpress](http://techaspect.podzone.net/wordpress)

I can connect by going to it by typing in
192.168.1.100/wordpress

Any help is appreciated

EDIT: I just checked my ip address and it changed. This means it has to do with dydns and ddns client.

---

### Post by tdrusk on 2007-06-12
I figured it out. My electric went out and my router assigned me 192.168.101 instead of .100. How can I stop this from happening?

---

### Post by silverglade00 on 2007-06-12
I just checked it and got your blog. Left you a comment ;)

To stop that from happening, you need to set your server's address to a static one outside of the DHCP scope of your router. For instance, if your router assigns 192.168.1.1 to 192.168.1.100, set it to 192.168.1.101 or something. If you don't have many machines on your local network, it might be easier just to set them all to static local IPs and turn off the DHCP server in your router.

---

### Post by tdrusk on 2007-06-12
> **silverglade00 said:**
> I just checked it and got your blog. Left you a comment ;)

To stop that from happening, you need to set your server's address to a static one outside of the DHCP scope of your router. For instance, if your router assigns 192.168.1.1 to 192.168.1.100, set it to 192.168.1.101 or something. If you don't have many machines on your local network, it might be easier just to set them all to static local IPs and turn off the DHCP server in your router.

Thanks man. ;)

---

### Post by tdrusk on 2007-06-12
> **silverglade00 said:**
> I just checked it and got your blog. Left you a comment ;)

To stop that from happening, you need to set your server's address to a static one outside of the DHCP scope of your router. For instance, if your router assigns 192.168.1.1 to 192.168.1.100, set it to 192.168.1.101 or something. If you don't have many machines on your local network, it might be easier just to set them all to static local IPs and turn off the DHCP server in your router.

Okay I tried to do what you said, and saw this in my router:
[IMG]http://i18.tinypic.com/4yisf3q.png[/IMG]

Is the static DNS what I need to change?

---

### Post by silverglade00 on 2007-06-12
Looks like we have the same router :)

Well, there are two ways you could go about this. First, it works, don't touch it if it ain't broke. The only problem is that when your power goes out, you will have to go back into the router settings and change the forwarded IP. Second way is to disable that DHCP and go to each machine you have and give it an IP address with 192.168.1.* and subnet mask of 255.255.255.0. It might take a little doing and some rebooting to get it all working right. Do you actually have other machines on this network?

If you go the second route (get it? uhh yeah.), you don't touch those static DNS settings. Instead, click disable next to DHCP Server in your screen shot. Save changes and then go into your Ubuntu network config and turn off DHCP. Give it a static IP and that subnet mask. Then you will probably need to reboot.

---

### Post by lazyart on 2007-06-12
I'll interject my idea here.

1- change the starting IP address to 101.
2- go to Network on your server and get the properties of the wired connection
3- change it from DHCP to static
4- set your ip address on the server to 192.168.1.100
5- Net mask is 255.255.255.0
6- Gateway is 192.168.1.1

This prevents you from having to change settings on any current or future machines.

---

### Post by tdrusk on 2007-06-12
> **silverglade00 said:**
> Looks like we have the same router :)

Well, there are two ways you could go about this. First, it works, don't touch it if it ain't broke. The only problem is that when your power goes out, you will have to go back into the router settings and change the forwarded IP. Second way is to disable that DHCP and go to each machine you have and give it an IP address with 192.168.1.* and subnet mask of 255.255.255.0. It might take a little doing and some rebooting to get it all working right. Do you actually have other machines on this network?

If you go the second route (get it? uhh yeah.), you don't touch those static DNS settings. Instead, click disable next to DHCP Server in your screen shot. Save changes and then go into your Ubuntu network config and turn off DHCP. Give it a static IP and that subnet mask. Then you will probably need to reboot.

See, the problem was the electric went out and the laptops we have, that were already on, stole the servers old connection. I pretty much want my server a guaranteed address to connect to every time.

---

### Post by silverglade00 on 2007-06-12
I think lazyart just won the thread.

---

### Post by tdrusk on 2007-06-12
> **silverglade00 said:**
> I think lazyart just won the thread.

I agree. 

I suppose I will just keep asking questions here.

I have ddclient. What do I need to put in for "Interface used for dynamic DNS service:"?

---

### Post by tdrusk on 2007-06-12
bump

---

### Post by silverglade00 on 2007-06-14
give your network connection. like eth0 or wlan0 or whever your connection is.

---

### Post by lazyart on 2007-06-14
Here's helpful page:
[http://linux.cudeso.be/linuxdoc/ddclient.php](http://linux.cudeso.be/linuxdoc/ddclient.php)

Reading this thread made me set up my own WP blog in a virtual machine.  Pretty cool.

---

### Post by fastpakr on 2007-06-14
SO much nicer to be able to configure DynDNS on the router than the desktop, along with DHCP reservations, etc...

---

### Post by lazyart on 2007-06-14
> **fastpakr said:**
> SO much nicer to be able to configure DynDNS on the router than the desktop, along with DHCP reservations, etc...
It is, but very few routers adhere to the DynDNS standards.  I have a Belkin and it has a place to enter the info and such but it never communicates it correctly.

If you have one of [these]("http://www.dyndns.com/support/clients/hardware/") routers and you use dyndns.org then by all means use the client built into the hardware.

---

### Post by fastpakr on 2007-06-14
> **lazyart said:**
> It is, but very few routers adhere to the DynDNS standards.  I have a Belkin and it has a place to enter the info and such but it never communicates it correctly.

If you have one of [these]("http://www.dyndns.com/support/clients/hardware/") routers and you use dyndns.org then by all means use the client built into the hardware.

I'm not on the list - I actually use a Buffalo WHR-G54S running Tomato 1.07.  In any case, it works fantastically, and gives me a lot of other features that aren't available on the OEM firmware packages.

---

