---
title: "printing tcpip"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by clemm on 2006-05-14
I need some help setting up my printer. I can acsess my dlink wireless print server from the web browser. My printer was configured in win XP to print wireless on a tcpip port. I cannot find anyway to print tcpip in ubuntu and I cant seem to get it to print any other way. I have read many other similer posts and tried everything I was capable of. Im new to ubuntu and skills are very limited. Thank You.

---

### Post by rvergara on 2006-05-14
clemm,

You did not send us much info on your set up.

I assume you have your printer connected directly to a print server that is set up with an ip address in your network.

Go to System->administration->printers

Double click on the add a printer icon.

On the new window (cups) select network printer and Jet Direct. enter the print server ip address in the host field, click next, select printer make and model, confirm and print a test page. You should be done if your printer driver was listed. If not, do not worry, come back and report the result to us.

Hope this helps

Ramiro

---

### Post by clemm on 2006-05-15
Hi Thanks for your help. I have tried installing this every way I can think of. It is dlink print server on a dlink wireless router, conected to this computer by lan. It all worked fine in windows.  I can acsess both the print server and the router from the web browser but I cannot make the printer print. My printer is listed in the set up and I dont think this is a driver issue. My wlan led on the router never even blinks. I dont think the data is getting to the print server. I can copy and paste any information you need from print server. I ran a port scan and and I have 515 open printer and 633 open ipp. I cannot get either of them to print. I have tried various ways of entering the ip for example 192.168.0.10 and localhost [Http://192.168.0.10:515](Http://192.168.0.10:515) and hundreds of other combinations. I have also tried cups, win smb and hp print. If you need more information tell me what you need and I will get it for you.
Thank you very much I really appreciate your help! Also I have not installed a firewall yet, so it shouldnt be blocked there, unless Ubuntu has some default thing I dont know about.

---

### Post by rvergara on 2006-05-20
Clemm,

did you create the printer usinfg the jetdirect option?, this should use the port 9100 and it should work with a print server.

Ramiro

---

