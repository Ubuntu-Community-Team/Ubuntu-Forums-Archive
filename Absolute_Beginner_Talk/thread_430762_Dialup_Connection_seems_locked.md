---
title: "Dialup Connection seems locked"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by edwardLS on 2007-05-02
Yeah, I know - I should have Broadband, but dialup is the only affordable option I currently have.  Installed Dapper Drake on an Intel platform using a hardware (USRobotics/RS-232) modem.  System is dual-boot, and the modem and system works properly in XP.  Using System->Administration->Networking I am able to see, and detect, the modem.  I have entered the Phone number of my ISP, my logon ID and Password.  When I activate the Modem Network, I can hear the modem dial out, I can hear the host modem and my modem negotiate, and the lights on the external modem indicate that I am connected.  However, it seems that I am unable the send and receive data.

In Synaptic Package Manager, I attempt to "Reload" the repositories database but no Rx/Tx activity light appear on the modem.  No repositories are reloaded, and eventually I can see that downloading each of the repositories has failed.

Is there some "lock" or such device in the OS which is blocking the system from communicating with the ISP?  I have had Dapper on a different system with a different hardware modem and my connection was perfect.  On the installation which don't work  I used the 'alternate' CD rather than the 'desktop' CD - if that matters.

---

### Post by Bartender on 2007-05-03
How do you have the little switches on back set up?  On mine, #3, 5, and 8 are down.

Have you tried setting up Evolution or Thunderbird?  I wonder if you could send/receive email.  

If the modem's dialing and you hear it negotiating then it makes me think that Ubuntu is cooperating with the modem and the problem lies elsewhere.  I wonder if it's something relatively simple like your username is supposed to be "johndoe@isp.com" or if it's supposed to be just "johndoe"?

---

### Post by edwardLS on 2007-05-04
Thanks for the information that you provided in your post.  I have solved (worked around) the problem and have everything working correctly now.  Remember that I did the installation with the Ubuntun (Dapper) Alternate CD.  I have been playing with Dapper since October 2006, and have installed, re-installed, and in general been kicking the tires.  In all previous cases, I used the Ubuntu (Dapper) Desktop CD, and had not problem whatsoever.
With the Alternate CD installation, I did also try using the browser to various URL's which I routinely use.  No joy.  In the dialing and connection I see the Tx and Rx LED flash in what I believe is the exchange of my user ID and password.  I have checked, and double checked the ID and password, including the case.  In every case beyond Login/Password, I see no Tx/Rx LED activity in Synaptic, or Browser.  It's as though some lock is set, or I don't have permission to use the dialup network.
I then removed the Alternate CD installation and did the same installation (Drive, Partitions, etc) using the Desktop CD.  Changing absolutely nothing, I enabled and configured the Modem in System -> Administration -> Networking.  I then Activated the connection, and did a successful Reload in Synaptic Package Manager.  I have used the browser successfully also, and have had no problem with the dialup since installing with the Desktop CD.  
I have not been able to check the switches since I am at work, and the modem is at home.  I am employing a strategy of "Download at work (Broadband), Install at home (Dialup)" of the updates and any new packages that I want to load.
Thanks again for your post.
Ed

---

