---
title: "booting Network Configuration problem"
date: 2005-11-17
forum: Absolute Beginner Talk
---

### Post by chilebeans on 2005-11-17
1 While installing Ubuntu 5.04 on installation...it never detects my network configuration so it reads "failure"...so I manually input the information if that helps?

2 well I been trying to connect with my configurations and it doesnt work

3 My other PC is Windows XP and I have no problem with connection? please help me and realize im a retard with Linux...but I want to convert to Ubuntu becuase im sick of windows and their scams...

thanks for this website...someone just handed me this Ubuntu cd.....I really want to make this work...please help me...thanks

---

### Post by matthewv on 2005-11-17
So you have a network..???
If so, do you run dhcp??

---

### Post by Lambert on 2005-11-17
is it wired or wireless?

---

### Post by chilebeans on 2005-11-17
[QUOTE=matthewv]So you have a network..???
If so, do you run dhcp??[/QUOTE]


1 Well....one modem and two computers connected to it if this answers your question?

2 What I find weird is when I boot the computer it doesnot detect my connection in the network configuration automatically.

3 so I have been trying to plug in my IP infor..Sub net mask...Gateway info but this does not connect me to the internet. Do you have any suggestions? 

note: I been reading the online info typing in the commands and I don't know if I am doing it wrong or why I can not connect. Windows XP is so easy in this regard but I really want to leave windows.

this forum is great I must say

thanks

---

### Post by tokyovigilante on 2005-11-18
Hi chilebeans,

Yes you have a network :) congrats. Networking can be tough to set up even in windows. 

A few questions about your setup:

1. Is the computer connected to the internet the one you're keeping XP on or the one you're installing Ubuntu on, or do you use a combination modem/router?

2. What kind of net connection (i.e. Cable, ADSL, dial-up etc) do you have?

3. If you're using an internal modem on your XP machine, do you have internet connection sharing (under Network Connections) for your ethernet connection (I'm guessing your network is based on ethernet RJ-45 cables) enabled? This will force XP to act as a DHCP server for your network, and assign itself the IP address 192.168.0.1.

4. Does Ubuntu detect your network interface (i.e. card)?

5. Can you connect locally to the other machine(s) on your network?

