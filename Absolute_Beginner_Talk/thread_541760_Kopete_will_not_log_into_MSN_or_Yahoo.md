---
title: "Kopete will not log into MSN or Yahoo"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by NacIK on 2007-09-03
I am having a problem whenever I try to log into any of my accounts through Gaim or Kopete.   It tries to log on for about 10 minutes then puts up an error that it cant log in.   Any ideas?:confused:

---

### Post by nowshining on 2007-09-03
did you make sure in both that all the settings are correct for yahoo
 
in gaim
 
accounts - add/edit
 
if you have a yahoo account setup select it and select at the bottom modify
 
under basic next to protocol make sure Yahoo is in the drop down box and select it.. in screenname input your yahoo accound WITHOUT the @yahoo.com
in password your password...
 
you can click remember password if you'd like so you won't have to retype it in each and everytime...
 
at the bottom click save and I don't use my msn account I may still have so i don't know about that one, but you can try the same thing but with MSN selected in protocol..

---

### Post by wieman01 on 2007-09-03
Running Firestarter and have you configured IP tables manually (firewall)? Then open the respective ports.

---

### Post by nowshining on 2007-09-03
> **wieman01 said:**
> Running Firestarter and have you configured IP tables manually (firewall)? Then open the respective ports.



ah forgot about that if so 




yahoos port is 5050 outbound
MSN is 1863 again outbound

---

### Post by gtdaqua on 2007-09-03
> **nowshining said:**
> ah forgot about that if so 

yahoos port is 5050 outbound
MSN is 1863 again outbound


I think you need to open inbound ports - they will be blocked by default by firewall. Outbound ports are normally open.

---

### Post by wieman01 on 2007-09-03
> **gtdaqua said:**
> I think you need to open inbound ports - they will be blocked by default by firewall. Outbound ports are normally open.
In Feisty all ports are open by default. Neither inbound nor outbound traffic will be blocked unless you install Firestarter or similar tools.

---

### Post by nowshining on 2007-09-03
no outbound will work just fine.. do not open up inbound ports as that will let people in...outbound is only needed for stuff like gaim and such.... only let internal when p2ping and only to the p2p ports you want to let people access...

---

### Post by NacIK on 2007-09-03
Still didn't work.  I have firestarter but when I turn it off it still wont log in

---

### Post by nowshining on 2007-09-03
go here [Shields UP! &#8212; Internet Vulnerability Profiling]("https://www.grc.com/x/ne.dll?bh0bkyd2")
hit proceed then continue when a dialog box comes up

under shields up services click the link all service ports and do this with firestarter off.. what are the results??[FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=2][/SIZE][/FONT]

---

### Post by philinux on 2007-09-03
I have kopete working fine and I have firestarter but did not change any settings :confused:

Right click on the kopete icon and select configure and tell us how your accounts have been set up.
For instance msn should have your full email address whereas yahoo only needs the bit before the @ symbol to work.

---

### Post by wieman01 on 2007-09-03
> **NacIK said:**
> Still didn't work.  I have firestarter but when I turn it off it still wont log in
How did you turn it off?

---

### Post by NacIK on 2007-09-03
It came up with everything stealthed

Yahoo is without the @yahoo.com and MSN is with the @hotmail.com

---

### Post by philinux on 2007-09-03
If your are using a router it has a hardware firewall which should show that all ports are stealthed. Mine is but kopete works fine :confused:

---

### Post by wieman01 on 2007-09-03
> **philinux said:**
> If your are using a router it has a hardware firewall which should show that all ports are stealthed. Mine is but kopete works fine :confused:
The hardware firewall should not be a problem as it is usually open for outbound traffic. It should not block any outgoing traffic.

Are you sure you have disabled Firestarter/IP tables? Have you clicked the shutdown button using the GUI? I suspect IP tables are still up!

---

### Post by NacIK on 2007-09-03
> **wieman01 said:**
> 
Are you sure you have disabled Firestarter/IP tables? Have you clicked the shutdown button using the GUI? I suspect IP tables are still up!

I hit the shutdown button

---

