---
title: "Setting up Broadband in Breezy"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by agarwaldvk on 2006-03-02
Hi Everyone

I have also set up Breezy for my dad on his computer. Went like a breeze, no problems at all.

He has got broadband for his internet.

Can someone help me to configure his internet/broadband in Breezy.


Best regards


Deepak Agarwal

---

### Post by procras on 2006-03-02
The set up will depend on the type of connection between the computer and the !broadband box!

Is it an ADSL modem/router to which the computer is connected to via a network port? What does it say on the box?

---

### Post by agarwaldvk on 2006-03-02
Procas

My apologies for not providing adequate information.

The connection is through an ADSL modem. I don't think there is a router because there is only one computer - would he need one? But he can connect to the internet on windows xp? Wouldn't that mean that he wouldn't need a router, would it?

Sorry but I don't know any better than this.

Does this help?


Best regards


Deepak Agarwal

---

### Post by Razorback on 2006-03-02
No, he doesn't need a router but a router can give him a hardware firewall which is beneficial especially for an XP machine. ;)

---

### Post by agarwaldvk on 2006-03-03
Guys

I need more help trying to set up my Dad's broadband using ADSL modem.

What do I need to type and where so that he can browse the internet using his ADSL modem (broadband).

Any further assistance shall be highly valued.

Best regards


Deepak Agarwal

---

### Post by evilc on 2006-03-03
What make of modem is it, have a look at this link it may help you.
[http://users.netwit.net.au/~pursang/adsl.html](http://users.netwit.net.au/~pursang/adsl.html)

---

### Post by agarwaldvk on 2006-03-03
EvilC

The make and model is "DLink - 302G"

I am having a look at the suggested link and let you know if I need further assistance.

Best regards


Deepak Agarwal

---

### Post by JAwuku on 2006-03-03
Is your ADSL modem connected by USB or Ethernet? It seems that Ethernet connections are more compatible. Try that if the modem has one.

I use a router to connect my Windows and Linux boxes via Ethernet, and Ubuntu instantly recognises the connection via DHCP.

---

### Post by evilc on 2006-03-04
The DLink DSL-302G ADSL modem is a router/DHCP-server. It can use either USB or Ethernet, would suggest use Ethernet there are drivers available for this modem.

---

### Post by Jucato on 2006-03-04
how about the command
```
sudo pppoeconf
```?? Used it to configure my ADSL with a router on an ethernet NIC

---

### Post by agarwaldvk on 2006-03-04
FenyX/EvilC

Do I just need to type in the command specified and not do anything with 

System -> Administration -> Networking?

Which is what I was trying and didn't know what to do next?


Best regards


Deepak Agarwal

---

### Post by Jucato on 2006-03-04
You just have to type that in the terminal. It will detect your eth0 and stuff. It will be asking you questions, but the defaults work. The only things you will have to take note of (for basic users) will be:
- username and password for your ADSL connection
- whether you want PPPoE to be started during startup

At least that's what I did. No problems here (though I'm not entirely sure if it's the "official" or proper way to do it).

---

### Post by agarwaldvk on 2006-03-04
Dear Fenyx

Thanks a lot for your help.

I shall try that tomorrow.

Once again thanks for your persistance with my ignorance.


Best regards



Deepak Agarwal

---

### Post by agarwaldvk on 2006-03-05
Guys

I tried that command :-

sudo pppoeconf

It then scanned 2 interfaces and could not find the "Access Controller"

I use Ethernet connection. Initially it used USB but I changed it to Ethernet now.

What do I do next?

At the time of installation, for some reason it did not find DHCP networking thing. So I proceeded with not configuring the network at all. Is that the  problem. I can do a reinstall but if I am supposed to manually configure the network, any suggestions, how would I go about doing that?


Best regards


Deepak Agarwal

---

### Post by agarwaldvk on 2006-03-05
Hi Everybody

Could someone please help me with this!

I need to get my Dad's computer fixed up. He is not particularly pleased with me stuffing him up.

Further, I need this since I am also looking at upgrading mine from dialup to Broadband but this sort problems, I am not looking forward to doing so.


Best regards


Deepak Agarwal

---

### Post by jbmalone on 2006-03-05
[QUOTE=agarwaldvk]Hi Everybody

Could someone please help me with this!

I need to get my Dad's computer fixed up. He is not particularly pleased with me stuffing him up.

Further, I need this since I am also looking at upgrading mine from dialup to Broadband but this sort problems, I am not looking forward to doing so.


Best regards


Deepak Agarwal[/QUOTE]

Shut down the computer, plug in the modem, then unplug the power cord.  Plug the power cord back in and then restart the computer.  This should reset the modem and have to pull the DNS servers again.  You should know if everything worked if the clock synchronized with the linux site on startup.  To make sure that everything is ok, go into Networking and make sure the eth0 connection is active.  You can poke around in those tabs too to figure out what your problem is, like if the computer is even recognizing the modem itself.

---

### Post by timothy_duncan on 2006-11-24
Hi all,

i've got the same adsl modem, a dlink dsl-302g.  any help on how to connect on internet..  it seems that dapper is not detecting my ethernet card.  i already did sudo pppoeconf and it says that no working ethernet card is detected.  

HymntoLife suggested i do a lspci, im posting the results here as well, in the hope that someone out there could shed light and give a solution.  here is it:

0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host Bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP Bridge (rev 03)
0000:00:04.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:04.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
0000:00:04.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:04.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0c.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
0000:01:00.0 VGA Compatible controller: Silicon Integrated System [SiS] 86C326
5598/6326 (rev d2)

im running kubuntu 6.06 on a PIII 550MHz old machine

cheers

---

### Post by louieb on 2006-11-24
Linux was born on the Internet. I have never had a problem getting a broadband connection established with any of the half dozen distributions tried. 
Just out of curiosity why don't you try the Knoppix or Dam Small Linux live CD. Both of them have excellent hardware detection.
Most ISP's use DHCP  and Ubuntu or any other Linux should pick up on that and connect automatically. 
Your ISP may have you set up to use a static IP. 
See if the computer is talking to the modem. For example if I enter 192.168.0.1 in the address bar of the browser, my modem responds with a page showing the state of my connection. Your modem address may be different check the documentation.
If so then the problem between the modem and your ISP. 
In this case you will need to contact your ISP for the IP address, subnet mask, and maybe gateway address.

---

### Post by timothy_duncan on 2006-11-25
ive had no problem with my modem when im using xp on a different machine..  it seems that the ethernet card is not being detected..  ](*,) 

any help please

---

### Post by louieb on 2006-11-26
> **timothy_duncan said:**
> ive had no problem with my modem when im using xp on a different machine..  it seems that the ethernet card is not being detected..  ](*,) 

any help please
Try the Knoppix or Dam Small Linux live CD. Both of them have excellent hardware detection.
If one of those succeeds.  
Run lsmod and see what module was loaded to get your network card up and running.
At this point I am at a lost as to how to have Ubuntu use the same module. I belive it is the modprobe command, but I have never had a need to use it.

---