As an aside, DHCP (or Dynamic Host Configuration Protocol) is a service that runs on your network to automagically give other computers on the same network information about the network and assign addresses. When you install Ubuntu, it should be fetching an address from your XP machine using DHCP. Since this doesn't work for you then this suggests that DHCP is not running on your network. If you enter the info manually, and you're using XP connection sharing (which forces you to use the 192.168.0.x subnet) then use the IP 192.168.0.10 for your Ubuntu box (assuming a printer or other computer isn't already), a subnet mask of 255.255.255.0, and a gateway of 192.168.0.1, i.e. your XP machine.

On the other hand, if both your computers plug into an external modem/router, this would suggest DHCP is not set up on your router, and you'd need to look into the manual for help with that.

On the other other hand, if you're trying to use your Ubuntu box as an internet server (which is an awesome idea as you get a really secure home network), then you need two network interfaces, one to connect to the internet via your ADSL/dialup/cable connection, and another ethernet or wireless interface to connect to the rest of your home network, and to bridge  them. The easiest way I've found to do that is to use Firestarter (enable Universe repositories in Synaptic then search for firestarter, or sudo apt-get install firestarter in a terminal. You'll probably want to install dhcp3-server (sudo apt-get install dhcp3-server) so that other computers can pick up their own IPs.

If that all seems too complex (it almost was when I was trying to get mine running) post a few details about your setup and what you're going for, and I'll see if I can be any more help.

Good luck!

---

### Post by chilebeans on 2005-11-18
Hi chilebeans,

Thanks for everything and I will try everything you said. I did a Q & A thing to make it easier for you to read........thanks again

1. Q 1. Is the computer connected to the internet the one you're keeping XP on or the one you're installing Ubuntu on, or do you use a combination modem/router?

A I use an external modem that is connected to a hub/router where two Lan lines go to each computer. My laptop is XP and the Desktop is Ubuntu.

Note: My desktop before was fine connecting to the internet through XP. So the connection was never a problem with the Desktop. I think its just my ignorance of this awesome anti-window program :eek: I am sick of windows!!

2. Q What kind of net connection (i.e. Cable, ADSL, dial-up etc) do you have?

A Its a cable broadband connection called " Enteladsl "

Note: I also live in Chile right now if this makes a difference

3. 
Q If you're using an internal modem on your XP machine, do you have internet connection sharing (under Network Connections) for your ethernet connection (I'm guessing your network is based on ethernet RJ-45 cables) enabled? This will force XP to act as a DHCP server for your network, and assign itself the IP address 192.168.0.1.

A I am using an external modem but my laptop does have an internal modem I believe

Yes, I have an internet connection under network connection..... but I guess its for my ethernet connection....yes I am using an RJ-45 cable

So I guess my XP is acting as the DHCP?

Note: I notice two icons under network connections. One is a Local area one( Local area connection Internet Protocal TCP/IP) and the other is Enteladsl ( my service internet sevice icon). The Enteladsl has a Server IP number and Client IP number. The Local area one has an Ip address, subnet mask, and physical address.  What I find weird is none of these match my IP address on the PC. 

4. Q Does Ubuntu detect your network interface (i.e. card)?

A  In the installation of Ubuntu the only error I get is the Network Configuration. The rest seems to load up fine. So I believe the network interface is detected. I will check though or try and check to see if it does.

5. Q Can you connect locally to the other machine(s) on your network?

A The laptop connects fine to the internet. So yes the other machine connects locally. I am thinking connecting to the internet when you say locally. I do not see my Desktop from my laptop PC if this is what you meant?



As an aside, DHCP (or Dynamic Host Configuration Protocol) is a service that runs on your network to automagically give other computers on the same network information about the network and assign addresses. When you install Ubuntu, it should be fetching an address from your XP machine using DHCP. Since this doesn't work for you then this suggests that DHCP is not running on your network. If you enter the info manually, and you're using XP connection sharing (which forces you to use the 192.168.0.x subnet) then use the IP 192.168.0.10 for your Ubuntu box (assuming a printer or other computer isn't already), a subnet mask of 255.255.255.0, and a gateway of 192.168.0.1, i.e. your XP machine.

A Ok I am getting it more now on what your talking about. I change the Desktop(Ubuntu) to static ip and punched numbers in but I get nothing. But no my Desktop does not detect the DHCP on the Laptop.

How do I make the XP use connection sharing?

So in your example your saying make my IP address on the Desktop a differenct number at the end of my IP address..... from the Subnet mask on my laptop? this will give my Desktop the proper IP address ? Use that exact subnet mask? and for the gateway again just change the last number at the end from the IP address? Im I understanding you correctly?

On the other hand, if both your computers plug into an external modem/router, this would suggest DHCP is not set up on your router, and you'd need to look into the manual for help with that.

A  Hopefull I can avoid this becuase I don't have the manual and its probably in Spanish which I am not fluent in yet.  :rolleyes:  

On the other other hand, if you're trying to use your Ubuntu box as an internet server (which is an awesome idea as you get a really secure home network), then you need two network interfaces, one to connect to the internet via your ADSL/dialup/cable connection, and another ethernet or wireless interface to connect to the rest of your home network, and to bridge them. The easiest way I've found to do that is to use Firestarter (enable Universe repositories in Synaptic then search for firestarter, or sudo apt-get install firestarter in a terminal. You'll probably want to install dhcp3-server (sudo apt-get install dhcp3-server) so that other computers can pick up their own IPs.

A I will try this but I think for now I should just try and get the Desktop to connect. . My laptop has an ethnet card so all I need is to do what you said. I just need to switch the lan lines in the modem i think...to make my Desktop the server. I have never bridge the computers together though I should. Maybe this is where my ignorance lies in this problem I have. One I decide to make it the server I will try the firestarter on Ubuntu...I am so new to this program...I have not even really explored it.;;; do I install dhcp3-server in the synaptic package? I so want to get good with Ubuntu...sounds like all I need is a command sheet... Thats what I use to used in the military because we had to use Cisco.


If that all seems too complex (it almost was when I was trying to get mine running) post a few details about your setup and what you're going for, and I'll see if I can be any more help.

A  thank so much, I don't know how to thank you. I think I will catch on becuase I have a basic foundal way of thinking with computers. I mean, I can listen and do things in other words...lol....so Im slow just above retarded when It comes to all this PC stuff lol

Good luck!

AMD Athlon64 3800+ X2 Dual Core / ASUS A8N-SLI / Sparkle GeForce 7800GT 256MB /GeIL Ultra 1GB DDR400 SDRAM / LG-4167B DVD+/-RW-DL / Maxtor 200GB 7200RPM PATA / Excel 350W PSU
Kubuntu 6.10 AMD64 Dapper Drake development version with KDE 3.5 RC1
Last edited by tokyovigilante : 14 Hours Ago at 02:40 AM. 


Thanks allot again ...thanks.....I will try to apply everything you said now..and I will let you know what happens..thanks

---

### Post by tokyovigilante on 2005-11-18
Hi again,

I'll run through your queries and then try and clarify a few things and see where to next.

> I use an external modem that is connected to a hub/router where two Lan lines go to each computer. My laptop is XP and the Desktop is Ubuntu.
That's a good setup and we should be able to get you going. What brand and model modem and router are you using?

> Note: My desktop before was fine connecting to the internet through XP. So the connection was never a problem with the Desktop. I think its just my ignorance of this awesome anti-window program I am sick of windows!!
That's promising, just sounds like everything needs to be configured. You're right, Linux is an awesome OS, but it does have a fairly steep learning curve, you've done well to get this far and only hit one snafu :) 

> Its a cable broadband connection called " Enteladsl "
Note: I also live in Chile right now if this makes a difference

Shouldn't do, as long as there's internet somewhere, Ubuntu should be able to use it.

> So I guess my XP is acting as the DHCP?
 From what you've said it looks like either your router or external modem is acting as a DHCP server.

> Note: I notice two icons under network connections. One is a Local area one( Local area connection Internet Protocal TCP/IP) and the other is Enteladsl ( my service internet sevice icon). The Enteladsl has a Server IP number and Client IP number. The Local area one has an Ip address, subnet mask, and physical address. What I find weird is none of these match my IP address on the PC.
That's normal, as I'll explain below, each connection needs a separate address, so your network needs an external address to be seen on the internet, then each connected computer needs one of its own to recieve packets it has requested.

> In the installation of Ubuntu the only error I get is the Network Configuration. The rest seems to load up fine. So I believe the network interface is detected. I will check though or try and check to see if it does.If its letting you enter details manually it should have detected your physical hardware correctly, which makes things much easier :)

> The laptop connects fine to the internet. So yes the other machine connects locally. I am thinking connecting to the internet when you say locally. I do not see my Desktop from my laptop PC if this is what you meant?
No connecting to the internet and connecting locally are different. Its a bit complicated and I'll try to explain below. Local means that your desktop and laptop can communicate to share files and printers etc. compared to accessing the external internet, but for now we'll just try to get you online.

> Ok I am getting it more now on what your talking about. I change the Desktop(Ubuntu) to static ip and punched numbers in but I get nothing. But no my Desktop does not detect the DHCP on the Laptop.
We'll try and work out what numbers you need (or if you even need them) below

> How do I make the XP use connection sharing?
With your setup you shouldn't need to, but the option is under Advanced in your Local Area Connection preferences.

> So in your example your saying make my IP address on the Desktop a differenct number at the end of my IP address..... from the Subnet mask on my laptop? this will give my Desktop the proper IP address ? Use that exact subnet mask? and for the gateway again just change the last number at the end from the IP address? Im I understanding you correctly? Just about. Each computer needs a different and unique IP, the subnet mask is specific for your network and remains the same on your computer, and the gateway is the IP address of the internet-connected device (which should be your modem). I'll try and explain IP networking in a nutshell below, which you can ignore if you want, but I find it fascinating, and hopefully you'll be better able to understand what's going on.

> On the other hand, if both your computers plug into an external modem/router, this would suggest DHCP is not set up on your router, and you'd need to look into the manual for help with that.

A Hopefull I can avoid this becuase I don't have the manual and its probably in Spanish which I am not fluent in yet. OK, hopefully we can get things going without fiddling with your modem or router. I'm sure your spanish is better than mine regardless ;)

> A I will try this but I think for now I should just try and get the Desktop to connect. .
You're probably right, setting up a Ubuntu server is (not much) more complicated, but I guess you just want to be online at the moment.

My laptop has an ethnet card so all I need is to do what you said. I just need to switch the lan lines in the modem i think...to make my Desktop the server. I have never bridge the computers together though I should. Maybe this is where my ignorance lies in this problem I have. One I decide to make it the server I will try the firestarter on Ubuntu...I am so new to this program...I have not even really explored it.;;; do I install dhcp3-server in the synaptic package? I so want to get good with Ubuntu...sounds like all I need is a command sheet... Thats what I use to used in the military because we had to use Cisco.
If you were going to set up a server, you would need two ethernet cards in your desktop, one to connect your modem, and the other to connect to your local network. Then Firestarter would automatically bridge the connections (i.e. send internet packets from the external (internet) network to your internal network, and dhcp3-server would provide IPs automagically. Thats probably a project for another day though ;)


As promised, the next step(s)...

The first thing we need to do is make sure a DHCP server is running somewhere on your network. Have a look at the network connections on your laptop, find the Local Area Connection, and open the Status page, and post the results. (It will either say Static IP or Dynamically assigned, i.e. DHCP). The DHCP server will most likely be running directly on your cable modem or on the router.

Depending on the result you get, we can work out if DHCP should work on your desktop, or what IP and subnet you need. 

**IP networking in a nutshell**

There are better explanations on the internet, but (semi)briefly: 

When the internet was created, it was realised that each connected computer needed an individual address so packets of information would be able to arrive at their destination. Not anticipating the eventual size of the internet, a scheme was created using 4 16-bit integers, i.e. from 0.0.0.0 to 255.255.255.255. This gives 256^4 possible addresses, or about 4.2 billion, allowing 4.2 billion computers to connect at once. You'd think that would be enough, but with every office, home and school having multiple computers, we're getting through them.

To solve this problem, local IP networks were created. The logic was that through IP masquerading or NAT (network address translation) many computers could pretend to be a single one for the purpose of internet connection. 

Each computer was assigned an internal IP address from the agreed private address ranges (192.168.x.x, 10.x.x.x etc). When a local computer (192.168.0.5 for example) wanted to access the internet, they would send a request to the *network gateway* for their network (which generally would have a 192.168.0.1 address (to keep things simple). 

The gateway would have another external or *public* address e.g. 60.34.78.252, and would *translate* the packet so that it appeared to originate from the gateway. When the gateway recieved a reply, it would translate the public address back to a private one (192.168.0.5) and route the packet correctly. In this way a single gateway can hide any number of PCs. Two PCs in different networks can have the same IP address without confusion because gateways perform NAT for them. 

The subnet mask facilitates this by indicating what range your local network can use. An internal network with an address range of 192.168.0.1 to 192.168.0.255 would have a mask of 255.255.255.0, with the value 255 representing your network (192.168.0.x) and the 0 representing 256 possible values for a maximum of 256 computers on this network. (In practice 254 as 192.168.0.1 is the gateway and 192.168.0.255 is a special address called the *broadcast address*). A larger network with the range 192.168.0.1 to 192.168.255.255 would have the subnet mask 255.255.0.0.

Computers can only see others with the same subnet mask, which is why it must remain constant across your network.

Whew! Hope that all makes sense. If you want to know more, then Wikipedia is a good place to start. The Linux Documentation Project ([http://www.tldp.org]("http://www.tldp.org") also has some good Networking How-tos, but they get pretty complicated pretty quick.

In your setup, your modem should be acting as a gateway, in which case it will have the external IP, and will also have an internal IP and run a DHCP server which allocates your network internal IPs and performs NAT.

OK have a work through all that and let me know how you go. Alternatively just post the addresses your laptop has and we'll go from there.

Ryan

---

### Post by chilebeans on 2005-11-20
Hi Tokyovigilante

thanks for all your help again....

Q
That's a good setup and we should be able to get you going. What brand and model modem and router are you using?
A 
Modem 
Brand : TRENDnet
Model Number: TDM-E300plus ……ADSL Modem 
Router
Brand: Encore
Model: ENH908-NWY

Q
That's promising, just sounds like everything needs to be configured. You're right, Linux is an awesome OS, but it does have a fairly steep learning curve, you've done well to get this far and only hit one snafu  
A
I really need to start reading about this. What websites do you know of that are geared towards learning Linux?

Q 
From what you've said it looks like either your router or external modem is acting as a DHCP server.
A
That explains every time I rebooted my computer with XP I never had to program anything, it was automatic. Does this make sense or am I confusing this with something else?
Q
That's normal, as I'll explain below, each connection needs a separate address, so your network needs an external address to be seen on the internet, then each connected computer needs one of its own to recieve packets it has requested.
A
Not clear but I will keep that in mind…external address needed. I will read below though as you said. I am not sure what you mean by receiving packets?
Q
No connecting to the internet and connecting locally are different. Its a bit complicated and I'll try to explain below. Local means that your desktop and laptop can communicate to share files and printers etc. compared to accessing the external internet, but for now we'll just try to get you online.
A
Great….I understand what you mean by locally since the military had to use local internet addresses. So I think I know what you mean.
Q
Just about. Each computer needs a different and unique IP, the subnet mask is specific for your network and remains the same on your computer, and the gateway is the IP address of the internet-connected device (which should be your modem). I'll try and explain IP networking in a nutshell below, which you can ignore if you want, but I find it fascinating, and hopefully you'll be better able to understand what's going on.
A
Yes,…I will definitely read it so I can understand this stuff. Knowing the whole or some of the story always helps especially so I can have a mental picture of what is going on.
Q
You're probably right, setting up a Ubuntu server is (not much) more complicated, but I guess you just want to be online at the moment.

A
Yes, for my wife’s father since I gave him my PC to go on the internet. My wife brought this program (Ubuntu) to me because some guy gave it to her. Well, I was totally interested because I want to leave XP. If I get the PC online I will put the LAPTOP on Ubuntu too. The thing is with my laptop is it sounds like its working to hard with the UBuntu program. I meet the requirements…but it sounds like my Laptop is going to explode. Maybe I should remove programs on it or something? The fan seems to work hard and the noise it makes when I click on other programs worries me. I have an emachine M305. if that matters.
Q
The first thing we need to do is make sure a DHCP server is running somewhere on your network. Have a look at the network connections on your laptop, find the Local Area Connection, and open the Status page, and post the results. (It will either say Static IP or Dynamically assigned, i.e. DHCP). The DHCP server will most likely be running directly on your cable modem or on the router.

A
Let me tell you what I did to make sure I did this right. 
Clicked on status page on local area connection but saw nothing for DHCP or Static IP….so I clicked on the properties to get Local Area Connection properties…….than I clicked on “internet protocol” than properties of internet protocal……than clicked advance under internet protocol properties and under TCP/IP settings it said….>DHCP enabled. 
Also, under status tab I clicked on the support tab and it said “automatic private address” 
With a IP, Subnet mask, Gateway…..
than under the details of that tab it gave my a physical address, IP address, and subnet mask
Back to the status page all I under connection all I saw was status(connected), Duration( the time connected), and the Speed( 100mbps)
Under Activity I saw packets….sent and receive.
Is this what you wanted?
I wanted to know if I give you all my IP information and stuff does that make me vulnerable to hackers who may be viewing what I am writing in this forum?
Q
IP networking in a nutshell

There are better explanations on the internet, but (semi)briefly: 

When the internet was created, it was realised that each connected computer needed an individual address so packets of information would be able to arrive at their destination. Not anticipating the eventual size of the internet, a scheme was created using 4 16-bit integers, i.e. from 0.0.0.0 to 255.255.255.255. This gives 256^4 possible addresses, or about 4.2 billion, allowing 4.2 billion computers to connect at once. You'd think that would be enough, but with every office, home and school having multiple computers, we're getting through them.

A

Yes I notice IP addresses only have that 4 combo number but I did not realize the highest was only 255 for each one. This is where the problem lied I guess. This is the network IP address right? That you are explaining about?

Q

To solve this problem, local IP networks were created. The logic was that through IP masquerading or NAT (network address translation) many computers could pretend to be a single one for the purpose of internet connection. 

A

If many computers pretend to be a single local IP network how do pc’s differ when receiving information?

Q

That is interesting, so the IP network are numbers 

Each computer was assigned an internal IP address from the agreed private address ranges (192.168.x.x, 10.x.x.x etc). When a local computer (192.168.0.5 for example) wanted to access the internet, they would send a request to the network gateway for their network (which generally would have a 192.168.0.1 address (to keep things simple). 

A

I see so an IP network acts as a number for the local computer IP which should be different numbers.  Is the IP network the gateway number? If not what is it? And what exactly is the computer IP number, is it the physical IP address? If not what is it? 

I think the IP network is the gateway number and sounds self explanatory….you got to the gate (gateway) to request information from the outside world.

Q

The gateway would have another external or public address e.g. 60.34.78.252, and would translate the packet so that it appeared to originate from the gateway. When the gateway recieved a reply, it would translate the public address back to a private one (192.168.0.5) and route the packet correctly. In this way a single gateway can hide any number of PCs. Two PCs in different networks can have the same IP address without confusion because gateways perform NAT for them. 

A 

My understanding must be off because when you explained two PC’s can have the same IP address I was confused. Can you explain this? My guess is that from the Gateway it can send information equally to both PC’s? like one river with that splits in two at the end?

The external or public address…is that a place physically somewhere else 60.34.78.252? 

Is the external address receiving all the internet info from the internet and than being sent to the gateway?

What is the purpose of having the external address act like the gateway…it seems unnecessary? Why the extra work unless its for a security reason I guess?

Q

The subnet mask facilitates this by indicating what range your local network can use. An internal network with an address range of 192.168.0.1 to 192.168.0.255 would have a mask of 255.255.255.0, with the value 255 representing your network (192.168.0.x) and the 0 representing 256 possible values for a maximum of 256 computers on this network. (In practice 254 as 192.168.0.1 is the gateway and 192.168.0.255 is a special address called the broadcast address). A larger network with the range 192.168.0.1 to 192.168.255.255 would have the subnet mask 255.255.0.0.

A

So when I look at the Subnet mask’s last number ( 255.255.255.this one) I should know it will go to 255? So all subnetmask numbers let you know how many computers I could use in the range from the last number to the number 255?

Q

Computers can only see others with the same subnet mask, which is why it must remain constant across your network.

A

So subnets stay the same but they let you know how many PC’s can be put on the network?

Q


Whew! Hope that all makes sense. If you want to know more, then Wikipedia is a good place to start. The Linux Documentation Project ([http://www.tldp.org](http://www.tldp.org) also has some good Networking How-tos, but they get pretty complicated pretty quick.

In your setup, your modem should be acting as a gateway, in which case it will have the external IP, and will also have an internal IP and run a DHCP server which allocates your network internal IPs and performs NAT.

OK have a work through all that and let me know how you go. Alternatively just post the addresses your laptop has and we'll go from there.

A

Thanks allot…I re-read this and it makes more sense now that I read it over…I will keep reading it…I did not want to change my questions because I still think they would help me understand. I think I really understand the relationship between the gateway and local PC…..thanks allot….I will read those links like advised….thanks very much for your time…this is a free educations…thanks again and I am very lucky to have your support..thanks


Ryan

---

### Post by tokyovigilante on 2005-11-21
Hi again,

I'll run through and answer your questions and clarify where I was confusing before.

> Modem
Brand : TRENDnet
Model Number: TDM-E300plus ……ADSL Modem
Router
Brand: Encore
Model: ENH908-NWY

OK the Encore seems to be a standard 8-port hub, so if a DHCP server is running anywhere it will be on your modem. The TRENDnet site is down which seems a little ominous but at least you have the manual (i hope!).

> That explains every time I rebooted my computer with XP I never had to program anything, it was automatic. Does this make sense or am I confusing this with something else?

You're right, if DHCP is working then you shouldn't have to worry about configuring anything.

> I am not sure what you mean by receiving packets?

Whenever you download or upload information on the internet, it is broken down into smaller standard-sized chunks called *packets*.

> The fan seems to work hard and the noise it makes when I click on other programs worries me. I have an emachine M305. if that matters.

Sounds like you need to setup power management on your laptop, try [Linux on Laptops]("http://www.linux-laptop.net/") or [TuxMobil]("http://tuxmobil.org/"). I don't have any experience with that laptop.
> 
DHCP enabled.
Also, under status tab I clicked on the support tab and it said “automatic private address”
With a IP, Subnet mask, Gateway…..

That's bad. That means that DHCP on your laptop is looking for an IP address from a DHCP server, but is unable to find one and so is resorting to giving itself an "automatic private address." Does the internet work on your laptop while this is going on? I'd expect that it wouldn't. If it does you may have chosen the wrong network interface. Make sure you're selecting the same connection in Network Connections that the cable is physically plugged into. If  that fails try the same process on your desktop while XP is running and post the result.

 (Each interface has it's own IP address. All the computers on your local network have an internal address. The modem is different as it has two interfaces, an internal ethernet one which connects to your local network via the hub, and an external public interface (your cable connection) which connects you to the internet and has the external IP address. Two interfaces = 2 IPs, an internal and external one, so the modem needs to perform NAT (network address translation) to bridge these interfaces. This is where the security comes from, as the external internet never sees these internal addresses, and so hackers are denied access to your internal machines. Have a look at the attached image, and hopefully you'll have a clearer understanding. Both computers have the internal IP 10.1.1.6, but they're hidden by the two gateways and NAT.)

[IMG]http://www.infosecwriters.com/text_resources/whatfirewall/image001.jpg[/IMG]

> I wanted to know if I give you all my IP information and stuff does that make me vulnerable to hackers who may be viewing what I am writing in this forum?

No, hopefully I've clearly set out above how your internal network is hidden from the external internet through NAT. So as long as you only post your internal details then you're safe. It will most likely be in the form 10.x.x.x or 192.168.x.x, which are designated private addresses. You are perfectly safe posting these. I need to know what IP address your desktop/laptop has, the subnet mask, and the gateway. That way we can work out if DHCP is working, and if not then we'll be able to work out what values you need to install Ubuntu with.

Other things:

> If many computers pretend to be a single local IP network how do pc’s differ when receiving information?

Because the gateway knows which computers on the local network have requested what information from where, and routes it appropriately.
> 
I see so an IP network acts as a number for the local computer IP which should be different numbers. Is the IP network the gateway number? If not what is it? And what exactly is the computer IP number, is it the physical IP address? If not what is it?

Kind of. A IP network is just connected computers, which all need unique IP addresses. To use an analogy, a postal network (IP network) requires all the houses it can deliver to to have individual street addresses (IP addresses). However two houses in different suburbs (subnets) can have the same postal (IP) address, e.g. 123 Linux Street in the Ubuntu suburb is a different address to 123 Linux Street in the Suse or Gentoo suburb. In this example, the gateway computer is equivalent to a local suburbian post office, and routes the mail (IP packets) depending on their street address (internal/local IP).
> 
I think the IP network is the gateway number and sounds self explanatory….you got to the gate (gateway) to request information from the outside world. 

You're right, you access the outside world (internet) via the gateway. I should have clarified, when i say gateway I (and most other things) are referring to the internal IP address of the computer (or modem in your case) acting as the gateway, and by convention is almost always 192.168.0.1 or 10.1.1.1.

> My understanding must be off because when you explained two PC’s can have the same IP address I was confused. Can you explain this? My guess is that from the Gateway it can send information equally to both PC’s? like one river with that splits in two at the end?

Hopefully this is clear from the diagram above.

> The external or public address…is that a place physically somewhere else 60.x.x.252?  
Yes, in a way. Its a way of tying a virtual location on the internet (for example [www.google.com](www.google.com)) to their physical server, whereever that is.

> Is the external address receiving all the internet info from the internet and than being sent to the gateway?

Yes, it collects requests for information from your network, then sends it through your gateway's external interface to the internet, then recieves replies and distributes them to the appropriate computers on your network.

> So subnets stay the same but they let you know how many PC’s can be put on the network?

Yes, a 255.255.255.0 subnet allows 256 computers (256^1), 255.255.0.0 allows 256^2, 255.0.0.0 allows 256^3. (0.0.0.0 isn't allowed, but I don't think ou'd want that may computers on your network ;). 255.255.255.255 is the "subnet" for the public internet. (If an IP is associated with this subnet don't oost it ;). Anything else is safe.

> What is the purpose of having the external address act like the gateway…it seems unnecessary? Why the extra work unless its for a security reason I guess?

Both security (as your internal computers are unknown to the external network) and so that multiple computers can share an IP. As I mentioned in a previous post, even though there are 4.2 billion possible IPs, we're running out. (In a few years, the internet will switch to IPv6 (version 6, we're running IPv4 at the moment). From Wikipedia - > IPv6 is intended to address the concern of IPv4 address exhaustion. There are too few IP addresses available for the future demand of device connectivity (especially cell phones and mobile devices). IPv4 supports 4.2 billion (2564 &#8776; 4.294 × 109) addresses, which is inadequate for giving even one address to every living person, much less support the burgeoning market for connective devices. IPv6 addresses this problem by supporting 340 undecillion (655368 &#8776; 3.4 × 1038) addresses. For scale, this would allow an average of about 430 quintillion (4.3 × 1020) unique addresses per square inch, or 670 quadrillion (6.7 × 1017) per square millimeter, of the Earth's surface. In other terms, assuming a population of about 6.5 billion humans, there are enough IPv6 addresses such that every atom of every person on Earth could be assigned 7 unique addresses with enough to spare (assuming 7 × 1027 atoms per human).

That hopefully will be enough ;) In the meantime we're stuck with gateways and NAT though.

OK, if you're still awake after all that, post up those internal addresses, making sure you're able to browse the internet from the computer whose address you're posting, and we'll go from there.

If you want to learn more about this stuff, try Wikipedia's articles on [IP networking]("http://en.wikipedia.org/wiki/IPv4") and [NAT]("http://en.wikipedia.org/wiki/Network_Address_Translation").

For basic guides, there's [Tux magazine]("http://www.tuxmagazine.com"), and try the [TLDP Introduction to Linux]("http://www.tldp.org/LDP/intro-linux/html/index.html") for an indepth intro to linux. Google is a great search engine if you're looking for something specific. Searching the Ubuntu forums is another good place to start. There's a good chance at least one other person has run into the same problem as you and posted about it.

Hope this is all starting to make sense and you can begin to see what you need to get everything running. Hang in there, its well worth it!

Ryan

---

### Post by chilebeans on 2005-11-21
hi Tokyovigilante

thanks again....I will reread what you sent...I realize allot of your post was explanation for learning....I will try and learn everything your talking about..here are my reply's


Q

OK the Encore seems to be a standard 8-port hub, so if a DHCP server is running anywhere it will be on your modem. The TRENDnet site is down which seems a little ominous but at least you have the manual (i hope!).

A
No manual came with this modem. Things are different here in Chile and the modem is with the service and no modem as I can recall. I will look and ask my wife though.
Q
You're right, if DHCP is working then you shouldn't have to worry about configuring anything.
A
You know, that is why I thought it was weird when I had to try and configure Ubuntu…because I was so use to the PC detecting the DHCP.
Q
Sounds like you need to setup power management on your laptop, try Linux on Laptops or TuxMobil. I don't have any experience with that laptop.

A
Can I get Linux for laptops or TuxMobil for free? I am optimistic about using linux thanks to all the support I have found here at Ubuntu. I find it fun like a hobby discovering how things work on the computer and using new programs. If I learn this stuff I will help others out too if I can. Maybe I will teach you someday…just kidding.
Q
That's bad. That means that DHCP on your laptop is looking for an IP address from a DHCP server, but is unable to find one and so is resorting to giving itself an "automatic private address." Does the internet work on your laptop while this is going on? I'd expect that it wouldn't. If it does you may have chosen the wrong network interface. Make sure you're selecting the same connection in Network Connections that the cable is physically plugged into. If that fails try the same process on your desktop while XP is running and post the result.

A
Yes, the internet works. I been using the Laptop XP all this time…while the desktop Ubuntu is not connecting.
Since it works I must have chosen the wrong network interface. 
How do you select the same connection? Where on the Laptop does it show where the cable is physically plugged into? (Make sure you're selecting the same connection in Network Connections that the cable is physically plugged into)
I am confused on the steps since I don’t know the above question (If that fails try the same process on your desktop while XP is running and post the result).
Maybe I should just read this material a couple of times.

Q

Each interface has it's own IP address. All the computers on your local network have an internal address. The modem is different as it has two interfaces, an internal ethernet one which connects to your local network via the hub, and an external public interface (your cable connection) which connects you to the internet and has the external IP address. Two interfaces = 2 IPs, an internal and external one, so the modem needs to perform NAT (network address translation) to bridge these interfaces. This is where the security comes from, as the external internet never sees these internal addresses, and so hackers are denied access to your internal machines. Have a look at the attached image, and hopefully you'll have a clearer understanding. Both computers have the internal IP 10.1.1.6, but they're hidden by the two gateways and NAT.)
A
So network A and network B are the two IP’s that you are talking about?
Q
No, hopefully I've clearly set out above how your internal network is hidden from the external internet through NAT. So as long as you only post your internal details then you're safe. It will most likely be in the form 10.x.x.x or 192.168.x.x, which are designated private addresses. You are perfectly safe posting these. I need to know what IP address your desktop/laptop has, the subnet mask, and the gateway. That way we can work out if DHCP is working, and if not then we'll be able to work out what values you need to install Ubuntu with.
A
Ok, cool, I am not worried anyways because I don’t put or do anything on the PC anyway like some people do.
Click on “Status” Local Area Connection….Click on “Support” Tab…..Under Internet Protocol TCP/IP it reads…..IP address 169.254.184.243……Subnet Mask 255.255.0.0……Default Gateway   ( its blank)….
That is weird I cannot find my gateway? Or it is set as default
Note: I connected my Xbox before and I can give you those settings?  Not sure if this matters though?or if its safe?
Q

---

### Post by tokyovigilante on 2005-11-21
Yes try connecting your Xbox and posting those settings. Any computer you connect to your network will have an internal address and be safe.

Let me make sure we're both clear, you're able to browse the net with your laptop, but under Local Area Connection at the same time, you have an Automatic Private Address beginning with 169.254.x.x? Are there any other connections listed?

Also try running a command prompt on Windows (Start->Programs->Accessories->Command Prompt or similar) and type 
```
ipconfig /all
```
and post the results. 

Also post the results of typing these in a command prompt:
```
ping 192.168.0.1
ping 192.168.1.1
ping 10.1.1.1
```

You shouldn't worry about hackers too much in Linux, but in Windows your machine can be taken control of remotely, your screen watched, your online banking etc passwords can be stolen, and your machine used by others to attack computers in Denial of Service attacks. Bad!! 

TuxMobil and Linux on Laptops are links to sites where you can find more info about setting up a Linux laptop, not programs (although if they were programs they'd be free like almost all Linux software ;)

See how you go with the above...

---

### Post by chilebeans on 2005-11-22
Hi TokyoVigilante

I sent you the response in an email just to be safe because I don't know who reads these forums...maybe some hacker.

---

### Post by tokyovigilante on 2005-11-22
OK this is where it gets a bit tricky...

At the moment a DHCP server is not running on your network.

The reason that Windows PCs are able to connect in this situation without IPs is a dirty hack called **Automatic Private Addressing (APA)**. APA comes into action if an IP cannot be assigned addresses, and creates a random one in the range 169.254.x.x. This works for getting onto the internet, but breaks any computer running as a server on your network, and won't allow you to use P2P, VoIP, or most other net services excluding web and email.

There is definitely a way to get this working as this setup almost exactly mirrors my home net, i.e. an ADSL modem connected to a router powering the network. 

Before we go any further, you need to get in touch with your ISP, and find out if your modem supports a DHCP server, and if so, how to enable it. I haven't been able to find any info about it on the net so they're the best place to look. If your modem does then we'll set that up and you should be away, otherwise we might have to get your desktop to run as one.

BTW Does your desktop have one network card or two? Does your modem have ethernet only or USB as well?

You won't see any gateways anywhere because APA is incapable of setting one up.

---

### Post by chilebeans on 2005-11-22
OK this is where it gets a bit tricky...

Q

At the moment a DHCP server is not running on your network.

A

That is weird becuase there is a place I see that says its enabled but you know better


Q


The reason that Windows PCs are able to connect in this situation without IPs is a dirty hack called Automatic Private Addressing (APA). APA comes into action if an IP cannot be assigned addresses, and creates a random one in the range 169.254.x.x. This works for getting onto the internet, but breaks any computer running as a server on your network, and won't allow you to use P2P, VoIP, or most other net services excluding web and email.

A

So the only downfall is network sharing but I can still connect with both to the internet? 

Q

There is definitely a way to get this working as this setup almost exactly mirrors my home net, i.e. an ADSL modem connected to a router powering the network.

A

thats a relief

Q

Before we go any further, you need to get in touch with your ISP, and find out if your modem supports a DHCP server, and if so, how to enable it. I haven't been able to find any info about it on the net so they're the best place to look. If your modem does then we'll set that up and you should be away, otherwise we might have to get your desktop to run as one.

A

The problem is I can not talk to the ISP people because they all speak spanish.

What you mean as one?

Q

BTW Does your desktop have one network card or two? Does your modem have ethernet only or USB as well?

A

I am sure only one? I will check though and reply to this question

How do I see if my ethernet has USB or ehthernet only?

Q

You won't see any gateways anywhere because APA is incapable of setting one up.

A

You know my xbox connets...can't I just set all the PC's according to that? It connects no problem to the internet..

I am thinking of removing the Icon and reloading the connection to see if its in the options...maybe I can change this? and get the gateway incase I downloaded it wrong in the set-up wizard for the connection.

---

### Post by tokyovigilante on 2005-11-22
Hey again,

No a DHCP **server** is absent. All your computers are set to be DHCP **clients**, which is why they state DHCP is enabled.

In theory, you could give the Ubuntu box a 169.254 address, but it wouldn't be very efficient, secure or functional. This is where Windows excels, making things easy while throwing compatibility and security out the window.

Try an experiement for me? Boot your desktop into Windows, plug the modem directly into the computer via ethernet, open a web browser, and enter [http://192.168.1.1](http://192.168.1.1). Let me know what happens. If a page loads, please paste a screenshot.

The TrendNet site is back up but has absolutely no info about the TDM-E300 other than the fact that they sold them to Entel. You might have to start taking spanish lessons... ;)

---

### Post by tokyovigilante on 2005-11-22
OK we're all set, I've found a guide in Spanish I translated with Google, the link is:

[http://216.239.39.104/translate_c?hl=en&u=http://www.madboxpc.com/contenido.php%3Fid%3D161&prev=/search%3Fq%3DTDM-E300plus%2Btrendnet%26hl%3Den%26lr%3D%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26sa%3DG]("http://216.239.39.104/translate_c?hl=en&u=http://www.madboxpc.com/contenido.php%3Fid%3D161&prev=/search%3Fq%3DTDM-E300plus%2Btrendnet%26hl%3Den%26lr%3D%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26sa%3DG")

Basically you need to directly connect your modem and your desktop, open Internet Explorer and enter the URL [http://192.168.1.1](http://192.168.1.1).

It should show a screen asking you to enter your username and password, this should be DSL for both.

Once you've logged in, on the left of the screen, choose WAN->PPP, find the option for DHCP, and enable it. If you see an option to enter your ISP user name and password, enter that too.

Click Submit, then Choose ADMIN from the options. Click Save then Reboot.

This will take ~30s, after which time your DHCP server should be running. As before, check your IP address, it should now be something like 192.168.1.x, with a subnet of 255.255.255.0. If so, great! Check you can still access the inernet, and if so, plug the modem back into the router, and install Ubuntu. DHCP should work fine.

Let me know if you have any probs with the above :)

---

### Post by tokyovigilante on 2005-11-23
Hey again,

I emailed TrendNet yesterday and they've sent me the manual in English, have a read through. It confirms you can set up the modem to be a DHCP server and run your home network. Hopefully you should have everything you need now :)

---

### Post by chilebeans on 2005-11-23
Q

Basically you need to directly connect your modem and your desktop, open Internet Explorer and enter the URL [http://192.168.1.1](http://192.168.1.1).

A

Thanks so much....I been trying to open URL [http://192.168.1.1](http://192.168.1.1). in Internet and firefox but it does not open...I get a timed out? I will keep trying though

---

### Post by chilebeans on 2005-11-23
On my firefox browswer I get "operation timed out" when typing in the [http://192.168.1.1](http://192.168.1.1). in my address bar

For internet explorer, I get "no web page" when typing that in.

Is there another way to that website? or link?

thanks...i think were close :o

---

### Post by tokyovigilante on 2005-11-23
You might need to follow the instructions on page 4 of the guide: 
Manually configure your desktop to have IP 192.168.1.3, Subnet 255.255.255.0, then try and access the page.

---

### Post by chilebeans on 2005-11-23
Ok I will try that now..i see your online

---

### Post by tokyovigilante on 2005-11-23
Yeah I'll be at my desk at work for the next few hours, hopefully we can sort this out today!

---

### Post by chilebeans on 2005-11-23
Hi...

I manage to change the settings on my local area connection to the IP and subnet mask of page 4. So my local area connection says

IP 192.168.3.1

Sub 255.255.255.0

But ther default( enteladsl icon) connection is still differnct all the time with the Client and server IP changing

Server: 200.72.3.116

Client Ip 164.77.40.122

I will try and change this...and I will do that command ipconfig

---

### Post by tokyovigilante on 2005-11-23
I know, with your current setup your computer is dialling the modem for you. Setting the modem up as a DHCP server will make it do all the work for you, and you won't see this connection. Just ignore your external connection for now, and worry about the Local Area Connection.

---

### Post by chilebeans on 2005-11-23
Ok the Loacal Area connection has the following:

IP 192.168.3.1

Sub 255.255.255.0

Gatewat:  its blank


I need to see if the DHCP is enabled now


I just can not go to that webpage you gave me? the http// on page 4

---

### Post by tokyovigilante on 2005-11-23
No, 192.188.**1.3**, not 192.168.3.1

---

### Post by chilebeans on 2005-11-23
ok yes I did that

---

### Post by tokyovigilante on 2005-11-23
OK now try 192.168.1.1 and configuring your modem for DHCP. You may also need to enter your username and password in the appropriate sections. Don't forget to save your changes, then reboot the modem.

---

### Post by chilebeans on 2005-11-23
My service went down so I am back now..

I think you may think that I have made it to that webpage with the number on page 4. I did not make it there at all but I manage to change the IP number while I am connected directly to the modem.


Q

OK now try 192.168.1.1 and configuring your modem for DHCP. You may also need to enter your username and password in the appropriate sections. Don't forget to save your changes, then reboot the modem.

A

ok, so under Local Area connection use that number....I am not sure how I will configre the modem but I will try and see what I can do since I never made it to that webpage...


:confused:

---

### Post by tokyovigilante on 2005-11-23
Well I don't really know what to next, if you cant get into the configuration of the modem there's not much else I can help with.

I'll run through the setup again:

Modem - powered on, ethernet direct to your computer, doesn't need the cable connection plugged in, you're only setting up the internal network at the moment. (Is the modem new or 2nd hand? is there a chance someone else has changed the settings?)

Computer, powered on, running Windows, Local Area Connection set to Manual configuration, IP address 192.168.1.3, Subnet mask 255.255.255.0, No gateway.

Internet Explorer: address [http://192.168.1.1](http://192.168.1.1). You should see a page similar to that in the User Guide i sent. If the above doesn't work, try and run through the User Guide instructions step by step.

---

### Post by chilebeans on 2005-11-23
OK now try 192.168.1.1 and configuring your modem for DHCP. You may also need to enter your username and password in the appropriate sections. Don't forget to save your changes, then reboot the modem.

R ( reply)

Ok I put those settings and I can still connect but the modem for DHCP...I have no idea if it is or what.. I look for the DHCP enabled and instead it just shows the IP I put in(under TCP/IP settings). The funny things is I messed with the IP and found I could connect with the IP 192.168.100.1. So I am not sure if I am doing anything



I hope I did not mislead you into thinking I connected to that webpage you told me to connect too. I was never able to get to that webpage?

---

### Post by tokyovigilante on 2005-11-23
It's not a webpage, it's your modem's internal address, and should load the modem's configuration utility, which runs in Internet Explorer. 
Defining a manual address means a connection is forced regardless of whether it is valid or not. 192.168.1.x is the only range which will work. 

It must be 192.168.1.x. There cannot be any other values for the first 3 numbers, and the last number must be between 2 and 254.

---

### Post by chilebeans on 2005-11-24
Hi Tokyovigilante

I am here to start the new day. I will try and do what you said in the last post.

This is actually fun for me becuase I am learning and I am hooking up another PC instead of one I depend on. When I do hook that one up on Ubuntu I will try and change this desktop to Ubuntu. However, I should only worry about being able to run both on the internet. 

Thanks for your help and I will let you know how everything goes. 

thanks

---

### Post by tokyovigilante on 2005-11-24
OK, good luck getting everything sorted.

AFAICT, if you can access your modem and enable the DHCP server everything should work fine, and everything I've found online, including the user's guide, says you should be able to with the setup you have.

With that in mind, it might be your only choice if you can't access it yourself is to get someone who speaks English at your ISP, or at least someone knowledgeable about the ADSL service in your area to take a look at the moment, because the instructions I've found should work if everything is configured correctly.

Again good luck, let me know how you get on.

---

### Post by chilebeans on 2005-11-24
I was thinking...what if I directly connect the desktop(Ubuntu) computer to the modem , than reboot it, do you think it would detect my DHCP?

Than connect the desktop back to the hub, and than connect this lap top to the hub?

would this work? it might be easier I would think?

---

### Post by tokyovigilante on 2005-11-24
No that's my whole point, the DHCP server on your modem isn't running, and you need to enable it on your modem. We're just using the desktop as an interface to communicate with the modem. 

The only reason Windows can connect is that when it cannot find a DHCP server it makes up an address for itself. This works for the internet but will break your internal network if you are sharing files and folders, so it's not much use, and why Linux doesn't do it.

---

### Post by chilebeans on 2005-11-25
lets say I just directly connect my desktop ( ubuntu) to the modem. Can I connect than? or will I have to have windows XP?

---

### Post by chilebeans on 2005-11-25
Hey guess what?

I typed the command ipconfig /release.....than ipconfig /renew.....and now the Dhcp is enabled for the "roller"......but it is not enabled for the "PPP adapter"...?

am I getting closer or does this not matter?

---

### Post by chilebeans on 2005-11-25
Hi 

Ok now in my local area connection I was able to enable the DHCP...its says DHCP enabled...i accomplished this by the following:


For peer-topeer networks, be sure NetBIOS over TCP/IP is enabled: Start, Control Panel, Network and Dial-up Connection. Right-click Local Area Connection, Properties, Internet Protocol (TCP/IP), Properties, Advanced, WINS tab, Enable NetBIOS over TCP/IP, OK, OK, Close. If you have a broadband router with a DHCP server or other DHCP server on your network (not the ISp DHSP server), try enabling Use NetBIOS setting from the DHCP server instead.

what should I do now?

thanks

---

### Post by chilebeans on 2005-11-25
Ok so the Dhcp for the roller(Local Area Connection) is enabled. But the Dhcp for the PPP is not enabled.

also, I can not have the Dhcp for the roller enabled with the IP address punched in. Instead, I have to use autoconfiguration for the local area connection. This way it shows the DHCP enabled. Once I type in the 192.... the Dhcp will not show enabled. 

Does this seem right to you? under local area connection everything reads 0.0.0.0

at least the Dhcp is enabled for the Local Area Connection

---

### Post by tokyovigilante on 2005-11-26
That's fine, but not what I meant at all really... :S

DHCP on your Local Area Connection is working fine by default. What you need to do is enable it on the *modem*, which has nothing to do with your connection in the Control Panel.

Try this, ignoring everything else:

1) Connect your computer and modem directly with the ethernet cable, no router between.

2) Boot into Windows.

3) Start -> Settings -> Control Panel -> Network Connections.

4) Right-click Local Area Connection -> Properties.

5) Internet Protocol (TCP/IP) -> Properties

6) Click "Use the following IP address:"

7) Enter 192.168.1.5 for the IP Address.

8) Enter 255.255.255.0 for the Subnet Mask.

9) Leave the Default Gateway blank.

10) OK, and OK to exit the connection properties.

11) Check that Status of the Local Area Connection is Connected.

12) Open Internet Explorer.

13) Try to open the address 192.168.1.1.

If you see a login screen, let me know.

---

### Post by chilebeans on 2005-11-26
yes yes yes!!!!! I got it...Last night I wiped out everything on my pc and for some reason it worked after I did that....

Ok so I get the login screen name and password, and it says viking too on it...


well I typed my normal password and user name but it did not log me in?

is there any reason? or what should I do next?

---

### Post by chilebeans on 2005-11-26
I am re-reading all our conversations and I am understanding it all more. It realize I was more questions than thought. It takes some time but I am starting to see it instead of wondering how it looks.

thanks...hope you read my post above when you get the chance.

---

### Post by tokyovigilante on 2005-11-26
THANK GOD! We have a breakthrough.

Now you need to follow the instructions in the user manual I sent to enable the modem's DHCP server.

The username and password are both DSL.

---

### Post by chilebeans on 2005-11-27
Hope you did not lose faith in me because I did until I wiped everything out and it worked.

Tommorow...monday...I will try everything from the manual...the wife and I just got back from the beach. We have some stuff to do but I have this week off from school so I will dedicate my time to this. Hopefully it will work right away.

thanks

---

### Post by tokyovigilante on 2005-11-27
:) Not at all, I'm just glad we're making progress. I'm not sure why wiping everything worked, but it's great that it did. 

