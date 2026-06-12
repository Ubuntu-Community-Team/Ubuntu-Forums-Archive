---
title: "im almost there (internet) need your help please"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by fanny on 2007-03-07
still need your help to connect through pppoe. 
somehow after couple of times i tried with this guide [http://ubuntuforums.org/showthread.php?t=183062](http://ubuntuforums.org/showthread.php?t=183062)    i had success to get: "sudo apt-get install build essential " but on the second step i was stuck the terminal gave me a message that there is  faliure . i tried also this guide: [http://www.ubuntux.org/how-to-install-broadband-adsl-pppoe-client-rp-pppoe](http://www.ubuntux.org/how-to-install-broadband-adsl-pppoe-client-rp-pppoe) and also have the same problem.
if im going : system>administration>networking  i see that my router\modem is detected but my   the computer cant recognized my modem. 
i ping to 10.0.0.138 and it seems that there is a communication ( it opens a web page with a place to put user name and password ). 
please help me i need to solve this problem .

---

### Post by endtroducing on 2007-03-07
What is your setup in terms of xdsl modem and router?

E

---

### Post by gwpritch on 2007-03-07
ok..need a bit more information. Tell us about your network setup.  Are you connecting to the internet via your router? If so you should probably not need an other software...ie rp-pppoe. I am assuming the login screen is where you log into your routers configuration setup? From here you should be able to configure your internet connection.

---

### Post by garybrlow on 2007-03-07
You don't really need to install the Roaring Penguin ADSL PPPOE dialer. Ubuntu already has something simpler and similar built in. Just run via the terminal using "sudo pppoeconf" w/o the quotation marks and it will bring up the PPPoE configuration wizard. It will automatically try to detect your DSL  modem and ask for for information like ISP account details etc. This works every time if your DSL connection is via PPPoE (LAN Card to modem connection) which is common. If its PPPoA (USB to modem connection) well its another story, you may have to check, the model, and make plus compile drivers etc. Post your type of connection, modem brand. make and model.


Cheers!!! :)

GaryBrlow :biggrin:

---

### Post by fanny on 2007-03-07
i did already the pppoeconf process its not solving the problem. 
my modem is adsl modem/router: eth-aztech  dsl 600e.
what is the login screen ? 
 i saw many people with the same problem. i belive theres most be a solution for that.

---

### Post by annda on 2007-03-07
if i understand you correctly, your router has an integrated modem - that means that all connection settings are stored in the integrated modem. it should connect to internet after being switched on. you do not need pppoe, the modem takes care of that - or at least it should (username and password for the WAN connection supplied by your ISP).

enter Admin as your username and Admin as password at the login screen (i found this info here: [http://www.petri.co.il/forums/showthread.php?t=4509](http://www.petri.co.il/forums/showthread.php?t=4509)) and see what settings are available.

---

### Post by fanny on 2007-03-07
the link you gave is exactly the modem i have and also talking about the same provider ( bezeq -the telephone monopol in israel). yes it is a integrated modem. 
actually i didnt understand at all what you are trying to say and how does it help me to connect the internet via ubuntu?
thnks!

---

### Post by annda on 2007-03-07
i can only tell you how i do it with a modem/router and hope it's similar for you.

first, the modem/router is connected to my computer by a LAN cable. since the modem is "inside" the router, my computer doesn't need to "talk to" the modem. the modem and router communicate with one another: the modem connects to the internet, passes all connections to the router, and the router passes all connections to the computer.

so i need to setup the modem (this is your only interaction with the modem). i open my browser, put the IP address of the router (it is the man-in-between). in my case it is 198........ and for you it's 10............. (some numbers from the forums above).

i login to the router using default data (admin/admin) and see a lot of configuration options. i go to WAN connection and fill in the form with the username and passworg i got from my ISP when they sent me the hardware. then i save the settings. look in your manual - some routers will require you to go to some sort of command center and save configuration. (it's different for every router, so you will need to consult the manual).

after that, when i restart the router. in ubuntu i go to system > administration > network and enable/activate and configure my wired connection. i choose automatic dhcp.

some systems need to be rebooted after that. and i am online!

i hope it works for you too. if not, post back and tells us at which step exactly you have a problem.

OOPS! i just realized (i am slow today) that you are already connected, because you are able to post here. are you using the same hardware under windows? if so, your modem/router is already configured. all you need to do is the last step.

---

### Post by fanny on 2007-03-08
still doesnt work. but.................. sometimes ,somehow the internet is working and i can surf its not something that i do its just happened.

---

### Post by garybrlow on 2007-03-09
hmm you might be having ISP/Telco problems or the networking configuration via modem may not be set properly. If the modem is used as a router, permissions and firewall rules need to be set correctly to have proper connection. Am not really sure if that modem of yours can be set to act as a bridge mode (non routing mode) instead as a router it should work immediately after supplying your account credentials and dialing in using pppoeconf. :)

Edit:
According to the manufacturer's website, your modem is capable of both bridge mode and routing mode. The default mode is Bridge Mode so no need to set rules etc. It should connect with no problems given the correct dial-in info unless there are ISP/Telco connection problems like bandwidth shortage, frequent disconnections, and bottle necks due to too little bandwidth serviced to an overloaded line to customer ratio or distance limitations from the service stations. This is a common practice among DSL providers the world over. I am currently suffering from this kind of service scheme. This may not be your kind of problem though, but it helps to check if your DSL Provider is not having problems. 


Cheers!!! :P


GaryBrlow :biggrin:

---

