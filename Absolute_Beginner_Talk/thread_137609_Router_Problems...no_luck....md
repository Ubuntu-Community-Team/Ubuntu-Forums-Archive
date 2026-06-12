---
title: "Router Problems...no luck..."
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by ConkreteDisko on 2006-02-28
Hello everybody. I am incredibly new to this. I just finished installing ubuntu maybe 40 minutes ago. I'm having a similar problem to what looks to be alot of people out there. I have a Intel Pentium 3 500mhz PC with 256 ram and all that. (yeah I know, it's old) and I'm using the D-Link DWL-G122 802.11g (notice the G) wireless USB adapter. Now, after searching for awhile, I have yet to find a solution. So does anyone out there now how to get this thing running? Keeping in mind I don't know alot of the commands, so it will have to be a very step by step thing, if you dont mind. My computer does not have windows, my harddrive is 120 gigs, with just ubuntu on it. So yeah, could someone please please please help me out? I'm dying without the internet!! Thank you in advance.

---

### Post by Jimmey on 2006-02-28
I'll assume that you're a begginner to Linux, Gnome, and Ubuntu in general.

First, you need to activate the apropriate Network Interface Card ( NIC as it's often called.. ). To do this, click on "System" >> "Administration" >> "Networking".

It should prompt you for your password.

From what I gather, you're using a USB WIRELESS device.. And so, again, I'll assume that you need to configure "ra0". To do this, click on "Wireless connection", and click "Properties". Then click "Enable this connection".

Select your wireless LAN's name. ( Mine's linksys, because my router's made by them. )

Unless you know better, you're able to leave the connection settings to "DHCP".

Then, once finished, click "Ok". It will return you to the previous screen, at which point you can again select your "Wireless", and then click "Activate". The final step is, from the drop down box marked "Default gateway device", select "ra0".

Then click "Ok".

With any luck, you should then have the internet. Without it, you might still have the internet. ( lol? )

EDIT: 
I've reviewed your post. It might not be ra0 that needs to be configured, but eth0. Try both?

---

### Post by ConkreteDisko on 2006-02-28
Yes, i am a complete newb. infact im so new to this i havent even had it for more than 3 hours. i did the first step, and when i clicked on  "networking" or whatever it was, nothing happened, i got the little spinny mouse icon thingy, like the loading symbol. then it went back to the normal mouse cursor and nothing happened..

---

### Post by Jimmey on 2006-02-28
Strange.

I guess

> sudo ifup ra0, in the terminal, is worth a shot.

---

### Post by dvarsam on 2006-02-28
What "Jimmey" ment, is from the Ubuntu menu, select:

Applications\Accessories\Terminal

Then type:

sudo ifup ra0

Select the output you will get (from the Menu, select "Edit\Copy") & paste it here in this Forum.

Good Luck!

---