Yeah try and run through the manual, let me know if you have any problems. Enjoy your week off! I think it's time for the beach myself ;)

---

### Post by tokyovigilante on 2005-11-27
I've just been back over the manual, once you've logged into the modem with username and password DSL, can you click on the LAN tab and post a screenshot before you do anything else? Cool.

---

### Post by chilebeans on 2005-11-28
Ok I will...

Almost done with my school work and than I am done with school for the rest of this week. This way I can focus on this...ok I will post it...I will be back today

---

### Post by chilebeans on 2005-11-28
ScreenShot of LAN:

ok here it is, I will type it sense I can't save it for some reason?

                           LAN Configuration
 
Use this page to set the LAN configuration, which determines how your device is identified on the network. 



                                      LAN Configuration
 
       System Mode:                                     Routing And Bridging  
   
   Get LAN Address:                             X-->  Manual(this one )
                                                                External DHCP Server
                                                                Internal DHCP Server
 
     LAN IP Address:                                      192.168.1.1

LAN Network Mask:                                       255.255.255.0       
                
                 Speed:                                       100BT 
                
                Duplex:                                       Full 
                  
                  IGMP:                                       Enable
                                                        X---> Disable(this one)
 
 
                  
 
Copyright © 2001-2003 GlobespanVirata, Inc. All rights reserved. 

