---
title: "pb with the internet"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by FuzZy2006 on 2006-06-22
while i use ubuntu sometimes some links don't work, as if the internet would stop working. other times, they work. the most problems i have when i go to login pages or search pages. it a little weird.

---

### Post by kb3hkg on 2006-06-22
how are you connected to the internet?

---

### Post by FuzZy2006 on 2006-06-22
DSL 768 pppoe connection - it requires a pass and user

---

### Post by kb3hkg on 2006-06-22
are you using wireless or just plugged straight in?

---

### Post by FuzZy2006 on 2006-06-23
just plugged in

---

### Post by FuzZy2006 on 2006-06-23
pls help. it is really annoying. while i am updating ubuntu, downloading files or anything that uses the internet, at nearly every 3-4 minutes, internet slows down and stops working ](*,)

---

### Post by kb3hkg on 2006-06-23
try running ifconfig while it is working, and then again once it stops. This may be able to help us narrow down the cause.

---

### Post by FuzZy2006 on 2006-06-27
well, i tried to do that i ran ifconfig but it doesn't just help me, the only think that sometimes changes is that the RX packets and TX packets have errors (0 dropped). When I ran plog it says so: 

Jun 27 21:26:41 fuzzy-desktop pppd[5410]: local  IP address 194.116.169.2
Jun 27 21:26:41 fuzzy-desktop pppd[5410]: remote IP address 86.105.223.178
Jun 27 21:26:41 fuzzy-desktop pppd[5410]: primary   DNS address 86.105.223.178
Jun 27 21:26:41 fuzzy-desktop pppd[5410]: secondary DNS address 81.180.254.157
Jun 27 21:26:43 fuzzy-desktop pppd[3695]: No response to 3 echo-requests
Jun 27 21:26:43 fuzzy-desktop pppd[3695]: Serial link appears to be disconnected.:confused: 
Jun 27 21:26:43 fuzzy-desktop pppd[3695]: Connect time 3.4 minutes.
Jun 27 21:26:43 fuzzy-desktop pppd[3695]: Sent 120 bytes, received 1856 bytes.
Jun 27 21:26:49 fuzzy-desktop pppd[3695]: Connection terminated.
Jun 27 21:26:49 fuzzy-desktop pppd[3695]: Modem hangup:confused: 

sometimes it says that it couldn't receive the ARP adress. :confused: 
Really interesting cos' in windows everything is working jus' fine, i was expecting more from ubuntu.  :-k 
Pls help, i need internet](*,)

---

### Post by WADemosthenes on 2006-06-27
This happened to me in firefox a while ago when I was trying out DSL linux.  Was it in firefox for you?  If so, maybe it has something to do with firefox.

---

### Post by FuzZy2006 on 2006-06-27
i oppened firefox before to try the internet connection but i don't think this is a pb:confused: ](*,)

---

### Post by FuzZy2006 on 2006-06-27
or is it?

---

### Post by FuzZy2006 on 2006-06-27
well even if i don't start firefox i have the same pb, internet isn't working. the error is Serial link appears to be disconnected or something that it can't get the ARP proxy adress. Pls help

---

### Post by FuzZy2006 on 2006-06-28
solved, using rp-pppoe 3.8

---

### Post by hatti_ajit on 2007-05-17
Thanks Fuzzy, I too had the problem of frequent net disconnection. I installed rp-pppoe 3.8.
Just for the sake of comprehansion, Im pasting the steps to install rp-pppoe 3.8


 How to install Broadband ADSL/PPPoE Client (RP-PPPoE)
---------------------------------------------------------------------------------
* do the following :

    wget -c [http://easylinux.info/uploads/rp-pppoe-3.6.tar.gz](http://easylinux.info/uploads/rp-pppoe-3.6.tar.gz)
    sudo tar zxvf rp-pppoe-3.6.tar.gz -C /opt/
    sudo chown -R root:root /opt/rp-pppoe-3.6/
    gksudo gedit /usr/share/applications/RP-PPPoE.desktop

* Insert the following lines into the new file 

[Desktop Entry]
Name=RP-PPPoE
Comment=RP-PPPoE
Exec=gksudo /opt/rp-pppoe-3.6/go-gui
Icon=pppoeconf.xpm
Terminal=false
Type=Application
Categories=Application;Network;

* Save the edited file 


source : [http://ubuntuguide.org/wiki/Dapper#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29)

---

