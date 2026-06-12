---
title: "how do i get connected to internet"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by gagme on 2006-07-05
now normally i would just connect computer up and im connected (windows) .but im perplexed as what to do with ubuntu i cant connect do i need to manually do something????

so far i like ubuntu alot

---

### Post by ProjectGod on 2006-07-05
can you give us more information... like what devices you use to connect to the internet? what type of connection you use etc etc.

---

### Post by MaximB on 2006-07-05
I'm sure that the answer to your question is already posted in the forum...
please do a search on the forum about how to connect to the internet.

---

### Post by gagme on 2006-07-05
connecting through comcast using ethernet .Ilooked at alot of posts and none touch upon my problem or my skill level .

now im sure its easy as typing in ip adress but i dont know where to look on windows for that info or even if thats what i do
i got another computer so i can use it to connect and possible copy info from here and enter it in there like ip info etcc.

---

### Post by ProjectGod on 2006-07-05
so youre saying that you've got another computer that's got windows installed and that's on the local "LAN" ok then... if its a windows. it's cinch. in START, SETTINGS, CONTROL panel... there should be a NETWORK connections or something folder...

open it up and go to LAN... right click ... properties... double click the TCP/IP listing... check / record IP addresses... if it's set to dynamic all the better... if not jot down everything. DNS server subnet mask default gateway ...

or you could use the command line in windows to check it faster... 

START> RUN, type "cmd" and enter.

at the command prompt. type:

ipconfig /all

once again note the settings... check if "automatic IP addressing" is enabled... meaning DHCP.

on your ubuntu machine log in, for something simple like this just use GUI... in SYSTEM > ADMINISTRATION > NETWORKING... there should be the ethernet adapter... click on it activate it! put all similar settings as found on your windows machine... if its DHCP enabled... do so on your ubuntu machine. now one thing that's a common recurrance is the DNS... 

from your windows machine log into the router... something like http or [https://192.168.200.1](https://192.168.200.1)... if your not sure one way to determine is to check your windows IP address... if its 10.0.0.2-253 then its highly likely the router's ip is 10.0.0.1... if windows machine is 192.168.0.3 ... highly likely your router is 192.168.0.1... log in using username / password combination... hopefully you have these! :)

check the DNS settings on the router... this DNS server is different to the local DNS server... its acting as a mini proxy so the DNS on this router is actually the public DNS server of your ISP...

you have to set this DNS server also on your ubuntu machine... unlike windows where once it discovers DHCP server everything is setup ... you have to do this step to have connectivity.

hope this helps O:)

---

### Post by gagme on 2006-07-05
I wanted to say thank you very much:cool: 

problem has been solved!!!!!!!!!!!!


all i did was enabled the ethernet adapater and now it works !!!!!!!!
yesssssss!!!!!!!!!!!!!!!!!!!!!!
awesome thank you thank you

---

