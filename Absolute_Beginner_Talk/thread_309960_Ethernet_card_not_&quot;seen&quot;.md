---
title: "Ethernet card not &quot;seen&quot;"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by simon303 on 2006-11-30
i have recently installed Ubuntu on my computer only to find that my ethernet card doesn't work. i have been told that the drivers are there, but the computer just can't "see" the card. it worked fine when i ran windows xp.
does anyone have any ideas?

---

### Post by deadgobby on 2006-11-30
What means of internet mode are you using. Dial up, DSL, or cable modem? Or using a wireless card?

---

### Post by simon303 on 2006-11-30
broadband via a modem (not sure what the technical term is)

---

### Post by Bachstelze on 2006-11-30
@deadgobby > his problem is that the NIC doesn't even appear in *lspci*.

@simon303 > are you sure your NIC is plugged in and working properly (blinking LEDs ?)

---

### Post by LDRoamer on 2006-11-30
Do you mean its not seen at all or just that it isn't working? 

If just not working I might have an idea you can try. When I installed Edgy I wasn't able to connect to the network with my ethernet card unless I opened a terminal window and ran the command "dhclient".  I use DHCP for my network and for some reason DHCP was not working unless I manually invoked it.

I installed network manager and use that to connect to the wired or wireless networks. Network Manager connects to both just fine. Although I didn't try very hard I wasn't able to get dhcp working automatically on my machine. Since I use wireless almost exclusively it wasn't a big issue for me.

In my case I am running Edgy on an old laptop and my ethernet card is a PCMCIA card.

---

### Post by simon303 on 2006-11-30
theres a LED on the back of the ethernet card which is on

---

### Post by simon303 on 2006-11-30
its found the ethernet card
just wont connect to the internet with it

---