How do you screen shot the web? I went to File--> save as--> and the        picture was not full? it was blank?

---

### Post by tokyovigilante on 2005-11-28
Is internal DHCP server a link? If so click on that and post the result.

I usually press the PrintScreen keyboard button then paste into paint for screenshots.

---

### Post by chilebeans on 2005-11-28
[IMG]http://192.168.1.1/hag/pages/home.ssi[/IMG]

I am testing to see if  the picture shows

---

### Post by tokyovigilante on 2005-11-28
Just try clicking the Internal DHCP server link, Hit Printscreen on your keyboard, open Paint, and Edit->Paste. Then save the file and post it as an attachment.

---

### Post by chilebeans on 2005-11-28
I did that and it says the file is too big

its 2.9 mb...i compressed it to 460 KB but that is still too big..its under a paint file I think...I will try it again

---

### Post by chilebeans on 2005-11-28
Test pic...cross my fingers

---

### Post by chilebeans on 2005-11-28
can you read this? how did you paste yours so big? the same way you just told me? I had to save it under Jpeg to upload the file.

---

### Post by tokyovigilante on 2005-11-28
Good stuff, that worked well. Now click on DHCP server above and post another screenshot.

---

### Post by tokyovigilante on 2005-11-28
And DHCP mode as well. We're so close!! :)

---

### Post by chilebeans on 2005-11-28
DHCP server screen shot

---

### Post by chilebeans on 2005-11-28
DHCP mode screen shot

---

