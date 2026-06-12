---
title: "Newbie Networking Advice"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by 65bit on 2008-02-09
Hi,

I’m new to Ubuntu and most all things networking.  I currently have a home and business network split across two subnets at my house.  It was put together by a friend a couple of years ago; has always seemed a bit kluge and doesn’t currently support all of our needs.  I’m looking for beginner’s advice on understanding the best approach to accomplish what I’m after.

In summary, I currently have this equipment available (not all now in use): 

[LIST]
[*]A broadband connection to the internet
[*]A single firewall
[*]A Dell 3424 switch with VLAN capability
[*]A wireless Linksys router
[*]A ‘regular’ Linksys router
[*]Four “work stuff” systems - servers and p.c’s.  (currently on 192.168.5.x with static addresses)
[*]Five “home stuff” systems – media server, p.c’s and laptops  (need to be accessed only by internal users; currently on 192.168.100.x with static addresses, except the wireless router serves as a dhcp server for a couple of home laptops)
[*]A couple of hubs
[*]A block of 5 external IP addresses
[/LIST]
What I’d like to be able to do:

[LIST]
[*]Have both work & home stuff get out to the internet
[*]Have any home stuff machine access any work stuff machine
[*]Block work stuff machines from accessing home stuff machines
[*]Access to work stuff machines from the outside
[*]Block access to home stuff machines from the outside – except - if completely secure, I’d like to be able to access one specific home stuff machine from the outside
[/LIST]
Some of my random questions
[LIST]
[*]Is separating the work and home traffic on two different subnets the best approach?
[*]Can I accomplish the ‘routing’ and traffic rules I’m after with only one VLan capable switch or do I need two switches with a router between them for the two subnets?
[*]Outside access to the work servers is currently done via port forwarding.  Is this the best (most secure) approach or should they be assigned an external ip address?
[*]I know my Internet connection needs to plugged into the WAN port of my firewall, and I know the LAN port of my firewall is then the main feed to my internal network; but then I’m lost on what it should plug into next and then what that should plug into, etc to accomplish what I’m after and what the default gateways for those devices as well as the work and home stuff systems should be
[/LIST]
ANY help, advice, beginner links, etc would be greatly appreciated.

Thanks,
David

---

### Post by mrsteveman1 on 2008-02-09
With a good firewall all the restrictions you want to place on traffic are perfectly reasonable and shouldn't be hard to implement, but it may take some careful planning to get the configuration right with the devices.

My first question is this, how important is it to restrict the business machines? There are certainly ways to secure machines from each other without using separate subnets, so what sort of things are you worried about when you say you want to keep the business machines from accessing the home machines?

There always must be a router between 2 subnets/vlans, and in order for that to work the router must either be the VLAN switch itself (integrated device), or must support VLAN trunking, which Linksys routers don't do.

With a setup this complex you may quickly outgrow the Linksys boxes (I'm assuming you are using the consumer types), so it might be necessary to implement something new to make your life easier as well.

Anyhow let me know what your concerns are.

Steve
Cisco Certified Network Associate #CSCO11241448

---

### Post by 65bit on 2008-02-09
One of the business servers runs IIS and hosts a publically accessible website.  Two other business servers support terminal services, where a couple of business partners login and share files, apps, etc.

Myconcern here is I don't want anyone who has access to the business machines from the outside to somehow be able to 'break out' and get to my home machines where I have personal information.  But, I'm about to start working from home, so I need to be able to easily get to the business machines from that 'home network side'.

The Dell 3424 swtich, which my friend put in, talks about supporting trunking; but hard for me to tell if it means between itself and other switches or inside its own 24 ports. From the manual: 
[LIST]
[*]GARP VLAN Registration Protocol (GVRP) provides IEEE 802.1Q-compliant VLAN pruning and dynamic VLAN creation on 802.1Q trunk ports. When GVRP is enabled, the device registers and propagates VLAN membership on all ports that are part of the active underlying "Spanning Tree Protocol Features" topology.
[/LIST]
I don't see anything to indicate he set that up.  As mentioned, I think it's a bit kluge now.

Any thoughts would be appreciated.  I'm pretty much lost from a conceptual perspective with integrating the sunbets seamlessly (if separate subnets are the best approach), yet providing the protection I'm after.

Thanks

---

### Post by mrsteveman1 on 2008-02-09
The Dell 3424 switch does support 802.1q trunking between multiple switches or between a switch and a router (the only way to route between VLANs btw), but as far as I know there are no consumer grade routers that do. If the subnets are split right now, what is joining them together? Which router are you currently using?

GVRP is just a way to ensure that all connected trunked switches have consistent VLAN information, so that they don't need to all be configured manually.

From what you've said i think the best approach is to keep things separated by zone with a firewall between the zones. Since you have an IIS server as well as terminal services running on the network you definitely need to keep that traffic separate since, I'm assuming, its business critical traffic. You may want to consider investing in a hardware edge security device, which would then be your firewall, but also route between the VLANs on the switch to keep traffic separate.

You sound like you have a good grasp on how things work so there are definitely multiple options. First there are commercial products like Astaro ([link]("http://www.astaro.com/our_products/astaro_security_gateway/model_comparison")), and Smoothwall ([link]("http://www.smoothwall.net/products/smoothguard1000/")), these are integrated devices which run linux with custom interfaces and management software. Astaro has a lot of different models for all size networks, and Smoothwall seems to be a more general device for many purposes. I have used both, and the Astaro and Smoothwall devices both support zones and fine grained control over traffic like you want. Of the 2, the Astaro software is definitely easier to use.

There are also software packages you can use on existing hardware, the Smoothwall and Astaro software are both free for use in situations like yours. I currently use the Astaro software on my own hardware, and I have been quite happy with how it works, though to do this you would need to choose the hardware carefully. You can demo the interfaces on both of these software packages [here]("http://www.astaro.com/contact/livedemo/(type)/asg_live_demo_landing_page") and [here]("http://demo.smoothwall.net/corporatefirewall/4.0/cgi-bin/index.html").

There are of course other options, you can always run a regular Linux distribution as a firewall, through this is fairly complicated and difficult to manage. You can also run Windows Server as an edge security device on your own hardware, it can definitely route between VLANs given the right hardware, and does a good job as a firewall as well.

---

### Post by 65bit on 2008-02-10
Steve - - thanks very much for the input.  I will dig into the edge security devices as well as the software packages you mentioned and see what I can learn.

I may be back with more questions :) but definitely appreciate your help

David

---

