---
title: "Unable to connect to internet or configure firefox"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by DonT on 2006-08-19
Background: I am somewhat hardware literate, but consider myself as a software cripple, thanks to windoze.  I built a PIII machine almost two years ago and am relative successful running XP pro on it - its what I am using right now to address this forum.
  I built another PIII system for my wife and decided to make the move to linux via ubuntu 5.10.  After a couple of false starts, first with hardware/bios configurations, I have ubuntu installed and operational, except I am unable to connect to the internet.

System build/setup:  DFI CM33-TL motherboard
                     PIII 933mhz CPU
                     1GB PC133 memory
                     80GB WD hard drive
                     Lite-On Dvd Burner
The motherboard uses Via chipsets and Realtek on-board 10/100 Lan.

I am connected to the internet using a Speed Stream DSL modem connected to a Linksys cable/dsl router.  My internet provider is TDS Telecom, and officially only supports IE or Netscape, although Mozilla products and others will function.

My only clue do far is that I don't have a green light on my LAN port - it is yellow.  No matter what site I attempt to connect to - after an extended period of time a message appears saying website not found, or words to that effect.  Also, I noted that during loading of ubuntu at boot, it was unable to connect with the ubuntu...clock.

OK, I know this is getting long winded, but I am trying to be complete.

My other computers (don't bring this up with my wife), can use this setup for simutaneous connection/communication with the internet without any problem - same cable - same everything, except they are loaded with (gag) windoze.

I have lost practically any skills I ever had with programing/software (first computer an Apple IIe), so I am quite lost with linux.  In fact, I haven't a clue what my selection during the hard drive setup is, or what the result is because it is very cryptic - what the h*ll is lvm?! etc.

I am assuming (I hate that word!) that I have a configuration problem, or need to install some driver(s).

PLEASE help!  I wish to be cleaned of this windoze affliction!

---

### Post by kombipom on 2006-08-20
Go to System->Administration->Networking type your password when it asks for it and see if there is an ethernet connection listed.  If there is and it is not active, activate it and select eth0 (assuming you only have one network card) as your default gateway device.

Hope that helps.

---

### Post by DonT on 2006-08-20
Hi Kombipom,

Thank you for your reply.

I did as you suggested, and under connections it shows the ethernet connection as "the interface eth0 is active, and, default gateway device:  eth0;
under properties the device is listed as eth0 and the enable box is checked.  Under configuration, DHCP is shown.  By-the-way, my ISP does not use a static IP address.

So, under general/dns/hosts, what do I need?  With my other computers, I have to duplicate my settings in my main system, ie, username/password.  How does that equate to hostname/DNS/hosts?

Thanks much.

---