### Post by tokyovigilante on 2005-11-28
Awesome, OK, In the DHCP mode page, select DHCP Server from the list and click submit. Then go to the DHCP server page, click Add, and post a screenshot.

---

### Post by chilebeans on 2005-11-28
On this screen shot you will see I have and extra pop up(dhcp server pool). I got this once I clicked add.

---

### Post by tokyovigilante on 2005-11-28
Ok, enter the following values:

Start IP address: 192.168.1.2
End IP address: 192.168.1.254
MAC Address: Leave blank
Netmask: 255.255.255.0
Leave everything else blank, and click OK.
IF the DHCP Server page doesn't update, hit refresh, and paste a screen.

---

### Post by chilebeans on 2005-11-28
it worked fine I think.

---

### Post by tokyovigilante on 2005-11-28
Awesome!!! Now for an experiment. 

1. Plug your modem and desktop back into the hub, and your laptop as well if you want. 

2. Open Local area connection TCP/IP properties, and change the Address option from Use the following IP address... back to Automatically assigned (I think that's the wording.

3. Click OK to all the options and exit out.

4. Right-click the Local Area Connection icon in your system tray (next to the clock, bottom left) and click Status.

5. Click the Support tab, and click repair.

6. Post a screenshot, if it says Address Assigned by DHCP, we're away!!

---

### Post by chilebeans on 2005-11-28
Here its is...it looks fine...and been waiting to say this'

yyyyyyyyyyyyyyyyyyyyyyyyyaaaaaaaaaaaaaaaaaaaaaaaaaaaahhhhhhhhhhhhoooooooooooooooooooooooooooo


:D  thanks bro

what should I do next?


I would like to learn about the DSL web page we been on

can I now network and stuff....thats awesome man...thanks so much

---

### Post by tokyovigilante on 2005-11-28
THAT'S GREAT!!! Now Ubuntu should have no trouble picking up your network! Your laptop and Xbox should connect automatically too!

About the config utility page, I'm not sure where else to get info. I emailed TrendNet to get the Starter guide, you could try emailing them and asking for the full manual.

As to where now, its up to you. You have a full functioning home network. Install linux, do whatever you want. I'd suggest giving the LiveCD a run through first to make sure Linux can see the network, but it looks like you're not going to have any more trouble.

Congratulations!!

---

### Post by chilebeans on 2005-11-28
awesome...thanks so much...I am gonna go try and connect the other PC right now. 

I would like to make this Ubuntu..but my wife right now has to finish up her last year in college. So she has all this homework stuff on the laptop now. 

Hopefully I can network XP with ubuntu in the meantime but first I want to see now if it connects.

this laptop sounded bad, the fan ran so hard, when I installed the CD last time. I will read the information on laptops with ubuntu like you said earlier.

Ok...i am gonna go try connecting...ill post later....if your around cool...it may take awhile though


thanks so much..I totally want to get rid of XP....I have a friend who uses XP...he has allot of issues like I did. I will get him to switch.

thanks ....

I'll be back

how is NZ?  I am in Northern Chile and the Beaches here are great..

---

### Post by tokyovigilante on 2005-11-28
Plugging XP + Ubuntu into your hub will work just fine, DHCP isn't specific to any one OS. 

Good luck with getting everything going. 

Dunedin's beaches are both surf, so swimming is a bit rough though the sand is great, and they're really close to the town, as Dunedin is on the coast. We were going to go yesterday but my partner's allergies flared up something chronic, so hopefully she'll want to go today. 

Take care :)

---

### Post by chilebeans on 2005-11-28
my computer is not connecting to the internet for some reason?

I put DHCP.... shouldn't this work?... I also signed the IP and Subnet....but this didn't work either?

maybe I should reboot it? can I now for sure it will detect the DHCP when rebooting?

---

### Post by tokyovigilante on 2005-11-28
DHCP is just connecting your computer to your modem, which then takes care of connecting to the internet. Your connection may just be down temporarily, try opening the modem config (192.168.1.1 in IE) and checking the status page. 

If DHCP works in Windows (and AFAICT it is now) it should work in linux.

---

### Post by chilebeans on 2005-11-28
the dhcp server shows as fine...with the address 192.168.1.1

is that what you mean?

---

### Post by chilebeans on 2005-11-28
Im going to go ahead and reboot it and if the DHCP is not connecting than I will know something is wrong.

I think I did so much stuff to it that I probably should reboot it...instead of figuring what I did wrong.

---

### Post by chilebeans on 2005-11-28
Hi

I have to call it a night, my wife is back but I will be on all day tommorow so I will look for you if your on.

Thanks allot for your help, in rebooting the Desktop Linux detected the DHCP for the first time. So it detected it. 

Ok,,,take it easy

thanks and see you later

---

### Post by chilebeans on 2005-11-28
I rebooted and for some reason it does not connect. 

I go to network settings to see if it on DHCP, which it was.

I also went to check the modem status which showed it on. 

I am not sure why its not connecting, maybe it will work tommorow? 

thanks Ill let you know what happens

Do you mean the LAN tabe in the 192 IE address when checking the status?

---

### Post by tokyovigilante on 2005-11-28
No your DHCP settings should be fine, try visiting the home page. There should be a status page somewhere which will allow you to check your ADSL connection.

Did you enter your username and password into the web config utility? You modem needs to handle the ADSL dialling itself now, read through the "Setting Up a Connection" section of the Quick guide for instructions.

---

### Post by chilebeans on 2005-11-29
I went to the home web page and there was nothing that really made sense. Like the Model number and serial number were wrong. However, the IP was correct. 

It might be the way they do things here. It obviously is mine because the DHCP is working now.


I never had to enter my username and password. When excatly was I in the web config untility?

I typed DSL only twice and it brought me to the DSL web page but no password or username was required.

I will read through the setting up connection guide...I will be back in a bit

---

### Post by chilebeans on 2005-11-29
Ok.....no I never had to enter in the password and username when logged into the web configuration page....

is that weird? what does that mean?

---

### Post by chilebeans on 2005-11-29
Some questions?

In the quick guide there are checks or X's. However, I see a check under DNS primary and secondary server? Does this mean I need to know the settings for the DNS option and type the settings in? The same was for the Subnet mask and IP address.

also there are there is a check under the VCI but I see the value 8. I am lost, do I leave the 8 there or take it off?

Also, I see DNS is the same as my gateway settings under "ipconfig all"

---

### Post by chilebeans on 2005-11-29
Here are two screenshots.

the problem I have is look on the web page and look at where the IP adress and VCI is

Do I punch in the IP address? and how do I know the value of VCI? How does a check mark explain what to do?

I want to proceed just I want to make sure.Also in the start it says the ISP will give my the value of what to punch in. Not sure what they meant because later it says follow the table. I think if you know the answers to the question I ask I will be able to proceed.

thanks

By the way if you ever come to Chile you will find that Southern Chile is a great place of Nature. Enviornmentalist love Chile for this reason. Its a great place there. North part is desert mountain area but the beches are great.

The beaches are great because they are cleaner to what I am use to in Southern California. Also, the waves are much closer and my wife says no sharks have ever been reported.

---

### Post by tokyovigilante on 2005-11-29
OK, what we need to do is switch your modem from running in RFC 1483 (bridge mode) to RFC 2516 (Standard PPPoE). This means your modem will connect and authenticate itself, rather than pass the buck to your computer. I think the checkmarks just mean the information is required, as the info will vary from person to person and depend on your ISP. Try the following:

1. Open IE and navigate to the home configuration page (The one beginning with "ATM Interface..."

2. Leave ATM Interface and Operation Mode alone. ATM interface 0 just refers to the first (and in most people's case only) DSL connection running on the modem. Operation Mode should be self-explanatory ;).

3. Change Encapsulation from 1483 Bridged IP LLC to (something along the lines of) 2516 PPPoE (or PPP over Ethernet). It's definitely NOT PPPoA or IPoA or EoA (which may also be options).

4. Leave VCI and VPI as-is. These are country-specific codes which control how packets from your ISP are interpreted, and if they were working before, they still will. (Britain also uses 8 & 35, NZ uses 0 & 100).

5. Change Bridge to Disabled. This forces your modem to authenticate itself.

6. Leave IGMP disabled (I don't know what that is and mine is disabled and works fine ;)).

7. Leave IP and Subnet blank.

8. Change Use DHCP to enabled. This will force your modem to get IPs from your ISP, and you won't have to enter them. (This is completely separate from the DHCP *server* we had so much fun enabling. This is an external DHCP *client *to talk to your ISP, whereas the server we set up is internal and talks to your local network.

9. Leave Default Route and Gateway address blank as well (DHCP will take care of these too).

10. Enter the username and password as supplied by your ISP, and leave Use DNS enabled.

11. I can't see any further options down the page from your screenshot but the above should be all that is required. 

12. At the bottom of the page should be an option to Submit or Save the above options. Click that, then navigate to the Admin tab. There should be an option to Reboot your modem. Click that, and wait 30s.

13. After 30s, your modem should come back on and automatically connect to your ISP. You should be set!

If you have any problems let me know. :)

Chile sounds great, I'd love to visit. Maybe after med school, student loan permitting ;).

NZ has a temperate rather than tropical climate, but we can still hit 30s in summer. We don't have sharks either ;) although the southernmost recorded shark attack in the world was in NZ's South Island back in the 70s.

---

### Post by chilebeans on 2005-11-29
3. Change Encapsulation from 1483 Bridged IP LLC to (something along the lines of) 2516 PPPoE (or PPP over Ethernet). It's definitely NOT PPPoA or IPoA or EoA (which may also be options).




In step 3, I have no 2516 PPOE or PPP over Ethernet option.

this screen shot shows what options I have though, all of them, I can pick any other ones.

---

### Post by tokyovigilante on 2005-11-29
Try PPPoE LLC first and run through the rest of the instructions, if that fails go back and try PPPoE VC-Mux. It'll be one of these two.

If neither work, try enabling Default route with both the above Encapsulation options.

---

### Post by chilebeans on 2005-11-29
11. I can't see any further options down the page from your screenshot but the above should be all that is required.


it was just the DNS information...is that important?

---

### Post by tokyovigilante on 2005-11-29
DHCP will take care of DNS servers, just leave blank.

---

### Post by chilebeans on 2005-11-29
Got worried because I could not connect....I tried both settings ot for PPPoe?

I will go ahead and try again

---

### Post by chilebeans on 2005-11-29
oh the option says DNS enabled...maybe I should disable it?

---

### Post by tokyovigilante on 2005-11-29
No DNS needs to be enabled.

So you've configured as:

ATM Interface: 0
Encapsulation: PPPoE LLC
VCI: 8
VPI: 35
Bridge: Disabled
IGMP: Disabled
IP: blank
Subnet: blank
Use DHCP: Enabled
Default route: Enabled
Gateway IP address: blank
Username: <Your ISP's provided username>
Password: <Your password>
Use DNS: Enabled
Primary DNS Server: Blank
Secondary DNS Server: Blank

You saved and rebooted the modem (not your computer?)

After you reboot the modem, wait 30s and repair the Local Area Connection. Check it is still assigned by DHCP, and that your Gateway under Local Area Connection is not blank.

---

### Post by chilebeans on 2005-11-29
My wife is going to use the PC for like 5 minutes....I messed up on the default route....I will enable it though....so after all this dont worry if it doesn't connect right? I still haver to repair the local area connection like you said...

I will do this like in 5 minutes..

she needs to use it bad...sorry

---

### Post by chilebeans on 2005-11-29
Hi 

I am back, sorry about that..ok i will go ahead and do that and post the results.

---

### Post by chilebeans on 2005-11-29
Yes, its not doing it for some reason....

I did every option....exactly....with both PPOE types

it does not connect when I did it exactly how you said...


Here is a screen shot of when I go to the reboot...I was wondering maybe I need to reboot from "last configuration"

to your last question, I click the submit button, not the save button, when I am done configuring.

---

### Post by chilebeans on 2005-11-29
In the meantime I will keep trying to configure...maybe something will happen

---

### Post by chilebeans on 2005-11-29
looking at the quick guide I find it off a little on my default configuration.

it has the IP/subnet/dns primary/ secondary checked...but my information is blank

Does this matter?

---

### Post by chilebeans on 2005-11-29
In the quick guide: from step 6 ( commit) to step 7 (reboot) I find the page does not come up and I have to click to get to the reboot button.

---

### Post by tokyovigilante on 2005-11-29
It should go as follows - Submit on Home page, Commit on Admin page (You may need to refresh) then reboot with current configuration on Admin page. Any other option will remove your changes.

I took the configuration straight from the Starter Guide so it should be as I've said. I think you might still be looking at the Bridged IP column in the Quick guide, you should be following the PPPoE guide.

---

### Post by chilebeans on 2005-11-29
ok.,...I been trying this and nothing seems to work but it must be something I am doing....

I click submit from the Home/ quick configuration page

I will try refreshing before I reboot though on the admin..

be back in a few

---

### Post by chilebeans on 2005-11-29
I just noticed that when I submit the configurations it never ask me to click "yes" with the knowledge that its possible other people can see the information.

does this mean I need to do more than the submit button under Home/ quick configurations?

I will go and check this out.

---

### Post by tokyovigilante on 2005-11-29
It shouldn't because IE's default security precautions are disabled for your local network, which the configuration of your modem is a part of.

If you can't get it to run, try rebooting from default configuration, which will reset all the settings, and try again. (This will also disable the DHCP server, so you will have to set that up again as well, remembering to assign your local area connection an IP and subnet (192.168.1.5/255.255.255.0) manually).

If that still doesn't help, you are probably have to get help from someone who knows the local settings for Chile and your ISP, or contact Entel directly and hope for someone who speaks English.

---

### Post by chilebeans on 2005-11-29
its still the same for some reason? I dont know what is up but I did exactly what you have said to do, I have tried many times doing the same things as you type with both PPOE. It just does not connect? 

in the hom page I have a "system mode" that has "bridging" enabled and "wan to wan bridging enabled." does this cause a problem when I disable the bridge in "quick configurations"?

---

### Post by chilebeans on 2005-11-29
Ok I will go ahead and do that...I wrote all the info down just in case.


thanks and hopefully it will work :confused:

---

### Post by chilebeans on 2005-11-29
hmm I rebooted from default configuration and nothing happened.. I mean the DHCP settings are still there and its also on my local area connection

---

### Post by chilebeans on 2005-11-29
ok I been trying this all night ....I will try again tommorow....Im tired....stinking thing....

I dont know why it doesnt work...hopefully it will tommorow

thanks
bye

---

### Post by tokyovigilante on 2005-11-29
[QUOTE=chilebeans]in the hom page I have a "system mode" that has "bridging" enabled and "wan to wan bridging enabled." does this cause a problem when I disable the bridge in "quick configurations"?[/QUOTE]

Hmm, it might do. Try disabling anything about bridging or "WAN-to-WAN".

I'm sorry we're still struggling with this, but you have all the pieces in place, we just have to figure out a configuration that works for you.

Have a good sleep! :)

---

### Post by chilebeans on 2005-11-30
I tried removing the wan to wan and bridge but it did nothing for me.

I noticed when I change thing the home page would change..the status for the eoa would go from green to red... maybe this is an immediate sign that what I am doing wont work.

I think I need some other kind of settings...just wish I knew...I am not real practical when trying to figure it out because I dont know what all the stuff means.

---

### Post by chilebeans on 2005-11-30
I dont know if this means anything but my local area connection always stays the same.

So it never changes even after the settings are changed.

---

### Post by chilebeans on 2005-11-30
what's the goal of my settings on the home page? It says I have a check under DHCP server, do I want to have a check under dhcp client?

---

### Post by chilebeans on 2005-11-30
I am thinking maybe its just ubuntu and not the DHCP? This pc shows DHCP enabled, and the desktop(ubuntu) did detect it.

---

### Post by tokyovigilante on 2005-11-30
I'm running out of ideas to be honest, I really think you need help from someone local who can set your modem up for standard PPPoE.

Did your ISP give you any other info apart from a username and password?

Our goal is to set up two things.

1) Your modem to dial, authenticate and connect to your ISP using the PPPoE protocol, and act as a DHCP client to be assigned an IP by your ISP.

