---
title: "Setting up static IP address on home webserver XAMPP"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by undesign on 2007-04-23
Hi,

I have successfully setup Xampp on Ubuntu desktop edition and have it running across the network with a dynamic IP of 192.168.1.198 issued from my orange livebox.  I want to change this to a static IP address so that I can permanently run a wireless webserver from it.

I also will still need to connect to the internet with this machine. Will setting up a static ip mean that I cannot connect to the livebox with DCHP?

Any ideas?

---

### Post by dannyboy79 on 2007-04-23
there's 2 different ways to set your ubuntu box to have a static ip but I think you may be misunderstanding which ip you need to be static so you can run your webserver. you actually need your external ip to be static as well as your internal ip. the way that you get your external ip to be static is just get a free hostname and domain name which will be tied to your changing external ip address. if your external ip is already static and you don't care about having to type in your ip to get to your webserver than you don't need to register your ip with a free dynamic host. (ie: [www.dyndns.com)](www.dyndns.com)). then it appears as though you have this orange livebox between your internal lan and the internet, you'll have to forward port 80 to your internal ip address of your webserver (192.168.0.198). 

the 2 ways to make sure the 192.168.0.198 stays what it is, is either leaving your orange livebox to be dhcp and make it so that it always "reserves" that exact ip address to the MAC address of your webservers nic card, or by using ubuntu to set the nic as a static ip. you'll want to make sure that you don't chose a stat c ip that can be given out by the dhcp server though, because then you'll have ip conflicts. is your orange livebox a REAL dnsserver? if it isn't then when you setup ubuntu with a static ip, you'll need to use the dns servers that your isp gave you. 

before I go to far and confuse you, please tell me which router you'd like to take and answer a few questions.

1.) is your external ip dynamic? (most residential isp's provide dynamic ip, meaning they do change)

2.) do you know how to configure your orange livebox? ie; change dhcp server ip's, does it have the capability to "reserve" an ip to a MAC address or marry them together?

3) do you kow what your isp's dns server's are?

4) is there any particular reason the ip for your webserver is so high? (192.168.0.198)

---

### Post by Cypher on 2007-04-23
If you only have one network interface in your computer, then yes setting a static IP on there will prevent your Internet access.

You would want to put in a second NIC that is homed to the internal network with a static IP and you will have what you want.

Regards

---

### Post by undesign on 2007-04-23
Thanks for the help both of you. A little out of my depth but I kind of see what you mean.

I didn't realise I had an external IP address but I knew that I could direct through a service like no-ip.com or whatever its called to a machine on my network.

My plan is simply to learn how to set up a machine on my network as a webserver. Ultimately I would like to have external access, but if its more trouble than its worth the internal LAN access will do for now.


I checked my router admin settings and found the following

> Port Forwarding - NAT

Port forwarding is used to forward specific incoming connections toward a dedicated PC on your network.

You do not need to change any of these settings unless asked to do so by Customer Support.

Your computer's IP address : 192.168.1.**

Service	Protocol	External port	Internal port	Server IP address	Remove

   
DMZ set-up

The DMZ will open all ports on one chosen computer.
Warning: In the DMZ, the computer becomes accessible from the Internet and more vulnerable to hackers. Click on the button "Configure DMZ on this computer" to set it up.

No DMZ is configured on your access point. 


I think this is where I configure the external IP.


My ultimate plan is to set up a WLAN but just now I am connecting to the router by wired USB on my Ubuntu machine. I have an old wireless BT Voyager 1010 adaptor but I can't get that working at the moment.

I wanted to access the internet on this machine also for updates to ubuntu and other software installation but if losing internet connection is the price I pay for setting up a webserver then so be it.

What should I do next?

---

### Post by dannyboy79 on 2007-04-23
> **Cypher said:**
> If you only have one network interface in your computer, then yes setting a static IP on there will prevent your Internet access.

You would want to put in a second NIC that is homed to the internal network with a static IP and you will have what you want.

Regards

Maybe there's some huge misunderstanding here but the above statement is completely false. All my machines have a static ip, even my winbloz box. Cypher, he isn't using his ubuntu box as a router. the only time you need 2 network cards is if you want to use your computer as a router with NAT and what not.

---

### Post by undesign on 2007-04-24
So what do I do?

Any ideas?

---

### Post by dannyboy79 on 2007-04-24
well, you need to answer the questions I have already asked so that I can help you.

before I go to far and confuse you, please tell me which router you'd like to take and answer a few questions.

