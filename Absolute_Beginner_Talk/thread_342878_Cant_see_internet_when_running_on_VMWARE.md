---
title: "Cant see internet when running on VMWARE"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by UBNUB on 2007-01-20
I am a wary newbie that prefers to really kick the tires before doing anything drastic to my Windows XP installation or setting up a dual boot.  

I originally downloaded the live CD and tried that.  It came up although it did not recognize all my USB devices.  I tried to get help on that here and failed.  I was going to give up on Linux and then someone suggested I try running Ubuntu on a virtual machine. 

Consequently, I downloaded the VMware player and the UBUNTU 6.10 VMWare Appliance.  
Everything was run "out of the box", with no attempt at any twiddling with knobs and buttons or other settings.  I succeeded in getting Ubuntu to load and run.  However, when I clicked on the Help Icon and tried to go to the forums, Firefox gave me a "Server not found" error.

My Win XP PC is a DHCP client to my router and thence to my DSL modem (the router handles the SBC DSL PPOE business).  I am submitting this question in a Windows XP session, having temporarily switched back from the VMWare/Ubuntu session.  There is, thus, no questioning the fact that I can (in Win XP) hit the internet successfully.  Still, the instance of Ubuntu running under VMWare does not connect successfully.  The problem would appear to be somewhere in VMWare and/or Ubuntu and their setup.

I know absolutely nothing about Linux, VMWare, or communications (I think that IP has something to do with bodily functions).  I looked under system/administration and it said I had a DHCP connection that was automatically configured.  I looked in network tools and it was mostly incomprehensible.  I did, however, see that it said that my network device was a "Loopback interface".

I am pretty much dead in the water here (although, thank God, my Win XP still works.  If someone were to ask me at this moment whether I would go with Linux I would in all honesty have to say "not at this time".

---

### Post by iluminate on 2007-01-20
Hi I do not know if I can help you, but I am running VMWare for Linux to be able to run XP.
I think there is a setting called NAT in Vmware...connect with NAT and it should solve the problem I think....

---

### Post by burek on 2007-01-20
default installation for vmware 

next next next next ... 
and it ll work the eth0

it s indeed a kind of nat

---

### Post by UBNUB on 2007-01-21
Tried setting the ethernet from bridged to NAT (and also tried, for the hell of it, host only).  None of these settings seemed to make any difference.  Still unable to connect.

I downloaded another VMWare appliiance, the Browser appliance.  That is a Ubuntu 5.10 version with Firefox as the only application.

This one worked (the ethernet setting was NAT).  From this, I might conclude that the Ubuntu 6.10 VMWare appliance is probably broken in some fashion, since it did not work out of the box, whereas the 5.10 did work out of the box (both on the same machine).

Has anyone had any experience running the Ubuntu 6.10 appliance under VMWare on Win XP SP2?  The browser appliance (5.10) is considerably stripped down and, I suspect, is nowhere near as capable as 6.10 in terms of OS capability and applications offered.  I am really curious about Ubuntu 6.10 but it seems to keep trying to hold me at bay.

UPDATE:  I downloaded yet another VMWare Applianc, this one for Ubuntu 6.06.  Same issue as with 6.10.  So, to recap:
Host machine = WIN XP SP2 as DHCP client to Belkin Router and, thence, to DSL Modem
VMWare Player V1.02
"Appliances":
 - Ubuntu 6.10 - no internet, no sound
 - Ubuntu 6.06 - no internet, no sound
 - Ubuntu 5.10 - internet and sound both work (no other apps on the "appliance")

So how did Ubuntu get it right way back with 5.10 and miss it on the 6.06 and 6.10 (The "Appliances" were the only thing that changed - host and VM Player and Router and Soundcard all remained the same.  Methinks the "Appliances" are at fault, but I do not have (the money for) the VMWare Workstation, which would allow me to do my own install ("Appliance")

---

### Post by UBNUB on 2007-01-22
Big DOH!  I realized the problem was due to my router firewall having MAC address filtering set on.  Once I added the generated MAC address (from the VMWare configuration file) to my router, successful connection ensued.

Close this.

---

