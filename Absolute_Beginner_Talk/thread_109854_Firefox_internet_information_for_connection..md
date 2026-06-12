---
title: "Firefox internet information for connection."
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by Shalaw on 2005-12-29
I have firefox on my computer (Windows) can I just take that information and get my Ubuntu firefox on the same internet connection?
Are there any Ubuntu servers in New Brunswick Canada?

---

### Post by TeeAhr1 on 2005-12-29
I'm afraid I don't understand the question.  Are you having problems connecting to the net in Ubuntu?  Or are you trying to transfer your Firefox settings (plugins, bookmarks, etc.)?  Both?

---

### Post by Shalaw on 2005-12-30
I'm trying to connect to the internet.  This computer I'm on is running windows but the one that I will have to work with is a Compaq Presario
1600.  The other thing is that the computer line my husband needs to work on is a high speed line.:( 
I have a non-long distance line that can connect to the internet by dialing a local number, and I thought I'd be able to get on the internet that way but I can't find out domain, and other things asked for on the Terminal Server Client.  The internet company doesn't know what to think of Ubuntu :???: and hasn't given me any information that I can use to connect to the internet.:(

---

### Post by thekiller on 2005-12-30
if your only concern is to connect to the internet on your compaq which I assume runs Ubuntu, then u only need to plug the line into the laptop and then if your ethernet device is recognized as 'eth0' then just do :

sudo dhclient3 eth0

In case eth0 is not, then look into the output of ifconfig.

---

### Post by alinuxfan on 2005-12-30
the the presario a laptop? if it is a desktop and it has an open PCI slot you can install a second NIC and aif you have a switch (shouldn't be too expensive and run the cat5 to your computer from the net and then other card to a switch and the switch to your other computer
This is how my wife and I do it
I use firestarter now which is so much easier than when i used to configure it manually from tldp website
and they don't have to be the same operating system either....my wife runs winME until I can get her to make the switch
that way you are both on the high speed connection and so long as you are only doing what you would have done with the dialup you won't be stealing much bandwidth

Just an idea and just my 2 cents, but i find it cheaper than going out and buying a router, pluce it is fun to say my linux box is my router.
Ihave been doing it for about 3yrsnow

edit: if it is a laptop...forget my drunken ramblings...

---

### Post by prizrak on 2005-12-30
It is a laptop. What you need to do is hook up your DialUp networking in the network manager. Click on System>Administration>Networking, there you will see the connections tab (it opens up to it) and you should have "Modem connection" which is not configured by default. Click on it then click "Properties" on the right side you will get a bunch of options to enter. Enter w/e is needed. 
I have to warn you though, Ubuntu is a broadband distro since Synaptics works through the net so I suggest getting a router so you can share the high speed connection with your husband.

---