1.) is your external ip dynamic? (most residential isp's provide dynamic ip, meaning they do change)

2.) do you know how to configure your orange livebox? ie; change dhcp server ip's, does it have the capability to "reserve" an ip to a MAC address or marry them together?

3) do you kow what your isp's dns server's are?

4) is there any particular reason the ip for your webserver is so high? (192.168.0.198)

No matter what you're going to want to forward port 80 to your internel web server no matter what. this will allow your web server to be displayed on line.So if you don't register with no-ip.com you would have to type in your external ip to get to your webpage. then the traffic will get forwarded from the internet thru your orange livebox to your internal machine due to the port forwarding you setup. Now to make sure that the machine with your webserver is always the same number that your port forwarding to, you need to either set it static using the os (ubuntu) or set it static using a feature some routers have where it marries the MAC address with the ip of the machine. this way, your dhcp server (orange livebox) will never give out 192.168.0.198 to another machine which would result in your web pages not being displayed. heres a great guide for setting up a very basic webserver in dapper but should apply to any distro. [http://myy.helia.fi/~karte/install_apache_on_ubuntu.html](http://myy.helia.fi/~karte/install_apache_on_ubuntu.html)

---

### Post by undesign on 2007-04-24
> well, you need to answer the questions I have already asked so that I can help you.

before I go to far and confuse you, please tell me which router you'd like to take and answer a few questions.

1.) is your external ip dynamic? (most residential isp's provide dynamic ip, meaning they do change)

**** From Orange Support

IP address

Your IP address is allocated dynamically via DHCP- you do not need to set this. We are unable to offer a static IP address.

Not sure have a look at this, does this mean you can set a static IP address or is port forwarding what you do once you have a static external IP address

[http://www.portforward.com/english/routers/port_forwarding/Inventel/Livebox/HTTP.htm](http://www.portforward.com/english/routers/port_forwarding/Inventel/Livebox/HTTP.htm)


2.) do you know how to configure your orange livebox? ie; change dhcp server ip's, does it have the capability to "reserve" an ip to a MAC address or marry them together?

**** Yes there is an admin area for the router. The server reserves ips from
192.168.1.9 to 192.168.1.200

There is a page called network where I can disable DCHP and possibly alter the following settings

Enable DHCP server	
LAN IP address		
Broadcast LAN IP addresss		
Subnet mask		
DHCP start address		
DHCP server end address	

As far as mac addresses go When a pc or mac is given a dynamic IP address such as my UBUNTU machine such as 192.168.1.198 via DCHP, that machines MAC address is visible as a machine attached to the network

There is an access point IP address listed starting with 62.136 . . . . 
don't know what relevance this has.

3) do you kow what your isp's dns server's are?

******* If you mean dynamic DNS servers. Yes

[www.dyndns.org](www.dyndns.org)

[www.no-ip.com](www.no-ip.com)