2) Independently of (1), set up a DHCP server to run on your modem, so that your modem will act as a firewall and DHCP server to assign internal IPs to your local network. I thought this had already been achieved, and that we were only working on (1).

Settings for 1 and 2 should not interact or overlap in any way.

In giving you help with configuring your modem to connect to you ISP I'm making some assumptions - that your ISP supports direct PPPoE connections (they should if bridging works), that your ISP is using DHCP to assign you an external IP, and that PPPoE and PPPoA (which I have experience with in NZ) have a similar configuration. I may be wrong about any of the above, which is why you really need someone to help you configure your modem.

BTW, how are you connecting to the net at the moment? Through your modem? What exactly is not working? If you can access the internet in Windows, and your computer has a 192.168.1.x IP assigned by your modem, you should be able to use Ubuntu without further ado.

---

### Post by chilebeans on 2005-11-30
Thanks for all your help. I understand what you want and I can only see from here if I can do it. 

All they gave me was a username and password and I still have the paper. No other information was given.

The DHCP server is already showing as checked, however, the DHCP client is what seems impossible.

I will see what I can do to get them to help me configure the modem in PPPOE

thanks again, hopefully something will work

In ubuntu i go to network settings to punch in the DHCP,DNS and host to key the settings. Is this the only place I need to go to try and connect?






I'm running out of ideas to be honest, I really think you need help from someone local who can set your modem up for standard PPPoE.



Did your ISP give you any other info apart from a username and password?

Our goal is to set up two things.

1) Your modem to dial, authenticate and connect to your ISP using the PPPoE protocol, and act as a DHCP client to be assigned an IP by your ISP.

2) Independently of (1), set up a DHCP server to run on your modem, so that your modem will act as a firewall and DHCP server to assign internal IPs to your local network. I thought this had already been achieved, and that we were only working on (1).

Settings for 1 and 2 should not interact or overlap in any way.

In giving you help with configuring your modem to connect to you ISP I'm making some assumptions - that your ISP supports direct PPPoE connections (they should if bridging works), that your ISP is using DHCP to assign you an external IP, and that PPPoE and PPPoA (which I have experience with in NZ) have a similar configuration. I may be wrong about any of the above, which is why you really need someone to help you configure your modem.

BTW, how are you connecting to the net at the moment? Through your modem? What exactly is not working? If you can access the internet in Windows, and your computer has a 192.168.1.x IP assigned by your modem, you should be able to use Ubuntu without further ado.

Ryan Walklin
[email]ryanwalklin@orcon.net.nz[/email]
Kubuntu 6.04 Dapper Drake AMD64
  	
Reply With Quote

---

### Post by tokyovigilante on 2005-11-30
That's quite alright. Just confirm one thing, how are you connecting in Windows? does the modem work properly when you run Windows?

---

### Post by chilebeans on 2005-12-01
yes the modem is fine but I have been getting a system shutdown every now and than but I have had this problem before with XP. So it is nothing unusual. The modem is working great.

I think what is weird is remember when you had me type in the DHCP numbers. Than later on you told me to rest last configuration in the ADMIN screen. Well, the DHCP numbers never change. Also, my local area connection never changed.

---

### Post by tokyovigilante on 2005-12-01
So you mean the modem is connecting itself, and you can get into the internet through your modem in Windows without having to type in your username/password, and your local area connection in 192.168.1.x assigned by DHCP?

---

### Post by chilebeans on 2005-12-04
I am back...my pc starting having a virus attack and my wife had some school stuff so I waited until she sent her files to her email

I have a brother in law helping me out who lives next door. I wrote down all the stats on the modem so I am not worried about him making changes to the modem. 

Right now on linux we are not getting the password and username login question like in windows XP. This is a problem for connecting since we need this.

He also thinks the servers here are based on windows which might be part of the problem.

So now he is trying to configure the modem so that it connects. He is trying to make it so you dont need a password or username.

He also thinks it may be the router. I told him  I have another router if he wants to try it. 

He knows how the internet works here so he is trying to figure it out. If we connect I will let you know what I found out. 

thanks again for your help

---

### Post by chilebeans on 2005-12-04
So you mean the modem is connecting itself, and you can get into the internet through your modem in Windows without having to type in your username/password, and your local area connection in 192.168.1.x assigned by DHCP?


No, but my brother in law is trying to make it work like this I believe. But right now I still type in the username and password.

I actully got my router to check under DHCP client and server. The two I believe you wanted while connecting. I don't know if this means anything? because the other PC(linux) is still not connecting. It may be that we are just not Ubuntu inclined. Maybe we need to learn how to use it.

---

### Post by tokyovigilante on 2005-12-04
> So you mean the modem is connecting itself, and you can get into the internet through your modem in Windows without having to type in your username/password, and your local area connection in 192.168.1.x assigned by DHCP?


No, but my brother in law is trying to make it work like this I believe. But right now I still type in the username and password.

That sounds good. I think the reason you are still having problems is because the modem is still working in bridge mode, ie it is connecting to the internet, but still asking your computer to log in by entering a user name and password. To get things going, you'll need to configure your modem to run in PPPoE mode so that it does both the connection and login. That way both Windows and Linux will not need a password to connect.

If you absolutely can't get the modem to work, then there is a broadband dialling program which will let you enter the username and password, but this isn't a very good solution as you will only be able to use one computer at a time. If you can get the modem to do all the work, then you can use all your computers (and Xbox!) at the same time.

Good luck!

---

### Post by chilebeans on 2005-12-04
I will let him know what you told me about it being in PPPOE mode. Yeah, I would want all connections at the same time. Even Xbox although I find I like playing the AI's more because people online get way to serious with it. It's fun but I can not get xbox games here anyway. When I get back to the states I will get that 360 xbox.

---

### Post by tokyovigilante on 2005-12-04
Yeah I know what you mean ;)

I have a PS2 and the NZ servers are usually a bit quiet, and the overseas ones have too high a latency to make playing worthwhile really. WoW is the best online game i've ever played though, and that and Quake 4 run on Linux so I'm happy!

---

### Post by chilebeans on 2005-12-06
I use to be so addicted to the Ghost Recon game in the states. I know how easily addictive these games can be. I know when I get back to the states I will start playing online again. In the meantime I think I will stick with sport games for quick fun. I want to wait mainly so I learn Spanish while I am here. The first year was wasted doing the online gaming and school work so I never really had great time to learn spanish.

Hey.....I am using Ubuntu and I am connected.....Yessssssssssss ...and finally.......:eek: :eek:  

Bye bye windows....you suck.....and I hate your guts. Man this pc is running like the 1000 plus dollars I spent on it. Windows always seemed to make my 1000 dollar computer run likes its a 250 dollar computer. So for all the time windows ripped money off me by making my PC run like an old crapper I get the final payback.
I can not count how many times my XP seem to get all these problems. Like all the time it would shut down, dump, and everytime i went on the net bugs seem to enter my PC.

Dude, this PC is so much better and now I want to learn all the cool things I can do  with it. 

Below is the steps I saw taken to make it work by my brother in law :

First he looked to try and find the Password and Username entry

After he could not find it he figure to do what you said, have it automatically connect

Next he went to the router and messed with the WAN and in Quick Configuration had it set under PPPoA LLC with the username and password.

Now he tried connecting and nothing still connected

Next day he brought back a sheet from the internet that said "Configuration with PPPOE in Ubuntu and Debian.

In this sheet it said to find the Root terminal and type in the following commands:

ifconfig

ifconfig eth0 down

nano /etc/network/interfaces

#auto eth0
#iface eth0 inet dhcp

#auto eth0
#iface eth0 inet static
# address 192.168.1.1
# netmask 255.255.0
# network 192.168.1.0
# broadcast 192.168.1.255
# gateway # 192.168.1.2

 /etc/init.d/networking restart

ifconfig

pppoeconf

/etc/resolv.conf

/sbin/ifconfig ppp0

ping ftp.cl.debian.org

ifconfig ppp0

/etc/resolv.conf

.........On the desktop all the commands were typed from step 1 to the last step. For my laptop I found I needed to start from    /etc/init.d/networking restart
. So after all the gateway and IP codes. The ping command really did the final test.

So now we are both connected to the internet and are both on Ubuntu. I am good because I am not in school right now so I can do this.

I think typing in these commands was the main thing. I wonder if the WAN mattered? I am not sure but I think it was the commands really that did it.

Thanks for your help...now I am gonna try and encourage allot of people to use Ubuntu... I am already talking to my friend Matt about it. Hopefully, get allot others.

What do you think I should try and learn on this Linux? I like to learn things now?

---

### Post by chilebeans on 2005-12-06
Now I am trying to get my friend Matt on this program so he can leave Windows like I  did.

---

### Post by chilebeans on 2005-12-06
Hi tokyovigilante ( <---- you a kung fu person?)

Do you have any advice on the chat program on Ubuntu? I have a friend I was going to talk too and it looks like the tricky part comes when trying to get hardware and programs to run? Any suggestions?

---

### Post by chilebeans on 2005-12-06
I am trying to use Gaim....for chatting...do I need to go online first and register there?

---

### Post by tokyovigilante on 2005-12-06
Hi :)

Congratulations! I'm pleased everything is finally going.

My nick is a reference to a track by obscure Detroit Grunge/Rock group Powerman 5000, "Tokyo Vigilante #1".  ;) I only wish I knew Kung Fu.

Gaim's probably the best IM client for linux, I haven't personally used it though. I'd guess you'd need to register for Yahoo/MSN/Whatever, then enter your account details into Gaim.

For your next step, I would say get comfy with the terminal. Most things in Linux are GUI now, but it's still a good way to get to grips with Linux as a whole. The [ubuntuguide ]("http://www.ubuntuguide.org")is really good as well.

---

### Post by chilebeans on 2005-12-06
I understand how to use the Gaim now...ok...I will read that... guide.

What do you mean by getting use to the terminal? Do you mean typing in the commands in the root terminal or what?

---

### Post by chilebeans on 2005-12-06
I am a newbie and would like to install Gizmo chat. How do I install this software. If its too detailed could you give me a general understanding? 

thanks

---

