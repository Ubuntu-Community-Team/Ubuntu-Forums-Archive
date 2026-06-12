---
title: "roaming mode"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by ghostcrab on 2007-08-29
hey  everyone I have a question also I seen the Ubuntu Book and the Ubuntu Unleashed they look EXTREMELY helpful I'm buying them this weekend but anyway I'm on a wireless N works great with ndiswraper.  What mode is better (roaming mode or none roaming mode)?

thank you

---

### Post by kevdog on 2007-08-29
The term better doesnt really apply.  With Roaming mode the card will search for available networks in the area and allow you to connect to these networks.  No roaming mode means the card will not look for other networks, and manual configuration to connect to a network either needs to be done through the nm-GUI or in the /etc/network/interfaces file.  This is useful if you want to set up static IPs.  Usually roaming implies dhcp.

---

### Post by maljaros on 2008-03-29
Just learning the fundamentals of Networking, so had a look at my Network Settings (Gutsy 7.10) and found that Eth0 was set to Roaming Mode. 
My router manual says that I should use DHCP, which is an alternative to Roaming Mode in Network Settings.    
According to the posts and wikis I could find, Roaming Mode relates only to WiFi connections, which my computer does not have.  
Also, some of the posts relating to Network problems recommend disabling Roaming Mode,  Is there any reason why I should/not do this?

---

### Post by maljaros on 2008-03-29
Apology - I think my last post was incorrect.  Roaming Mode is not specifically an alternative to DHCP, but if I check the Roaming Mode tick box in th GUI then the DHCP section greys out.  I suspect I should RTFM, and would appreciate some guidance on where best to look for the answer.

---