4) is there any particular reason the ip for your webserver is so high? (192.168.0.19

**** See point two for the range of IP addresses.

Can they be changed? I don't want my other two machines not to be able to connect to the internet. Will changing the range of IPs affect the connection to DCHP of these machines.

Hope this answers your points

Am I on the right track?

---

### Post by dannyboy79 on 2007-04-25
> **undesign said:**
>  Hope this answers your points

Am I on the right track?

Well, everything is what I expected except for two things.

Port forwarding is what you need to do after you set a static ip for your internal lan'd computer BUT you may not have to set the ip to be static thru Ubuntu IF (see directly below)

You didn't answer if you can "reserve" (thru your orange livebox) a certain IP address (192.168.0.198) to the MAC address of your webserver machine. This way you don't have to worry about setting static ip within Ubuntu because it'll always get the same ip from your orange livebox dhcp server. Look for something that states reserve ip or mac OR maybe static dhcp it's also called.

Ok, then the "other" dhcp server is what gives your internal computers their ip address in your local lan. you stated that your orange router/dhcp server hands out ip addres from 192.168.0.9 thru 192.168.0.200. This is fine. Is the orange router's ip address 192.168.0.1? If not, what is it?

To make something clear, your attached to an external dhcp server which gives you your external ip address. this can change, so in order to be able to see your website, you'll either have to always know your external ip and type that into a web browser, or you associate a hostname using either dyndns or no-ip.

> **undesign said:**
> There is an access point IP address listed starting with 62.136 . . . . 
I looked at my previous post, I don't see anything about me saying anything or mentioning anything about 62.136....., so what are you talking about here? 

If you're not going to set Ubuntu to have a static ip and you can enable your orange router to do this thru the "reservartion" technique, than don't worry about your dns servers.Normally these are displayed somehwere within your orange routers admin pages somewhere. THese dns server basically are what's used for when you open firefox and you type in [www.gogle.com](www.gogle.com), firefox will look to the isp's dns server's to find out what ip address that [www.gogle.com](www.gogle.com) is, so that it can go to that webpage. you stating what you did regarding this question is way off base here. DNS server are domain name servers. They associate hostname (domains) to ip address so that we all don't have to type in an ip address to go to a webpage. I wanted to know what the dns servers that your ISP (internet service provider) uses because it's often good to set them when you set Ubuntu to have a static ip, AGAIN THOUGH, if your orange router can do static dhcp or reserver an ip to a MAC address, than just forget me saying this as it appears to be confussing you.

Ok, I still don't understand why ddhclient within Ubuntu is grabbing such a high IP address when your internal dhcp server hands out ip address 192.168.0.9 first. ANyway, it doesn't really matter I was just curious. You can change it but again, let's first see if your router (orange livebox) can do this for ya using what is referred to as static dhcp or reserving an ip to a MAC address. 

so let me know the few things that I have asked above. also, did you perform the steps in the link I gave you about setting up apache2 which is basically the webserver software?

---

### Post by compmodder26 on 2007-04-25
> **dannyboy79 said:**
> I looked at my previous post, I don't see anything about me saying anything or mentioning anything about 62.136....., so what are you talking about here?

That would probably be the external IP his/her ISP is assigning to the router.

---

### Post by dannyboy79 on 2007-04-25
> **compmodder26 said:**
> That would probably be the external IP his/her ISP is assigning to the router.


oh, you know what, I totally misread that. I thought his statement was, "There is no access point IP address listed starting with 62.136 . . . . " Hence why I said what I did. DISREGARD my statement, I can't read. :-)

---

### Post by compmodder26 on 2007-04-25
We've all been there. :)

---

### Post by jpatton on 2007-04-25
You know, depending on who is provider is, accessing his box from the internet may  be a mute point, regardless of using dyndns or any other solution. Most provider's anymore block inbound traffic on specific ports. He should configure the router to forward traffic from some other http port to his internal webserver's port 80. Alternatively if possible, place a webserver as a DMZ host and configure apache to listen to a port other than 80. 

I have noticed that over time a provider will notice regular incoming traffic and begin to close those ports as well, personally I think it's crap, but I can certainly understand the business logic behind that though.

---

### Post by dannyboy79 on 2007-04-25
i would never setup my main machine as a dmz. now if it's isolated from my main network with a hardware firewall between me and it than maybe. That's just me and I would hope that you inform others of the security risk in doing this. It's not like it's hard to do, he's almost there but that's a great point if that's the case with his provider regarding him using his **ip/port ** to view his webpages, then just forward that port to port 80 on his internal box. (NOTE: the forward slash between the ip and the port is suppose to be a colon, but the forum kept turning it into  a smiley because the p after the colon.)

---

### Post by jpatton on 2007-04-25
You take all the fun out of it when you urge people to setup firewalls! ;)

---

### Post by dannyboy79 on 2007-04-25
> **jpatton said:**
> You take all the fun out of it when you urge people to setup firewalls! ;) You must be a hacker who owns a botnet network!! I don't like people like you cause you bang at my ssh and  ftp doors all day long with brute force attacks but you'll never get in.

i never urged anyone to setup a firewall, i merely informed you how my setup is. It's not smart to tell a newbie what to do but not inform him of the ramifications!

Some home routers refer to a DMZ host. A home router DMZ host is **a host on the internal network that has all ports exposed,** except those ports forwarded otherwise. (do you really want to open every port on your main computer?)

This is not a true DMZ by definition since these pseudo DMZs provide no security between that host and the internal network. That is, the DMZ host is able to connect to hosts on the internal network, but hosts in a real DMZ are prevented from doing so by the firewall that sits between them.

I am guessing that you have a home router with a dmz option. this is exaclty what they are talking about, it provides no protection to the internal network!!!

---

### Post by jpatton on 2007-04-25
Nope not a hacker thanks, was merely providing my insight on how the major broadband providers work with regards to hosting personal content. To be frank, he would be breaking his agreement with whatever provider he has by setting up a server that is available to the public network. I dont' know of any provider that has a provision that allows this type of use in their agreements.

