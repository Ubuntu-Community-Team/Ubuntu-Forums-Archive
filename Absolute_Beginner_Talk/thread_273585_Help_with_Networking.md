---
title: "Help with Networking"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by l1nux on 2006-10-08
Hi there i have installed ubuntu on my pc a few days ago and it is GREAT! i really like it but i am having a lot of trouble getting the internet to work. It dosent seem to pick up my router its a belkin one(if that helps)and its wireless. I foned belkin and they said it was not compatible and i was to call linux!?!?! Im at my wits end about what to do as i REALLY do not wish to put XP back on my pc. Any advice on cheap ubuntu friendly routers would be great or if you Know how i could fix this let me know.
Cheers Andrew

---

### Post by hyper_ch on 2006-10-08
Well, I think it's not a problem with the router but more with your wireless card.

What have you tried so far to get it to work?

---

### Post by l1nux on 2006-10-08
Ive tried puting an ethernet cable from the router to the pc and acessing the router through the ip address but that dosent work i have no security on the router enabled so it should be able to access it ive tried manualy entering the settings on the network part of ubuntu and once i have the settings i activate it press ok and if i go back to network is says that it is not active!!!grrrr!!!

---

### Post by hyper_ch on 2006-10-08
Well, does the router assign you a lan ip by DHCP and if so, did you enable dhcp in your network settings in ubuntu?
If you don't get a lan ip assigned by dhcp by your router did you set correct settings for the static ip then?

---

### Post by RudolfMDLT on 2006-10-08
All networks work the same and they all have to conform to a norm, an ISO standard.

Please check the following first:

1) when you plug in the ethernet cable, does the light come on at the back(I know you're not stupid, check it anyway! :) )
2) Are you running DHCP or are you running fixed IP's? 
3) If you are running fixed IP's check that you have not only entered a correct ip for the Ubuntu machine but also that you have given it a Gateway. The Gateway is the IP of the router.

Hope this helps,

cheers!

---

### Post by bergfly on 2006-10-08
Ok, the router actually makes no difference, and Belkin support is useless, trust me. Unfortunatley using Linux, you will run into a fair amount of techincal support nosense. You just learn to ignore it!

Try doing what  RudolfMDLT has recommended above. If you are not sure about it, here is what to do

The first thing to do as said above is to see if you are using Static or DHCP. Go to System- Administration - Networking and have a look what it says there. Check it for all you network interfaces. By default it should be DHCP.


Assuming it is DHCP, now you need to check if you are getting an IP address. Best to try this first with a patch cable to the router. Wireless can be a nightmare, so lets look at a wired connection first. 

When patched in, open a terminal (Applications-Accessories-Terminal) and Type

*ip address*

This will give you a list of stuff, depending on what you have for networking. Your ip address should show up here, probably under eth0, but you never know. If the router is set to default settings, you should get 192.168.XXX.XXX as your IP address. If there is an issue you might get 169.XXX.XXX.XXX.

Assuming that you get a 192.168 address, your internet should work. If not, check those cables and lights! If you do, then it is time to try that wireless card. Before you do, I recommend finding out what type of chipset you have on your card and doing some reading. Wireless in Linux is something of a black art, although a lot better now than before. 

I doubt the wireless router is to blame, as I have a Belkin sitting here which i use with my laptop. Works fine for me in Ubuntu, but windows users have a lot of issues with it.

---

### Post by RudolfMDLT on 2006-10-09
I hope you got it working! What bergfly said is true. The router doesn't take offence to Linux. The helpdesk support guy probally never even heard of linux, which is a shame. Part of the TCP/IP standard is that the protocol must not be OS specific.

Anyway,

CHeers!

---

### Post by Straevaras on 2006-10-09
I use a Belkin router at home and it works with Ubuntu just fine.  I didn't have to change any configuration or anything.

What kind of Wireless card and Ethernet chipset do you have?  I know Linux has always been iffy with wireless interfaces, so try getting it to work with your Ethernet first.  My wireless works just fine as well and I have an Intel2915ABG.  Ubuntu might be having a hard time configuring the Ethernet and Wireless card if it's something it doesn't recognize.  Although I _shouldn't_ be unable to configure the Ethernet.  The only time I've had that problem is in RH9. *shivers*

---

### Post by sailor2001 on 2006-10-09
in terminal:  ifconfig   to double check ip, gateway, mask numbers

---

### Post by majoorpa on 2006-10-10
I am also  Belkin router with wireless. I had troubles accessing internet initially. That was not related with identifying the network card or Belkin. My network card and Belkin was identified automatically by Ubuntu. I am also using wireless on Belkin. I am ready to give info which stepped I followed to rectify my troubles

---

