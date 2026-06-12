---
title: "total newbie, need help setting up internet"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by benbasche on 2006-05-09
i recently intalled ubuntu on my emachines m2105 laptop

i have been using windows xp and a netgear 802.11b wireless card to connect to my router 

now i want to know how to get internet on my ubuntu and start using web services

could someone please take me thorugh the steps it would be greatly apprecieated

---

### Post by fake123 on 2006-05-09
i am afraid that emachines hardware is anti-linux
emachines signed a contract with microsoft so now all of their hardware NEEDS windows
you are going to have to buy a new wireless card

---

### Post by benbasche on 2006-05-09
how about a hard wire i have one going to this desktop

---

### Post by benbasche on 2006-05-09
an ethernet cable

---

### Post by fake123 on 2006-05-09
im sorry i was misinformed
please disregard my above post

but yeah the ethernet cable should work fine

---

### Post by benbasche on 2006-05-09
okay does anyone nkow how i could do this plesae!!!

---

### Post by benbasche on 2006-05-09
yeah i plugged it in but im totally newbie at this how would i configure it to connect and stuff

---

### Post by RavenOfOdin on 2006-05-09
Try this:

Go into System > Administration > Network.
Then you'll see a window with the available interfaces and a notice as to whether or not they are configured. 
If you see your wireless (this should be marked as either wlan0 or ra0 depending on your set up, or even eth1 with some cards - and it will probably say "Wireless network" above itself)  click it so its highlighted and then edit its properties. 
For each value put as follows:
ESSID: Whatever your access point network is named.
Key type: This is a drop down with the two values "Plain" and "Hexadecimal", select "Plain" if you're not sure what to use.
If you selected DHCP (Dynamic Host Configuration Protocol) you don't need to worry about the boxes below.

Then, hit "OK" to go out of that box and go right tab by tab until you see "Search Domains" - this is where you put the domain name of your access provider. The same goes for "DNS servers" which should be on the same tab below "Search Domains."

After that, go right another tab to "gateway/aliases" and add the gateway for your access provider. Give it a catchy name like "Wireless."

That should be all the steps you need, and if you have trouble with those just post back here.

@fake123: It IS possible to add this NIC, but the system its being added on will need the ndiswrapper module.

Go into console (Which should be accessible from Applications > Accessories if you're using Ubuntu, or K Menu > System if you're using Kubuntu) then type in 

> 
sudo modprobe ndiswrapper


That should get you started.

---

### Post by benbasche on 2006-05-09
okay, let me try this. i gotta u nplug it from this computer ill get back to you if i hvae problems

---

### Post by benbasche on 2006-05-09
okay, right now i have the internet working with the cable

i went to network settings and selected that dhcp or whatever and it figured everything else out itself

now when i tried without the cable and used the card, i didnt see one of the conenctionsnamed wireless conection...

---

### Post by RavenOfOdin on 2006-05-09
[QUOTE=benbasche]okay, right now i have the internet working with the cable

i went to network settings and selected that dhcp or whatever and it figured everything else out itself

now when i tried without the cable and used the card, i didnt see one of the conenctionsnamed wireless conection...[/QUOTE]

Does your wireless have USB capability?

If so . . . "Without the ethernet cable" usually means that you have a bad USB port somewhere, which is a hardware issue. Try plugging your wireless into a different port.

I had a bad USB port way back. . .took that hardware back and got a PCI card. . .worked fine.

---

### Post by benbasche on 2006-05-09
[QUOTE=RavenOfOdin]Does your wireless have USB capability?

If so . . . "Without the ethernet cable" usually means that you have a bad USB port somewhere, which is a hardware issue. Try plugging your wireless into a different port.

I had a bad USB port way back. . .took that hardware back and got a PCI card. . .worked fine.[/QUOTE]

[QUOTE=benbasche]how about a hard wire i have one going to this desktop[/QUOTE]

yeah... it is a pci card

---

### Post by RavenOfOdin on 2006-05-09
What's the model number?

---

### Post by benbasche on 2006-05-09
ma521 32 bit cardbus 802.11 b netgear

---

### Post by benbasche on 2006-05-10
anyone??

---

### Post by benbasche on 2006-05-10
i need help!!!!

---

### Post by Papa-san on 2006-05-10
OK...I don't have netgear, but I had good luck setting up my wireless with the 'How To' in my signature below that is named wireless. The bcmxx, won't help you, but wireless and ndiswrapper will... Just go through from the beginning, check all of your hardware, etc. Please, also post the results from your terminal...

---

### Post by benbasche on 2006-05-10
problem with commands with sudo

whenver i do anything with sudo

it asks for a pssword but doesnt let me type anything just has a blinking cursor

---

### Post by Jay_Dogg on 2006-05-10
You can't see the password(safety, I think), just type it and press enter.

That should do it.

---