Not that I am an expert on the law, but I have heard that not providing an adequate means of protecting your own network from attack can be grounds to be sued as part of a class action if your IP/Computer was hijacked and used in a DOS type attack.

As to my personal network, I don't use a home router, but having been in the technical support arena since 1991 I'm very familiar with the average person's home configuration, and most of those Wireless/Wired Broadband Cable/Router devices have some kind of DMZ option. I personally don't feel it necessary to inform someone as to how to secure their own network, as most people anymore fully understand what a Firewall is and don't need me to remind them of the importance of them.

Thanks,

---

### Post by dannyboy79 on 2007-04-25
> **jpatton said:**
> Nope not a hacker thanks, was merely providing my insight on how the major broadband providers work with regards to hosting personal content. To be frank, he would be breaking his agreement with whatever provider he has by setting up a server that is available to the public network. I dont' know of any provider that has a provision that allows this type of use in their agreements.

Not that I am an expert on the law, but I have heard that not providing an adequate means of protecting your own network from attack can be grounds to be sued as part of a class action if your IP/Computer was hijacked and used in a DOS type attack.

As to my personal network, I don't use a home router, but having been in the technical support arena since 1991 I'm very familiar with the average person's home configuration, and most of those Wireless/Wired Broadband Cable/Router devices have some kind of DMZ option. I personally don't feel it necessary to inform someone as to how to secure their own network, as most people anymore fully understand what a Firewall is and don't need me to remind them of the importance of them.

Thanks,


as most people may know what a firewall is, they don't know what a DMZ server is and as I tried pointing out, these home routers with the option to point to a DMZ server is completely insecure and you're telling me that I take the fun out of it by telling him her should be firewalled? I don't understand, one second you say go DMZ, then the next second you're talking about the person get get sued by not securing their network blah blah blah. 

I don't know what's going on here but you're really confusing me.

---

### Post by jpatton on 2007-04-25
lol...I'm bored

---

### Post by undesign on 2007-04-26
> **jpatton said:**
> Nope not a hacker thanks, was merely providing my insight on how the major broadband providers work with regards to hosting personal content. To be frank, he would be breaking his agreement with whatever provider he has by setting up a server that is available to the public network. I dont' know of any provider that has a provision that allows this type of use in their agreements.

Not that I am an expert on the law, but I have heard that not providing an adequate means of protecting your own network from attack can be grounds to be sued as part of a class action if your IP/Computer was hijacked and used in a DOS type attack.

As to my personal network, I don't use a home router, but having been in the technical support arena since 1991 I'm very familiar with the average person's home configuration, and most of those Wireless/Wired Broadband Cable/Router devices have some kind of DMZ option. I personally don't feel it necessary to inform someone as to how to secure their own network, as most people anymore fully understand what a Firewall is and don't need me to remind them of the importance of them.

Thanks,

Thanks for trying to find a solution both of you but this is getting out of hand. I don't want to break my service agreememt and what I don't need is to set up another commercial webserver. I already have a website with php/mysql that I can use to test things commercially. 
I don't want to enable all the ports on my computer to run a webserver either. The last thing I want is to make my network vulnerable to hackers any more that it is in general. 

If you go back to my first post, I intend to set up a wireless LAN but don't have a suitable wireless device yet. I am connecting the Ubuntu box with a wired connection to my livebox just to get it working on my INTERNAL network. I don't really want to go through Orange to provide external access, I would rather go down the path of learning how to set up a wireless webserver that I can connect to from another computer and if eventually I can get another person nearby to connect, then so much the better.

So what I really need to know is how to set my ubuntu box to have an INTERNAL static ip address. As far as having a webserver already, the clue is in the title **Setting up static IP address on home webserver XAMPP**