### Post by tokyovigilante on 2005-12-06
[http://www.gizmoproject.com/download-linux.html]("http://www.gizmoproject.com/download-linux.html")

If you're looking for software, search packages.ubuntu.com as a first step, then Google "<software> linux" or "<software> ubuntu" for help. Trust me, on Linux Google is your best friend, someone has ALWAYS done what you're trying to do and posted a Howto. Besides, i've gotta cut you loose into the Linux world sometime right? ;)

---

### Post by chilebeans on 2005-12-06
Cool, I already use google. I just need to get informed. Right now I am not sure if things are right or wrong. 

I will read the info they have on google.

thanks

---

### Post by chilebeans on 2005-12-06
I am trying a test right now. I have gizmo-project downloaded to my computer. I want to see if I can install the software. I am trying to find the package and that has not worked yet. 

I been reading and most of the information is how to install software off the Synaptic Packages. But I want to use software off the internet. This is challenging to find any reall instructions. I found 2 but there commands did not work for me.

---

### Post by tokyovigilante on 2005-12-06
Have you tried just downloading the three .deb files (.deb packages are what Debian uses for software installation, kind of like a Windows .zip, and since Ubuntu is based on Debian, we use the same),then running

```
dpkg -i /path/to/file.deb
```
(replace /path/to/file with the directory and filename of each package)

---

### Post by chilebeans on 2005-12-07
I see the three .deb files ( control.tar.gz, data.tar.gz, debian-binary) with the add and extract buttons. I am not sure what to do next.

Do you want me to type that commnd in the root terminal?

---

### Post by chilebeans on 2005-12-07
I will read up on the file roller and see what I can do in relation to your command you gave me.

---

### Post by chilebeans on 2005-12-07
I am trying to install a serperate file which excludes me from installing through synaptics. In the "Wiki" tab instructions for downloading off the internet it says to download the file to desktop which I belive I have done. I have not extracted the file but its there. Now the "Manual" for installation gives me a process to follow while typing under terminal:

Cd desktop

sudo dpkg -i gizmo-project_1.0.0.15-1_i386.deb


however the result I get is as follows:

root@enteladsl:/home/username # cd desktop
bash: cd: desktop: No such file or directory
root@enteladsl:/home/username # sudo dpkg -i gizmo-project_1.0.0.15-1_i386.deb
dpkg: error processing gizmo-project_1.0.0.15-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 gizmo-project_1.0.0.15-1_i386.deb
root@enteladsl:/home/username #

Can anyone help me on this? I believe I am typing in the right commands.

---

### Post by chilebeans on 2005-12-07
Hi Tokyovigilante

I typed...      dpkg -i gizmo-project_1.0.0.15-1_i386.deb

and got the following:



root@enteladsl:/home/username # 
dpkg: error processing gizmo-project_1.0.0.15-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 gizmo-project_1.0.0.15-1_i386.deb
root@enteladsl:/home/username #

I got the same message when typing in "sudo" before the command.

---

### Post by tokyovigilante on 2005-12-07
Hey,

You just need to be in a user terminal to install, ie. Applications -> Accessories -> Terminal.

Then cd to the directory you downloaded the files to (probably best to shift them from the Desktop into somewhere else in your home directory as it's easier to get to from the terminal) and type sudo dpkg -i <filename>.

PS In the Bash terminal (what you're using, you can hit the Tab key after the first couple of characters, and it will fill in the rest of the matching filename so you can be sure it's right. Also, Bash is case-sensitive, so Desktop is a different folder to desktop.

Make sure you install the packages in the order the website recommends.

Also, have you tried just right-clicking the packages on the desktop one at a time and selecting install?

I know that works on Kubuntu, should be an option in Ubuntu too.

---

### Post by chilebeans on 2005-12-07
I did not know about the difference between "desktop and Desktop"

so this time it detected the file in the terminal which was a great feelings. However, the dependencies are the issue of course. You said to install in the order instructed. I did not really see an exact order of installation but I will look.

thanks

oh yeah

I am not exactly sure what you meant by sending it to cd? Is this place under filesystem?

---

### Post by chilebeans on 2005-12-07
Hi TokyoVigilante

I was not going to update my 5.04 since there are no problems with it. However, you explained that I could right-click on the gizmo file and see and install button? I do not have that great feature. Maybe its becuase of the older version I have? 

Will updating my 5.04 give the installation feature?

thanks you been great help

---

### Post by tokyovigilante on 2005-12-07
From [http://support.gizmoproject.com/index.php?_a=knowledgebase&_j=questiondetails&_i=135]("http://support.gizmoproject.com/index.php?_a=knowledgebase&_j=questiondetails&_i=135")

nstalling Gizmo Project on Linux
This article specifically relates to the Linux version of Gizmo Project. There are similar articles for the Windows, and Mac versions.

> To install Gizmo Project on Debian, the following Debian packages must be installed in order:

   1. Bonjour - A networking library from Apple. More information can be found here.
   2. libsipphoneapi - This is the main library for Gizmo Project, it is common to all of our versions.
   3. gizmo-project - This file is specific to the Linux version, and contains the User Interface

cd is not a folder, it is a shell command to **c**hange **d**irectories.

e.g. cd /home/<username> will change to your home directory. cd .. (two dots) takes you to the directory one level up.

---

### Post by chilebeans on 2005-12-07
Hi TokyoVigilante


Well, sorry about not reading the website. I think I am so use to just clicking one download like in windows that I thought all I needed was one download. I realize I have to read more for now on and look carefully at the download process

In the Installation,I was pretty proud of myself when I realized the problem and corrected it. For Gizmo I have three downloads, the first dowload "bonjour" never amounted to a dependency problem. The second download did and I corrected them all by installing the file in the synaptic package manager. However, the third download "gizmo-project" showed dependency problems and I corrected them. Yet, the problem still shows. I even downloaded all packages that had the same name. The terminal even shows the exact file I need in the Synaptic Package. However nothing seems to change after I installed it. What do you think I can do about this?

Below is the actual read out:


username@enteladsl:~$ cd Desktop
username@enteladsl:~/Desktop$ sudo dpkg -i bonjour_107.1-0.0.0.50.linspire0.2_i386.deb
(Reading database ... 60501 files and directories currently installed.)
Preparing to replace bonjour 107.1-0.0.0.50.linspire0.2 (using bonjour_107.1-0.0.0.50.linspire0.2_i386.deb) ...
Unpacking replacement bonjour ...
Setting up bonjour (107.1-0.0.0.50.linspire0.2) ...
username@enteladsl:~/Desktop$ sudo dpkg -i libsipphoneapi_0.78.20051201-1_i386.deb
(Reading database ... 60501 files and directories currently installed.)
Preparing to replace libsipphoneapi 0.78.20051201-1 (using libsipphoneapi_0.78.20051201-1_i386.deb) ...
Unpacking replacement libsipphoneapi ...
Setting up libsipphoneapi (0.78.20051201-1) ...
username@enteladsl:~/Desktop$ sudo dpkg -i gizmo-project_1.0.0.15-1_i386.deb
Selecting previously deselected package gizmo-project.
(Reading database ... 60501 files and directories currently installed.)
Unpacking gizmo-project (from gizmo-project_1.0.0.15-1_i386.deb) ...
dpkg: dependency problems prevent configuration of gizmo-project:
 gizmo-project depends on libfontconfig1 (>= 2.3.0); however:
  Version of libfontconfig1 on system is 2.2.3-4ubuntu7.
 gizmo-project depends on libpango1.0-0 (>= 1.8.2); however:
  Version of libpango1.0-0 on system is 1.8.1-0ubuntu2.
dpkg: error processing gizmo-project (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gizmo-project
username@enteladsl:~/Desktop$

---

### Post by chilebeans on 2005-12-07
Ok yeah...in the download dependency error it said

izmo-project depends on libpango1.0-0 (>= 1.8.2); however:
Version of libpango1.0-0 on system is 1.8.1-0ubuntu2.

the 1.8.1-0ubuntu2 was identical under the "version"...so this is what I went by for installing the package.

---

### Post by tokyovigilante on 2005-12-07
Well it looks like you have everything you need installed, it's just that you need to update to new versions.

Go to Synaptic and find Manage Repositories, the add universe to all of them, should just be a checkbox, but you may need to edit and manually type it in. Just append it to the lin that says "main restricted", ie change to "main restricted universe." It may ask you if you want to update the package lists, if so click yes.

Then go to a terminal and type:

```
sudo apt-get update
sudo apt-get upgrade

```
This will update your system to the latest stable software versions, and get bug and security fixes.

Hopefully this will give you the correct versions so you can install Gizmo.

---

### Post by chilebeans on 2005-12-08
I typed in the main restricted universe in all of them. However, it download most packages but that when I clicked ok an error came up.It said:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences

Earlier today I updated my computer and the computer shut down becuase of the battery. So now when I boot I get an message that says something like

Locale: Lc Message could not connect to file or directory.

Maybe I should reboot the compouter? Or do you think its the way the router is?

---

### Post by chilebeans on 2005-12-08
I went ahead and tried to typed the other commands you gave me(sudo apt-get update/upgrade and got the following error messsage:

Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/hoary/Release  Unable to find expected entry  universe/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/universe Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.






username@enteladsl:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  gizmo-project: Depends: libfontconfig1 (>= 2.3.0) but 2.2.3-4ubuntu7 is installed
                 Depends: libpango1.0-0 (>= 1.8.2) but 1.8.1-0ubuntu2 is installed
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/universe Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Unmet dependencies. Try using -f.
username@enteladsl:~$



I got the same error message that I got in the repository. I than tried sudo apt-get -f install


username@enteladsl:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  gizmo-project
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 9762kB disk space will be freed.
Do you want to continue [Y/n]?y




after yes...i got



rl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 62728 files and directories currently installed.)
Removing gizmo-project ...
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/universe Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems


I went back to running sudo apt-get update but got the same problem from the start. I think maybe my pc turning off during the update screwed it up. I will try the other pc and see what happens.

---

### Post by chilebeans on 2005-12-08
everytime i log into synaptic packages I get the error message:

W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/universe Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)


you have any idea what happened?

---

### Post by tokyovigilante on 2005-12-08
[QUOTE=chilebeans]I typed in the main restricted universe in all of them. However, it download most packages but that when I clicked ok an error came up.[/QUOTE]

Type 
```
cat /etc/apt/sources.list
```
in a terminal and post the result.

[QUOTE=chilebeans]Earlier today I updated my computer and the computer shut down becuase of the battery. So now when I boot I get an message that says something like

Locale: Lc Message could not connect to file or directory.

Maybe I should reboot the compouter? Or do you think its the way the router is?[/QUOTE]
Hmm I've never seen that before. Do you mean your laptop went flat because you were running on batteries? Or is there an issue with your desktop's CMOS battery?

This may be a hardware issue. At what stage of boot do you get it?

---

### Post by tokyovigilante on 2005-12-08
Now I see what's going on. You're running the 5.04 release of Ubuntu, whereas the latest version is 5.10 (Breezy Badger). Its probably a good idea to upgrade to this version. If you post your /etc/apt/sources.list, I'll update it and you can write it back, then upgrade to Breezy.

BTW, the apt error message is related to not being able to find the Ubuntu CD. You need it in the drive if you're installing something from it.

---

### Post by chilebeans on 2005-12-08
Hi TokyoVigilante

Ok the repository is fixed now. That was my problem because once it was fixed the apt-get update/upgrade were fine plus I stop getting error messages. The problem was when I typed in the "main restricted universe" it did not understand. So I removed all of the repositores and added the three back --Ubuntu 5.04 hoary hedgehog (binary), Ubuntu 5.04 Security Update (binary), and Ubuntu 5.04 Updates (binary). They were all checked under the four boxes when editing and there recieved the name "main restricted universe multiverse."


I went ahead and typed cat /etc/apt/sources.list and got the following:


## Uncomment the following two lines to fetch updated software from the network

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe m ultiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe mul tiverse




Do you know how I can update my version? I thought I already did that when I went to update manager? it updated like 124 packages I believe.

thanks

---

### Post by chilebeans on 2005-12-08
If you post your /etc/apt/sources.list, I'll update it and you can write it back, then upgrade to Breezy.

Ok I read what happened in the terminal and I guess I can not update? Its free though ...?

---

### Post by tokyovigilante on 2005-12-08
> **chilebeans]o you know how I can update my version? I thought I already did that when I went to update manager? it updated like 124 packages I believe.
[/QUOTE]
Yes that will upgrade any packages which have changed within Hoary (5.04), like a service pack for Windows. Upgrading versions is like replacing Win 2000 with XP, but it's much easier  said:**
> Its free though ...?
Yes, that's one of the great things about it ;)

---

### Post by tokyovigilante on 2005-12-08
You might also want to download the new Breezy CD from [http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/ubuntu-5.10-install-i386.iso]("http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/ubuntu-5.10-install-i386.iso")

---

### Post by chilebeans on 2005-12-08
I opened up terminal and did the following:

username@enteladsl:~$ sudo mv /etc/apt/sources.list /etc/apt/sources.old
mv: cannot stat `/etc/apt/sources.list': No such file or directory
username@enteladsl:~$ sudo nano -w /etc/apt/sources.list
username@enteladsl:~$ sudo apt-get update
E: Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list
username@enteladsl:~$ sudo apt-get dist-upgrade
E: Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
username@enteladsl:~$



I never saw the following after typing the "sudo nano -w /etc/apt/sources.list" :



deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security breezy restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted universe multiverse

Am I in the wrong terminal?

---

### Post by chilebeans on 2005-12-08
You might also want to download the new Breezy CD from 

[http://mirror.mcs.anl.gov/pub/ubuntu...stall-i386.iso](http://mirror.mcs.anl.gov/pub/ubuntu...stall-i386.iso)

Can I install it from the desktop?

---

### Post by chilebeans on 2005-12-08
ok..,.,im downloading the file and its downloading real real slow...its says I have 1 hour and 20 minutes left.

---

### Post by chilebeans on 2005-12-08
ok....wait I followed your instructions wrong...figures....I think its downloading so disregard anything I said before...dur


thanks

---

### Post by tokyovigilante on 2005-12-08
Good to see you worked things out ;)

The best way to follow directions off the net is to copy and paste into a terminal, so you don't make typos.

BTW, if you're following a step-by-step guide, its not generally a good idea to just go on to the next step if the current one has failed, as they generally depend on the one that comes before ;).

---

### Post by chilebeans on 2005-12-08
ok...it took like an how and 20  minutes to download and when I was done it gave me some problems as follows:



Fetched 529MB in 1h28m0s (100kB/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.0.7-0ubuntu20_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.0.7-0ubuntu20_i386.deb)  Connection timed out [IP: 82.211.81.151 80]
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/breezy Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_breezy_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?



so natrually I typed the apt-update and got the following:



username@enteladsl:~$ sudo apt-get update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16.9kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [19.6kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Packages
Fetched 36.8kB in 2s (12.8kB/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/Release](http://security.ubuntu.com/ubuntu/dists/hoary-security/Release)  Unable to find expected entry  breezy/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/breezy Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_breezy_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
username@enteladsl:~$



what does all this mean? Did it fail? I will try to install the files anyhow...

thanks

---

### Post by chilebeans on 2005-12-08
also when I went to the synaptic package mangager page it gave me this error:


i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)


looks like I am missing packages and still using old ones. Any idea what to do?....I know why it timed out in the process of the download... ( router had to be power back on).....so maybe I have to do the whole thing over again? what do you think?

while I was downloading though it seem to go on fine? not sure if this matters but thats what happened.

---

### Post by chilebeans on 2005-12-08
I think the errors above are due to the repository. In there all three are checked. They are :

[http://archive.ubuntu.com/ubuntu/breezy](http://archive.ubuntu.com/ubuntu/breezy) (binary)

ubuntu 5.04 Security Updates ( Binary) ...breezy underneath it

[http://archive.ubuntu.co,/ubuntu/breezy-updates(binary](http://archive.ubuntu.co,/ubuntu/breezy-updates(binary))



I find when I click "add" there is only the ubuntu 5.04 stuff and no breezy selection. Should I try and install becuae I doubt it will work with the errors in the synaptic page and the errors I recieved while downloading?

---

### Post by tokyovigilante on 2005-12-08
What you have downloaded will be fine, but there are still errors in your sources.list.

try posting cat /etc/apt/sources.list again and we'll take a look.

---

### Post by tokyovigilante on 2005-12-08
Synaptic/apt is trying to tell you something's not right, don't try and force an upgrade with a bad configuration, you'll just end up breaking your system. Your sources.list has to be correct first.

---

### Post by chilebeans on 2005-12-08
I typed the sudo apt-get dist upgrade and it is working something....i got this message in the midst of it too

You will need to start these manually by running `/etc/init.d/<service> start'
If the service still fails to start, you may need to file a bug on
libc6 or the service involved.

I read your last messages and I will type those commands next.

thanks

---

### Post by tokyovigilante on 2005-12-08
[QUOTE=chilebeans]You might also want to download the new Breezy CD from 

[http://mirror.mcs.anl.gov/pub/ubuntu...stall-i386.iso](http://mirror.mcs.anl.gov/pub/ubuntu...stall-i386.iso)

Can I install it from the desktop?[/QUOTE]

You'd need to do a fresh install and then set up the networking again as before. Hopefully this won't be necessary, the upgrade from Hoary 5.04 to Breezy 5.10 should just work. But it's good to have the latest version on CD so that if you ever need to reinstall or put it on a different computer then you don't have to download all the updates again.

BTW an ISO is an exact copy of a CD (an "image") in archive form. You use a program called gnome-baker (get though Synaptic once we've fixed all these upgrade probs), which is like Nero for Windows, and choose the "Burn Image to CD option" (I'm assuming you have a cd burner). If not just get a rich friend to do it for you ;)

---

### Post by tokyovigilante on 2005-12-08
[QUOTE=chilebeans]I typed the sudo apt-get dist upgrade and it is working something....i got this message in the midst of it too

You will need to start these manually by running `/etc/init.d/<service> start'
If the service still fails to start, you may need to file a bug on
libc6 or the service involved.

I read your last messages and I will type those commands next.

thanks[/QUOTE]
This shouldn't matter too much, its just complaining that it needs something else installed which will most likely be set up later in the upgrade. A reboot following major upgrades like this will generally fix most things. Let me know how you're getting on with the process, and post up that sources.list. :)

---

### Post by chilebeans on 2005-12-09
Hey

Lol, well last night the pc powered down again..it was because the laptop had been on all day. Ok, so i rebooted and now I  will upgrade like you explained. I will let you know what happens...thanks

---

### Post by chilebeans on 2005-12-09
ok I re installed ubuntu....update the version and at the end I got the error message:

W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/breezy Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_breezy_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

I will go ahead and reboot now...than try and install gizmo.

---

### Post by chilebeans on 2005-12-09
ok when I rebooted the first time I got some pop up error message for the LUM?

I rebooted twice and in the load up the " random generator number" shows fail?

The good thing is I know for sure I have the newer version. Last night it did not load up like this. 

Ok..i will try to install gizmo

---

### Post by chilebeans on 2005-12-09
ok...I did the
 
cd Desktop

than I did the

sudo dpkg i- <files1,2,&3>

now everything went great with no errors but I can't tell if its been downloaded? I will see if I am missing a step.

---

### Post by chilebeans on 2005-12-09
I figured out why that error message comes at the end of the upgrade to the new verison. Its the repository section. My repository looks perfect....i got all three updates...not websites like last night. I have all of them checked right too.

The above thread is about the gizmo download just in case you were wondering.

Is there a difference between "terminal" and "root terminal" because in this new version all I see is the terminal...I will explore some more though.

---

### Post by chilebeans on 2005-12-09
ok....I have been reading up and found that the command dpkg -l shows what I downloaded. I than realized its the same as my repository. So I went to the repository and found that Gizmo-project shows its downloaded. 

How do I install this now and use it? I will try and see if I find a way in the meantime.

---

### Post by chilebeans on 2005-12-09
What I meant before is its installed but how do I use Gizmo now?

---

### Post by tokyovigilante on 2005-12-09
I don't think it is fixed or installed as you're still having errors when you try to update.

Please post the results of cat /etc/apt/sources.list.

---

### Post by chilebeans on 2005-12-09
my results are:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted universe mu ltiverse


I see the green box next to Gizmo in the repository too....just don't see it anywhere else? its weird cause I figured I could use it now or try to.

---

### Post by tokyovigilante on 2005-12-09
Hmmm...

Edit your sources.list (sudo nano -w /etc/apt/sources.list) and take out the space in the middle of the last multiverse. Then try apt-get update again. Do you still get any errors? Post the output of that if you can thanks.

The terminal just means Linux's command-line interface, a much more powerful and clever version of DOS if the analogy helps. Terminals start in user mode, ie you are only allowed to perform standard user functions like run programs etc, no configuration changes. The prompt ends in a $ sign. A root terminal is obtained by typing sudo -i and then your password. This authenticates you as root or the superuser, allowing you full write access to your system. Its very easy to break things as root, which is why (unlike Windows) you aren't allowed to be root all the time. Single commands can be run by prefacing them with sudo (SuperUser DO) as we have been doing.

---

### Post by chilebeans on 2005-12-09
I went to see if there was a space inbetween but there was none. I saved it amd typed the apt-get command and got no errors:


username@enteladsl:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [19.6kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [19.4kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [11.1kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Fetched 70.1kB in 3s (18.0kB/s)
Reading package lists... Done

I rebooted this morning and than updated it....the repository and synaptic ( apt-get) page handled really fine. I see the difference. Last night my PC shut down during the download. Maybe this is why I had allot of problems.

Thanks for the sudo explanation. I am starting to read the how to's and beginner guides. Also, I use to do these commands at work because I believe we ran ciso...or unix? The thing is we copied steps instead of really understanding. But I don't fear command types because I use to do them all the time.

Should I see Gizmo software that can be used?

---

### Post by tokyovigilante on 2005-12-09
OK cool, if you've done a sudo apt-get upgrade or used Synaptic to upgrade after the update, then just reinstall gizmo and it should work fine. If it doesn't appear in the menu just try "gizmo" from a terminal.

---

### Post by chilebeans on 2005-12-10
cool...It ended up working

First it acted weird because it saw nothing in my username for the program of gizmo and kept asking for me to type in a name.But  than I removed....reboooted,,,,,and I was able to use gizmo.

The weird thing is that I have to type "gizmo" in terminal because its invisible. I never see it? and look for it buts its hidden?

thanks allot....maybe I am a master at downloading software now? does it get crazier than this? if so how do you think?


I am gonna try to install hardware ( the printer) next. Once I can the printer....and digital camera on the PC I will be set...I mean the wife wont be all worried.... I was like..yeah see software download is no problem ;) she know now I can download it....relief relief....

That wikipedia websit is awesome for learning commands...like what they mean and stuff so instead of letters I see a story or specific command.

---

### Post by chilebeans on 2005-12-10
wow...no need for help on the hardware...installing the printer was easier than windows. Usually I have to download the drivers off the web. Here I just locate the type of printer I am using, and than I am good to go.

So far this is my wife and I really need for an operatings system ( printer, camera, and ability to download software) 

What do you think I should try to do next? I want to learn all this cool stuff and I would like to be learning stuff constantly....although I wont be in a rush since I have what I need but I want to use this to the full potential. Maybe it can be a test and I will try and figure it out? I just want to learn this more and you said how the learning curve is great. Maybe I can try and do something that you ask?


thanks allot for all your help.....I appreciate it allot...I probably asked a bunch of dumb questions but hey....this dummy can use the OS now....awesome, awesome, and awesome.

It is probably childish to sit here and be anti-windows but I have had so much problems with them. I depend on a computer too since I am going to school here and stuff. Well, to make a long story short you saved me allot of pissed off days. I am amazed how this program just works for me. I can open more than 3 web browsers without it slowing down. I can also not get so pissed off like someone else is controling my computer. Its great...

So thanks dude....because you helped save me from allot of BS and hassle....thanks man....maybe I can help someone else out...I am trying to get my friend on it..well, thanks again

---

### Post by tokyovigilante on 2005-12-11
That's awesome, I'm really glad everything is working for you now. 

I didn't think your questions were stupid at all, everyone's gotta start somewhere. There's no question Linux can be tough to set up, but once its going, its fantastic, as you're already seeing.

As for where to next, I guess thats up to you, and what you want to do with your computer. The [Ubuntu guide]("http://www.ubuntuguide.org") has a lot of good info regarding multimedia and stuff. The forums are good to browse through. 

Try searching the forums for a piece of software called Automatix. It's an extension to Ubuntu that makes installing software and setting things up a one-click process.

Take care, and most of all, have fun!

---

### Post by chilebeans on 2005-12-11
Do you know how to find gizmo physically? Because I always have to type gizmo in the terminal section.

Also, my cursor seems to jump around the computer every now and than. Do you have any idea on how to fix this? Not a real big deal for me but my wife had to look at the keyboard when she types.

Hey, I been reading the forums and found Kyral on terminal for beginners real enlightening. 

thanks again

I will tell my friend Matt about that automatix program. Sounds encouraging for those who like windows.

Also, do you now of any spanish to english translations on this Linux? Maybe I can have a software program for learning Spanish.

---

### Post by chilebeans on 2005-12-12
right now I am trying to figure our how to install a gz file? I'll see if I can find out anything

---

### Post by tokyovigilante on 2005-12-13
To find gizmo, open a terminal, and type

```
sudo slocate -u
```

This will create an index of all the files on your drive in a few seconds.

Then type 

```
locate gizmo
```

It should be in /usr/bin or something along those lines. When you've found the file, you can create a shortcut to it by using the Gnome menu editor (Smeg I think).

You don't install gz files, gz is short for gzip, similar to a windows zip file. Its just a program or collection of files in an archive. Often the files are also compressed using tar, in which case the file end in .tar.gz, and be called a "tarball." To extract a straight .gz file, use the command 

```
gunzip <filename>
```

to extract a tarball (.tar.gz), use

```
tar -xvzf <filename>
```

which will do tar and gz extraction in one step. Again if the program is in Synaptic, it's much easier to install software using it rather than manually, as that way updates are automatic. For example, Skype, a VoIP program like gizmo, should be in Synaptic.

---

### Post by chilebeans on 2005-12-13
Hi TokyoVigilante

Man...I may need to go back to windows on this computer while I learn Linux on the other computer. The problem is I can not even read files from classes online. I open it and under doc...as well as other programs. When I scroll down everything locks up. Yeah...just locks up and my computer can be used. So I power down and restart it. If I can not figure the file problem I will have to go back to XP :(.....but I can use the other PC to learn how to fix that....

---

### Post by chilebeans on 2005-12-13
Well...back to windows...I realize I need to really learn everything. So far its just the word document that prevented me from moving forward. It just kept stalling my pc and I would have to hit the power button.

I will go on the other PC and learn all this stuff. I am sure there is some way to fix the problem so I will just search around. 

Thanks

---

