---
title: "Configuring Network Card(need help)"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by jon_z on 2005-12-08
Hello,
I just recently have installed Ubuntu.. I got totally fed up with mandriva and switched over to this and love it.  I have only problem, at my school, my TCP-IP settings need to be set to "Obtain an IP address automatically" and my DNS to "Obtain DNS server automatically"  With the configuration for my network adaptor (which is installed as eth0) I cant figure out how to do this.
Any information is greatly appreciated

sincerely, 

Jon Zabron

---

### Post by cwaldbieser on 2005-12-08
[QUOTE=jon_z]Hello,
I just recently have installed Ubuntu.. I got totally fed up with mandriva and switched over to this and love it.  I have only problem, at my school, my TCP-IP settings need to be set to "Obtain an IP address automatically" and my DNS to "Obtain DNS server automatically"  With the configuration for my network adaptor (which is installed as eth0) I cant figure out how to do this.
Any information is greatly appreciated

sincerely, 

Jon Zabron[/QUOTE]
In the terminal type
```

$ sudo dhclient eth0

```
That should cause your card to contact the DHCP server and configure itself.  If that works, you will want to set it up so that happens whenever you boot up.  If you search the Networking forum under Hardware Help, there is a lot of info there on how to set it up permanently.

---

### Post by jon_z on 2005-12-08
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval it used 4,8,9,14,19,7
No DHCPOFFERS recieved.
No working leases in persistent database - sleeping.

you can contact me on AIM sn: stones92886 for quicker communication

---

### Post by jon_z on 2005-12-08
[QUOTE=jon_z]DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval it used 4,8,9,14,19,7
No DHCPOFFERS recieved.
No working leases in persistent database - sleeping.

you can contact me on AIM sn: stones92886 for quicker communication[/QUOTE]

bump

---

### Post by Mr. Electric Wizard on 2005-12-08
Go to System-->Administration-->Networking.
Select your Ethernet card, and then hit the "Activate" button.
Then click on properties.
You should see a check box at the top to "Enable this connection" (or similar).
After that, you can select DHCP.

After you hit OK, everything should be cool.
If you still cannot get your network up, then go back into Networking and see if your "Gateway" is set to eth0.

Let us know if it works.  If it doesn't you might have a bad NIC, or a bad cable...
:KS

---

### Post by jon_z on 2005-12-08
eth0 does not stay enabled as my default gateway.. I hit ok, ubuntu thinks for a bit, it looks like etho is up..I close the network interface, open it back up and default gateway is blank again.  As for the cable and NIC, both work..I have had internet connection up until last night when I installed ubuntu.

---

### Post by Mr. Electric Wizard on 2005-12-08
what kind of card make, model, chipset is it?

---

### Post by jon_z on 2005-12-08
Marvell 88E8001

its built in with my ASUS A8V Deluxe motherboard
*me thinks i might have to use a new flavor of linux for this nic*

---

### Post by ssam on 2005-12-08
try to work through [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643) it might help.

---

### Post by ed_d on 2005-12-08
Wow, that link is awsome, lots of good info there................

Maybe put it as a HOWTO?

---

### Post by jon_z on 2005-12-08
the result of $sudo mii-tool eth0 is
SIOCGMIIPHY on 'eth0' failed; operation not supported..
i.e. eth0 isnt even working, so this flavor of linux doesnt like my nic, anyone got any ideas?

---

### Post by jon_z on 2005-12-09
bump

---

### Post by janrinok on 2005-12-09
No - the response that you got means that mii-tool is not doing what you expected  I get the same answer and my eth0 is working perfectly - in fact, my internet link is through it and it is being used while I write this!.  But I haven't used mii-tool before so I will have to check how it works. Jan

---

### Post by janrinok on 2005-12-09
It seems that you get this error message is your eth0 is already in use - i.e. mii-tool cannot renegotiate with the card because it is already set up and in use.  What do you get if you 'ifconfig eth0'?
Jan

---

### Post by janrinok on 2005-12-09
[http://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=609949](http://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=609949)

This is not the answer to your problem - but it does illustrate that mii-tool does not always do what the user thinks it is doing.  I am not criticising the original advice that  is found here

[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

simply pointing out that what worked for one individual might not always work for others.  Your problem is that your eth0 will not stay activated and all that this command appears to show is that mii-tool can identify _some_ ethernet cards.  Please anyone, correct me if you can but mii-tool seems not to work with a large number of ethernet cards.  Jan

---