I already have xampp running with basic security (I know people say don't use XAMPP its not secure - well its more secure than letting me set up apache/php/mysql manually)  and  I am able to connect to the ubuntu box from another computer on my network which almost suits me. 

What I do not want is to spend loads of time configuring wordpress or joomla or some other CMS and then find that Orange deals me a completely different IP for some reason.

By the way my range of internal ips is 192.168.1.9 to 198.168.200 not 192.168.0.9 to 192.168.0.200.

the default admin IP (i.e the root of the network is 192.168.1.1)

This does not seem high to me except that DCHP gave me a default IP so close to the edge of my available addresss.

I would have thought if I could set a static IP address on the ubuntu box lower than those reserved for the network, then this would work wouldn't it?

---

### Post by Austin_KW on 2007-04-26
Why bother with static ip. Just use dhcp & the dns on your router , it is much simpler.

You can instruct you machine's dhcp client to register its name with the dns masquerade on your home router.  Then you can address your PC's by name on your home network.

Use your favourite editor to change the file /etc/dhcp3/dhclient.conf (gksudo gedit /etc/dhcp3/dhclient.conf)and add a line to register *yourPcName*
Add **send host-name *"yourPcName"***

then rerun dhcp clinet to register the address
sudo dhclient eth0

another PC on the network can then address your pc by nane
eg [http://yourPcName/](http://yourPcName/)
or [http://yourPcName.yourDefaultDomain/](http://yourPcName.yourDefaultDomain/) probably [http://yourPcName.home/](http://yourPcName.home/) 

If you do decide to give your PC a static ip address yo should assign one outside the dhcp pool as not all routers will watch the LAN traffic for conflicts.
eg. you should assign a static address in the range 198.168.1.201 to 198.168.1.254

---

### Post by dannyboy79 on 2007-04-26
> **undesign said:**
>  Thanks for trying to find a solution both of you but this is getting out of hand. 
Ah, I wasn't "trying" to find you a solution, I AM providing you a solution to HAVE a **home webserver** that is accessible from the "internet". I didn't know what XAMPP was (i know I should have looked it up but the main thing I concentrated on was web server from home) I merely thought it was some kind of program that served something similar to webpages etc etc?? Now that I understand that you already have an external webserver that you pay for (IMHO this is a waste of money cause you could do this yourself) I can help you more directly now and not have to get into such detail and ask you all these extra questions that are related to setting up a web server which would be accessible from the "internet".
> **undesign said:**
>  I don't want to break my service agreememt and what I don't need is to set up another commercial webserver. I already have a website with php/mysql that I can use to test things commercially. 
I don't want to enable all the ports on my computer to run a webserver either. The last thing I want is to make my network vulnerable to hackers any more that it is in general.  I have not heard of any ISP's ever having anything like restrictions within the contract that states you can't run a webserver or run a ftp server or the like but that doesn't mean it isn't true. Some ISP's actually block some incoming ports (i've read in this forum) which you would find out anyway when you tried my suggestion. So I suppose in theroy, if they are blocking it, than I guess it may just be in the contract. (i don't have this problem with Road Runner) I wouldn't want you to open all your ports either!!!! Hence why I informed you what a DMZ server option in most home routers does. You wouldn't have to do that either, all you have to do is forward 1 port to your internal port 80. The advantage of a DMZ server option is that it will allow all services thru which makes it easy if you have a DMZ server seperate from your main network so that you don't have to sit there an open up each port for all the different services a server may be running. You don't want to do this as I already stated repeatedly.

> **undesign said:**
>  I don't really want to go through Orange to provide external access, 
This statement makes no sence at all, your ISP is always only going to provide you with 1 ip address, you apparently aren't understanding how all this works. You have a device in your residence which is like a gateway (you called it orange livebox), the internet comes into this device and then "routes" (hence why they are referred to as a router) the internet access to each and every device that is connected to it. Most routers will also have a built in firewall and built in dhcp server to give your internal network ip addresses. You're almost making it sound like you don't have internet access on your ubuntu machine by stating what you have stated, you don't need to give ubuntu an "external" ip address, not unless of course you wanted to run more than 1 of a particular service that's accessible from the internet from within your internal network. Meaning, you can't forward port 21 to your ubuntu machine and also your windows machine if htey both had ftp servers on them that you wanted to access from the "internet".

> **undesign said:**
>  So what I really need to know is how to set my ubuntu box to have an INTERNAL static ip address. As far as having a webserver already, the clue is in the title **Setting up static IP address on home webserver XAMPP** 
I have told you repeatedly how to do this and you have not yet informed me if your orange live box has this capability. Does your orange livebox have a place where it allows you to "marry" your ubuntu MAC address with the IP that the orange livebox has assigned it (192.168.1.198 or whatever you said before)

> **undesign said:**
>  I already have xampp running with basic security (I know people say don't use XAMPP its not secure - well its more secure than letting me set up apache/php/mysql manually)  and  I am able to connect to the ubuntu box from another computer on my network which almost suits me.  What do you mean almost suits you? Is this because you're afraid that ubuntu's ip address might change? This is obviously why you want to set ubuntu to be static correct?

> **undesign said:**
>  What I do not want is to spend loads of time configuring wordpress or joomla or some other CMS and then find that Orange deals me a completely different IP for some reason.  
Again, you're not udnerstanding how this works. Your ISP gives you an IP address thru it's dhcp server, that'll be a number NOT like 192.168.... or NOT like 10.0....... because those IP address are for "INTERNAL NETWORKS" so you have nothing to worry about here if you don't want to access your ubuntu machine from the outside "internet" If you do, than I have already repeatedly told you how to make sure that your External IP is married to a certain hostname so that you can always access it even if Orange gives you a different one. Just so you know, you can access your ubuntu machine from the outide internet by typing in 192.168.1.198 because that's NOT YOUR OUTSIDE (INTERNET) IP ADDRESS. You need to know that in order to access your  ubuntu box from the internet. What happens is that if you're on the outside of your network and you want to access your internal machines,  you FORWARD the certain port you want to access on your Ubuntu box from the Orange Livebox to your Ubuntu box. So then what happens is that if you were at the library and you typed in http://"YOUREXTERNALIPHERE then the packets would go to your router (that's your orange thingy) and your router would review the packets and it's "confie file or setup" and say, hey, I need to forward these packets to this IP address. (this ip address being whatever you told it to forward to, which in your case 192.168.1.198) 

Are you getting this now??????

> **undesign said:**
>  By the way my range of internal ips is 192.168.1.9 to 198.168.200 not 192.168.0.9 to 192.168.0.200.  
That's irrelavent, after reading all the above you should understand now why the ip doesn't matter as long as you know what it is. 

> **undesign said:**
>  the default admin IP (i.e the root of the network is 192.168.1.1)  
Ok, that's what I figured but I wanted to make sure since it's handing out such a high ip address.

> **undesign said:**
>  This does not seem high to me except that DCHP gave me a default IP so close to the edge of my available addresss. 
What do you mean doesn't seem high to you? You stated your self that your orange livebox built in dhcp server hands out .9 thru .200, why in the world it handed out .198 is beyond me. It should have stated at the beginning of it's range, being .9.

> **undesign said:**
>  I would have thought if I could set a static IP address on the ubuntu box lower than those reserved for the network, then this would work wouldn't it?  Yes it would, you're absolutely correct hence why I asked what range of ip's your dhcp server gives out. BUT, as I stated, the easier method is to set your orange livebox to use "static dhcp" IF it has it so again, please let me know if you can do that, if not, than i'll help you set up ubuntu to have a static ip.

---

### Post by dannyboy79 on 2007-04-26
> **Austin_KW said:**
> Why bother with static ip. Just use dhcp & the dns on your router , it is much simpler.

You can instruct you machine's dhcp client to register its name with the dns masquerade on your home router.  Then you can address your PC's by name on your home network.

Use your favourite editor to change the file /etc/dhcp3/dhclient.conf (gksudo gedit /etc/dhcp3/dhclient.conf)and add a line to register *yourPcName*
Add **send host-name *"yourPcName"***

then rerun dhcp clinet to register the address
sudo dhclient eth0

another PC on the network can then address your pc by nane
eg [http://yourPcName/](http://yourPcName/)
or [http://yourPcName.yourDefaultDomain/](http://yourPcName.yourDefaultDomain/) probably [http://yourPcName.home/](http://yourPcName.home/) 

If you do decide to give your PC a static ip address yo should assign one outside the dhcp pool as not all routers will watch the LAN traffic for conflicts.
eg. you should assign a static address in the range 198.168.1.201 to 198.168.1.254


very few home routers are dns servers, they only forward dns requests to the ISP dns servers so I am not sure if this would work but it is a good idea. he can also set it to be static using 192.168.1.2 thru 192.168.1.8 but your main point is correct, he should assign any number outside the dhcp server's range. If he does set ubuntu to be static, some routers fall short of forwarding the dns requests to the ISP dns servers and then you lose internet. You don't lose internet but you'd only be able to surf by ip addresses which I don't know of anyone who know the ip addresss of all the websites they surf on. So that was my point of asking him what his ISP dns servers were unless of course his home router is a true dns server which very few are. This is a common problem if you read the forums regarding dns issues and the fact that dhclient will keep asking the router for the dns server but it tells dhclient that itself is the dns server but it really isn't a TRUE one, it only forwards the request so you have to change your dhclient.conf so that it DOESN'T ask the router for the dns servers and that way the ones you put within the networking gui under system admin, won't get overwritten each time you renew your dhcp lease. Like I said, this problem is everywhere in the forums.

---

### Post by Austin_KW on 2007-04-26
A lot of routers  will resolve lan addresses if the name is sent in the dhcp request. It does not need a full dns server/cache, it has all the information in the dhcp leases. You may save a couple of miliseconds when bypassing the dns masquerade but most people will not notice this as a fraction of the dsl delay.

If dhcp returns a DNS server address on the LAN, then there is at least DNS forwarding/masquerading in the router. The problem is usually that the ISP dis not provide a DNS server address in its response over the ppp link and then the ISP's dns must be manually entered in the router config.

---

### Post by undesign on 2007-04-27
> I have told you repeatedly how to do this and you have not yet informed me if your orange live box has this capability. Does your orange livebox have a place where it allows you to "marry" your ubuntu MAC address with the IP that the orange livebox has assigned it (192.168.1.198 or whatever you said before)



OK, I think I know what you are saying, forgive me for being slow, this is a beginners forum after all, and I am new to linux and setting IP addresses.

In answer to your question there is only an IP address for the connection to the internet through the livebox and that is 62.86.***.***. How do I know this? when you log into the admin area of the router under my services > internet 

You are connected to the internet

Your IP address is 62.86.***.***  

This is listed in the information about the system as the WAN IP address

there is also a 

Gateway, Primary and Secondary DNS server address in there also.

It doesn't matter whether I log into this admin area on Windows, OSX or Linux, it says the same thing. So this has to be the IP address of the router?

As far as marrying this address with a mac address, the router itself has a mac address but the individual machines on the network have device addresses, not sure if this is the same thing as a mac address.

There is nowhere in the admin area of the router to change the mac address

There is a page in the admin area called network where you can enable or disable dchp and set alternative range of addresses for your network. But not for a particular machine I don't think.

I have tried googling orange inventel livebox static dhcp to find an answer but have drawn a blank. I cannot find the answer on the Orange support pages either.

Not sure where to go next!

---

### Post by Austin_KW on 2007-04-27
Routers implememt static dhcp in a couple of different ways. 

In the dhcp options there may be a 'check box' that says something like 'alyways use the same address'. In other routers is is done by setting a large expiry timeout on the lease (how long the address is assigned to the pc). 

Some routers will give this as a option line '1 hour', '1 day', '1 week', '1 month', other routers will give it a number which is seconds. Setting the lease expiry timeout to the highest value you can will, in effect, create a static dhcp address assignment (because the timer starts again everytime the PC asks for its address. 

Sometimes this option is not in the dhcp options but is found wherever the router lists connected devices. This would list your connected MAC addresses and associated IP addresses. Selecting one of the connected devices may give an option like 'always use this address'.

> There is a page in the admin area called network where you can enable or disable dchp and set alternative range of addresses for your network. But not for a particular machine I don't think.
There is no need to disable dhcp to use static addresses. DHCP only assigns an address if a client PC asks for one. The range of addresses is called the dhcp pool and clients are assigned an address in this range, usually in order from first to last. If you want to give a static address to a pc then you just pick a valid address outside the pool, in your case this would be addresses [2..8] and [201..254] (0 is invalid, 1 is your router, and 255 is broadcast/everyone).

---

### Post by undesign on 2007-04-27
Thanks for your reply Austin,

There are no options that I can find that say always use this address. It looks like the router has very basic functionality.

I think I will just have to manually pick one outside the pool and have done with it.

If I go back to your previous post, that gives instructions on how to set that doesn't it?

Here it is I think

> Why bother with static ip. Just use dhcp & the dns on your router , it is much simpler.

You can instruct you machine's dhcp client to register its name with the dns masquerade on your home router. Then you can address your PC's by name on your home network.

Use your favourite editor to change the file /etc/dhcp3/dhclient.conf (gksudo gedit /etc/dhcp3/dhclient.conf)and add a line to register yourPcName
Add send host-name "yourPcName"

then rerun dhcp clinet to register the address
sudo dhclient eth0

another PC on the network can then address your pc by nane
eg [http://yourPcName/](http://yourPcName/)
or [http://yourPcName.yourDefaultDomain/](http://yourPcName.yourDefaultDomain/) probably [http://yourPcName.home/](http://yourPcName.home/) 

If you do decide to give your PC a static ip address yo should assign one outside the dhcp pool as not all routers will watch the LAN traffic for conflicts.
eg. you should assign a static address in the range 198.168.1.201 to 198.168.1.254

---

### Post by Austin_KW on 2007-04-27
That is mainly a change to how you use dynamic dhcp addresses. 
In this case you register you pc's name with the router so that on your network you can use the name. If you do this then it does not matter if the address changes as it the name will be resolved to the new address.

---

### Post by dannyboy79 on 2007-04-27
Ok, you're still not understanding what you need to do or how this works. As I have explained, you have an external ip address which is what is shown on the internet if some1 were going to try to access your router. If your router had built in capabilities to be a web server than that's the ip address (62.86.......) you would use to access it IF you didn't setup a hostname with dyndns or no-ip.com (your router is on the wan, wide area network, it gets it's IP address from the dhcp server that Orange has. i am under the impression that orange is your isp, internet service provider).

NOW, you have computers within your local are network (referred to as the lan) which get INTERNAL ip addresses from your dhcp server (this is your orange livebox) It's also a router and a firewall I imagine. You informed me that there was a location within your router that showed you that attached devices, within that area is there anything that allows you to "marry" or "reserve" the ip address that ubuntu is getting (192.168.1.198)????? You can't set your External IP address to be static because that's provided to your from Orange. Also, you CAN change the MAC address of your Orange Livebox but you don't need to. There are reasons to change it but I forget why. You could make the router have the MAC address of your internal computer hooked to it (or even make it whatever you want I think) which then would allow you to see that MAC address from the outside world (internet) but I don't see a good reason for you to change the MAC address of your Orange Livebox unless some1 else chimes in to help and explain why you should. 

So again, please let me know if you can within your Orange Livebox, tell it to always provide ip address 192.168.1.198 to your ubuntu machine???

If not, I will then help you setup ubuntu with a static ip. As I said before, you may need to find out your ISP's dns servers so that you can add them within your interfaces file or within your resolv.conf as sometimes consumer routers don't properly forward dns requests as I tried pointing out earlier. good luck

---

### Post by dannyboy79 on 2007-04-27
alright, I see that others are providing you the help you need. The amount of information and expaining that is required here, I am just going to let these other users help you as it appears that your getting the help you need.

I will however point out that your home router (orange livebox) may or may not work if you put that within the system, admin, networking dialog box under dns. If it doesn't work by merely putting in 192.168.1.1, then you'll need to find out your isp's dns servers or use the free ones from this guide.  

[http://www.opendns.com/start/](http://www.opendns.com/start/)

---

### Post by undesign on 2007-04-27
> So again, please let me know if you can within your Orange Livebox, tell it to always provide ip address 192.168.1.198 to your ubuntu machine???


Thanks for your reply,

I cannot find any information anywhere either on the admin pages, forums, Orange themselves, that states that your internal IP address doesn't change so the answer to your question has to be no.

---

### Post by dannyboy79 on 2007-04-27
ok, then just use my previous tips about dns and go into system, admin, networking and change your interface (normally eth0) from dhcp so that it is static and fill in the info. 

IP=192.168.1.8
Netmask=255.255.255.0
Gateway=192.168.1.1

I can't remember what else there is to set here but don't forget to click on the dns tab and fill that out also. for this just follow my previous post about the "gotchas" of home routers.

OR 

just do what austin_kw wants you to try:

Why bother with static ip. Just use dhcp & the dns on your router , it is much simpler.

You can instruct you machine's dhcp client to register its name with the dns masquerade on your home router. Then you can address your PC's by name on your home network.

Use your favourite editor to change the file /etc/dhcp3/dhclient.conf (gksudo gedit /etc/dhcp3/dhclient.conf)and add a line to register yourPcName
Add send host-name "yourPcName"

then rerun dhcp clinet to register the address
sudo dhclient eth0

another PC on the network can then address your pc by nane
eg [http://yourPcName/](http://yourPcName/)
or [http://yourPcName.yourDefaultDomain/](http://yourPcName.yourDefaultDomain/) probably [http://yourPcName.home/](http://yourPcName.home/) 


BUT I can 't speak for that since I have never done that. let us know if you get austin_kw's suggestion to work. if you do, you wouldn't have to set ubuntu with a static ip and you could just acces your XAMPP server using your hostname as he suggests.

---

### Post by undesign on 2007-04-28
Thanks for the help guys,

Just as I started to look at setting it up Orange broadband went down. Typical.

I will come back to you soon and let you know if it worked.

Thanks

---

### Post by Austin_KW on 2007-04-28
You dont need broadband to use or configure the LAN side of your network

---

