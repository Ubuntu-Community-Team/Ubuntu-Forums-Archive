---
title: "is it working?"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by chrluc on 2006-02-20
hello all... have  question... I have a trendnet tew-226pc wifi card and founs this thread [http://www.ubuntuforums.org/showthread.php?t=112960&highlight=tew-226pc](http://www.ubuntuforums.org/showthread.php?t=112960&highlight=tew-226pc) and fallowed the instructions and it seemed to work (no errors) but where do I go next? I went to system, administration, and networking and the card is not listed, how do I know if it is working? 
thanks

---

### Post by anirban.sam on 2006-02-20
try pinging localhost

---

### Post by chrluc on 2006-02-20
sorry, how do I do that?

---

### Post by earobinson on 2006-02-20
```
 ping localhost 
```

you can type that in the terminal, bring up the terminal using alt + f12 (I think)

---

### Post by cronholio on 2006-02-20
Applications->Accessories-> Terminal

Enter "ping localhost".

---

### Post by chrluc on 2006-02-20
I did like you said and am now up to icmp_seq=369 so I guess it did not work what di I do now?

---

### Post by chrluc on 2006-02-20
I did ndiswrapper -L and got installed ndis drivers:
net 8180 invalid driver!
which I believe is telling me that it is not working but everything is the same as tthe other post the card is the tew-226pc and I'm running ubuntu 5.10.

please help I have to get 30 laptops up and running

---

### Post by cronholio on 2006-02-20
It means it worked perfectly. Press Ctrl-C to stop it.

In the networking dialog you should see "Ethernet connection". Do you?

EDIT: D'oh! I mean Wireless Connection.

---

### Post by carlosqueso on 2006-02-20
IIRC, pinging onesself uses the internal loopback interface, not a wireless one. 

chrluc, something went wrong with your driver install.  First type ```
ndiswrapper -e net8180
``` or whatever the name of the driver was.  Then type ```
lspci
``` and post the output.

---

### Post by chrluc on 2006-02-20
I'm not connected to the internet... posting this on my treo/phone is there something I should look for in the output?

---

### Post by chrluc on 2006-02-20
I do see 0000:02:00.0 Ethernet controller: Realtec Semicondutor Co., Ltd. RTL8180L 802.11b MAC (rev 20)

---

### Post by carlosqueso on 2006-02-20
yup...you have the same one as me..... [http://www.ubuntuforums.org/showthread.php?t=96989](http://www.ubuntuforums.org/showthread.php?t=96989)  is what I did to get it working.  If you need more help...post back and I'll try.

---

### Post by chrluc on 2006-02-20
those were the instructions I followed ... and here I am still stuck w/ invalid drivers any other Ideas? in the terminal I didn get any errors. but no conformation either. the card should be in the slot while doing this right. and will it appear in networking as an eathernet... because is is not.

---

### Post by carlosqueso on 2006-02-20
Yes, the card should be in the slot.   A couple of things to check.  First, remove the invalid driver with ```
sudo ndiswrapper -e NET8180
```  second, make sure that you are in the directory with the windows driver and that the .sys file is there.  Third, remember that linux is case-sensitive, so make sure you  entered it in exactly like the howto.  If everything is done correctly ```
ndiswrapper -l
``` will yeild something like "driver present, hardware present"

---

### Post by chrluc on 2006-02-20
how do I know if it has been removed. I did what you said to remove it and tried to reinstall it and it says it is allready installed. by the way the sys file was not on the system... that has to be the problem

---

### Post by chrluc on 2006-02-20
ok I got driver present hardware present... should I expect to see it in system- networking. because it is not there.

---

### Post by carlosqueso on 2006-02-20
I would think so....did you type ```
sudo modprobe ndiswrapper
``` after you saw driver and hardware both present?  If you have....try typing ```
ifconfig
``` to see if you can see it.

---

### Post by chrluc on 2006-02-20
that was the problem! the sudo ndiswrapper -m gave some type of error? so... now my nextquestion how do i get two computers to see each other (1 windows 2000 and 1 ubuntu) my two windows systems see each other but they cannot see the ubuntu or the ubuntu see the windows.

---

