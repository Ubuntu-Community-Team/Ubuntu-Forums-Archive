---
title: "Need Help With Broad Band"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by hvignesh on 2005-11-28
Hi Ubuntu Friends

---

### Post by tikal26 on 2005-11-28
hey you need to give us more info. Like who is your provider and whether you dualboot. just more info

---

### Post by hvignesh on 2005-11-29
hi 

         i have an adsl modem.. and i think my ethernet card was detected by ubuntu.. bcox i could c that the acitvate and deactivate button is working and my ISP is from india.. and the username will look like this sam@dataone and some user defined password.. and i could c different ip address when ever i log into my windows and connect to broadband so pls help me... pls let me know if u need some more info to help me...

---

### Post by Robgould on 2005-11-29
what you see from windows has no bearing on Ubuntu.  When you log into Ubuntu select system -->  administration --> networking.  Select your ethernet card from the menu, and then click the properties button button.  choose to enable the connection and give DHCP info.  Click ok, then click activate.  That should get you connected.  I hope this helps you.

---

### Post by Robgould on 2005-11-30
Have you gotten going?

---

### Post by hvignesh on 2005-12-01
hey no... 

         wat am i supposed to do with DHCP.. i dont know wat to enter there ... tell me something more about dhcp... pls dont mistake me.. i am new to ubuntu... pls guide me...

---

### Post by ed_d on 2005-12-01
You should have gotten something from your ISP as far as IP addresses and gateways. You should be able to just select dhcp, either restart the daemon, or reboot and be good to go.

---

### Post by Robgould on 2005-12-01
Does your ISP offer technical support?

---

### Post by hvignesh on 2005-12-02
no.. my ISP is not providing any technical support.. they jus gave me the user name password and the site where am i supposed to check my acount info that is usage of the broadband.. and they gave me an ADSL modem and a device driver for that modem .. thats all they gave... so i am not sure of wat to enter in the DHCP IP address and gateway... so pls try helping me......

---

### Post by Robgould on 2005-12-02
you need to know from them.  I have no idea what their IP address is.  You need to know the IP address of their DHCP and Gateway servers.

---

### Post by hvignesh on 2005-12-02
r u sure .??? will they provide me???

---

### Post by hvignesh on 2005-12-02
hey ok

          i got the ip address and gateway from the providers.. jus now i called them and got them.. now help me out wat am i supposed to do...

---

### Post by Robgould on 2005-12-02
I am at work now.....I won't be back to ubuntu for several hours....I can't go click by click off memory.  If you don't have an answer by then, I will write the instructions for you.

---

### Post by hvignesh on 2005-12-02
hey roubgauld pls pls.. some how help me man.. i got totally frustrated with windows.. and i am still trying to do the config work with ubuntu .. but i am not able to make it.. pls take ur own time and some how help me in this... i will be thankful to u if u can help me...

---

### Post by Robgould on 2005-12-02
I just won't know the answer until I get home.  I can give you just general idea now.  Did your ISP provide you with a router?  If so, you need to configure it with the IP address your provider gave you, and set it up to act like a DHCP server.  Then you should be able to activate your connection from withun Ubuntu.  I don't know what kind of router or modem you have.  Does you connection work from windows?
 
If so goto start --> run --> type cmd and enter
 
type ipconfig /all
 
This should give you all your connection information.  
 
Also if you can connect from windows that means your router is set up correctly and you issue is within ubuntu.  I am assuming that you can not connect with windows either.  
 
Did you get a manual with your router?  That is the key.  Once you have something that can give ubuntu an IP address with DHCP, it will be able to connect.
 
The other option is to use a static address.  If you are dual booting and can connect from windows, get that IP address (ipconfig /all) and then boot to ubuntu and try the same address.
 
I wish I could be more help.

---

### Post by hvignesh on 2005-12-03
i am browsing from my house only everyday and that too from windows XP it is able to auto detect my modem and i normall install my ethernet driver explicitly from windows and after that my LAN will work.... i have ADSL (Async Digital subsrciber link) modem .. and i dont know wat is  a router.. and this is wat i am given.. 


i dont have any problem with windows.. it is working perfectly.. and ipconfig/all is showing everything..  and i have attached the jpeg file of wat my ipconfig/all is showing.. so with this.. u help me wat am i supposed to do.. and as i have told u that i have got the ip address and gateway from my ISP and if i need to get something more also u let meknow i will ask them.. pls man somehow help me..

---

