---
title: "Newbie vs ADSL Router + Ubuntu 5.04"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by andrew.46 on 2006-12-14
Hi,

 I hope someone can have the patience to guide me through connecting my computer to an ADSL Router. I confess to being more than a total newbie: I bought a computer today with Ubuntu 5.04 installed today and have only just turned it on :-)

 The computer has a network card and I am hoping to connect it to a D-Link ADSL router that already has a Windows XP computer connected by USB. (Router has a spare / unused ethernet socket.)

 Not wanting to risk the ire of the forum I have searched the threads and I am almost sure that I am after:

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

 But I am not connecting to a modem, I have a network card?

 Please keep it simple for me! I am very excited with this little computer (HP e-Vectra) and am hoping to complete my BA with it!!

         Thanks for your trouble,

                    Andrew

---

### Post by renzokuken on 2006-12-14
well for starters, use the ethernet link for ubuntu, usb modem support is not good.

what type of router/modem are you using (model name / number ?)

if its the right type of modem, you can program the modem to do all the dialing and connections for you and wont have to bother with PPPoE

---

### Post by andrew.46 on 2006-12-14
Hi!

 Thanks for the prompt reply!

> **renzokuken said:**
> well for starters, use the ethernet link for ubuntu, usb modem support is not good.

what type of router/modem are you using (model name / number ?)

if its the right type of modem, you can program the modem to do all the dialing and connections for you and wont have to bother with PPPoE

The modem is a D-Link ADSL router DSL-502T. It has one USB connection (used by my Windows XP computer) and a vacant ethernet spot.

                   Andrew

---

### Post by Chinkostu on 2006-12-14
with my router, i just plugged it in and it was automatically set up. im not sure if you can use the ethernet when the USB is plugged in, but its worth a try.

---

### Post by linuxn00b73 on 2006-12-14
Yeah, I'm not sure you can use both either. You would need a router with more ports for that I'm guessing. I'd try disconnectinting the the USB cable and a restart of the dsl router. Mine just automatically worked also. My theory is that using the USB overides the the Ethernet port.

---

### Post by andrew.46 on 2006-12-15
Hi,

 Well the plot thickens :-) I dug around a little and looked in:

System / Networking /

 And saw two entries, one of which was 'Ethernet Connection' which stated: The interface eth0 is not activated. I 'activated' this and chose DHCP.

 Looking under 'Network Tools' I saw Ping and TraceRoute both of which found [www.google.com](www.google.com). However Firefox (1.0.7) still finds nothing.

 Can anybody guide me with this? I am getting a little frustrated.

                      Andrew

---

### Post by happy-and-lost on 2006-12-15
Life will probably be made a lot easier if you upgrade to Dapper or Edgy. The hardware support is much better!

---

### Post by rich.bradshaw on 2006-12-15
Normally plugging in an ethernet cable automatically works. You shouldn't have to do anything.

Update I would - CD's are free from shipit if you haven't got fast internet.

---

### Post by AndrewB on 2006-12-15
on occasion I've had to point the browser to the router or modem. The modems address should be listed in its manual, or you can google it. Mine is 192.168.1.1

good luck,
Andrew

---

### Post by andrew.46 on 2006-12-15
Hi,

 Thanks for your advice:

> **rich.bradshaw said:**
> Normally plugging in an ethernet cable automatically works. You shouldn't have to do anything.

Update I would - CD's are free from shipit if you haven't got fast internet.

 I have sent a request in for the CDs. Hopefully this will make life easier. Is there a guide somewhere on the forum to upgrading the operating system like this?

          Thanks again,

                 Andrew

---

### Post by happy-and-lost on 2006-12-16
You'll have to do a fresh install over 5.04. It's not hard to do, the graphical LiveCD installer will guide you through it.

Edit: When you do install, I recommend creating a separate /home partition, as a relative newbie I know how easy it is to screw up an install!

---

### Post by andrew.46 on 2006-12-20
Hi,

 Well I guess I am officially frustrated now :(  Despite some of the excellent advice that I have found on these forums I am still faced with no Internet access from this computer / ADSL router / Ubuntu. I downloaded the neweset version of Ubuntu 6.10 but unfortunately the live CD failed, I suspect because I have a 128meg machine. I will try the same with 6.06 when it arrives in the mail.

 Interestingly enough the DSL live cd I downloaded also could not raise the Internet at all through this router, although pronouncing the network card + connection good.

 I recently had to reinstall the router in windows XP. Guess what: 3 minutes work and I am off downloading porn ooops I mean Linux software!!!

 I would be very grateful for any assistance that will stop me from reformatting the drive an installing win 98 on this little machine ](*,) 

                   Andrew

---

### Post by ske1fr on 2006-12-20
Andrew. with a machine having only 128 MB of memory you should try to use Xubuntu, as the XFCE windows manager needs less memory than Gnome and KDE.  Having said that, you should still be able to see something of the router from your computer's web browser running Ubuntu 5.04, by using [http://192.168.1.1](http://192.168.1.1) as a web address.

Activating eth0 and chosing DHCP was a good move.  The fact that you could ping google was good, but the fact that Firefox didn't seem to work is not necessarily a problem - it can be slow to respond when first started.  It will take forever to resolve addresses too until you turn off IPV6 in it - do a search on here for how and why. 

It's some time since I tried 5.04 so I can't comment.  I would strongly recommend you obtain the "alternate" (i.e. non-graphical user interface) Xubuntu Dapper Drake CD and try this, and make sure that your other PC on the USB connection is not connected when you try this.  Xubuntu Dapper works fine on an old 128MB laptop I have, and the version of Firefox it uses is fine.

Good luck.

---

### Post by andrew.46 on 2006-12-20
Hi!!

 Wooooooooooooo hoooooooooooooooooooo!!!!!!! Guess who is typing this from their Ubuntu box??????? I officially forgive Linux for making this a little difficult for me.

 Once I did a little digging I found that the problem was actually one with the DNS settings. I found a specific description of the problem by an employee of my ISP: AAPT in Australia  (good of him since the company does not support Linux) that described my router and gave the correct DNS settings. Typed those in and off I went.

 I have placed these in via System / Administration / Network Settings / DNS although the ISP guy said they are better by manually editing etc/resolv.conf. I guess once I actually find out what that is I shall do it :) 

 I will stick with Ubuntu 5.04 for the moment while I have my training wheels on but definitely Xubuntu alternate install looks like the next step. Now to look at this Synaptic thingy .......

                Thanks to all who gave advice!

                                      Andrew

---

### Post by muximus on 2008-03-14
I too have an adsl router, a d-link dsl 502t. My desktop and laptop are both connected to it, and it works fine. Have never faced a prblem. Maybe in your router settings, the dhcp server is disabled, and if so, you need to configure the network, you know, the gateway, subnet ip etc. I also had a problem with accessing the internet, but that got solved when i copied the dns server info from the config pages of the router, and placed the same dns servers in my linux connection.

Hope that helps

---

