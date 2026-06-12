---
title: "problem connecting to wireless internet in ubuntu"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by threeonethree on 2007-08-02
my gf has a toshiba laptop.. she removed windows today and installed ubuntu.. installation went fine  and her onboard intel graphics was detected and installed..  she clicked on top right network manager it tried to find connections around her .. she found her connection too .. when she clicked on it asked for a passphrase , she gave the right one as 9876543210  but it wont connect her ..

also she cant open the 192.168.2.1 router config page in this pc , but can open in her bros pc .. hlep


i found out its a wep 64 bit passcode that she uses on other computer .. isnt wep enabled in ubuntu please help

---

### Post by Inxsible on 2007-08-02
> **threeonethree said:**
> my gf has a toshiba laptop.. she removed windows today and installed ubuntu.. installation went fine  and her onboard intel graphics was detected and installed..  she clicked on top right network manager it tried to find connections around her .. she found her connection too .. when she clicked on it asked for a passphrase , she gave the right one as 9876543210  but it wont connect her ..

also she cant open the 192.168.2.1 router config page in this pc , but can open in her bros pc .. hlep

Does the router also have MAC address filtering enabled? Maybe that's why she cant connect. As for the problem that she cant get to the 192.168.1.1 page, ask her to log in with her bros machine, go to that page, and then specifically click 'Logout' on that page. 

I have seen this happen with me when I log in with one machine change a setting and then simply close the browser and then I cannot log in with any other machine except the one I used earlier. Maybe the router saves the session ID and machine ID that accesses it.

---

### Post by threeonethree on 2007-08-02
> **Inxsible said:**
> Does the router also have MAC address filtering enabled? Maybe that's why she cant connect. As for the problem that she cant get to the 192.168.1.1 page, ask her to log in with her bros machine, go to that page, and then specifically click 'Logout' on that page. 

I have seen this happen with me when I log in with one machine change a setting and then simply close the browser and then I cannot log in with any other machine except the one I used earlier. Maybe the router saves the session ID and machine ID that accesses it.


mac address filtering = disabled... wep 64 bit is enabled .... cant connect please help

---

### Post by Inxsible on 2007-08-02
> **threeonethree said:**
> mac address filtering = disabled... wep 64 bit is enabled .... cant connect please help

All I can say is that she probably forgot her passphrase. Normally, you enter a word or phrase that you can remember and it spits out this 64 bit alpha numeric string which is used as the passphrase. You need to enter the word or phrase that you used to set up the router.

Alternatively, you can simply log in to the router(using the bros machine) and then change the password for the router network and see if the new one works

---

### Post by threeonethree on 2007-08-02
i tried to reover the passphrase using cain and abel and instead of saying passphrase it said 9876543210 HEX   ... she tried to choose hex when she tried to give this passphrase but then the "login" button isnt activated when she chooses hex or something other than wep 128 bit

---

### Post by threeonethree on 2007-08-02
[http://img527.imageshack.us/img527/9624/adszmp0.jpg](http://img527.imageshack.us/img527/9624/adszmp0.jpg) 

a screenshot of the router  config from her bros pc help please

---

### Post by threeonethree on 2007-08-02
:(:(:(:( helpppppppppppppppppppppppp

---

### Post by Inxsible on 2007-08-02
Instead of entering the Key1 try entering the passphrase.
0) You can select 128 bit encryption for better protection. 64-bit WEP is pretty much useless these days for a determined hacker.

0a) Also select Dynamic Key Provisioning. That way keys will be dynamically generated (I think) and you will only need to remember the passphrase

1)Select the checkbox near Passphrase and then enter any word  that you would like to make as your password. Remember that password.

2)Apply the changes and restart your router. Then select your network name and when it asks for the password, enter the one that you made in the 1st step.


Hope that helps !

---

### Post by splintercellguy on 2007-08-02
Can you check the wireless clients page on the router and see if she's actually connected?

---

### Post by threeonethree on 2007-08-02
> **Inxsible said:**
> Instead of entering the Key1 try entering the passphrase.
0) You can select 128 bit encryption for better protection. 64-bit WEP is pretty much useless these days for a determined hacker.

0a) Also select Dynamic Key Provisioning. That way keys will be dynamically generated (I think) and you will only need to remember the passphrase

1)Select the checkbox near Passphrase and then enter any word  that you would like to make as your password. Remember that password.

2)Apply the changes and restart your router. Then select your network name and when it asks for the password, enter the one that you made in the 1st step.


Hope that helps !

selected 128 it encryption... selected dynamic key provisioning .. selected the checkbox near passphrase and typed hello as passphrase.. applied the changes and restarted the router... in ubuntu it didnt connect just like before.. when i came back to my windows pc and check the router page again , it was stilll 128 bit, dynamic key provisioning was turned on , but the passphrase box was blank !!! whats going on?? and on windows pc how can i check if shes is using wep or wpa , how do i configure it to be wpa instead of wep if shes using wep.. which runs out of the box for ubuntu? wep or wpa .. should i change key entry method from hex to something else?

help me , my girl friend wont be able to talk to me , or will have to reinstall xp :( she cant use her bros pc

---

### Post by Inxsible on 2007-08-02
> **threeonethree said:**
> selected 128 it encryption... selected dynamic key provisioning .. selected the checkbox near passphrase and typed hello as passphrase.. applied the changes and restarted the router... in ubuntu it didnt connect just like before.. when i came back to my windows pc and check the router page again , it was stilll 128 bit, dynamic key provisioning was turned on , but the passphrase box was blank !!! whats going on?? and on windows pc how can i check if shes is using wep or wpa , how do i configure it to be wpa instead of wep if shes using wep.. which runs out of the box for ubuntu? wep or wpa .. should i change key entry method from hex to something else?

help me , my girl friend wont be able to talk to me , or will have to reinstall xp :( she cant use her bros pc

To be able to setup a WPA network, your router needs to support WPA. I see that your router does support it. Disable the WEP and go to the WPA link in your router admin page and play with the settings there.

---

### Post by threeonethree on 2007-08-02
which has best support out of the box in feisty?? wep or wpa?

---

### Post by Inxsible on 2007-08-02
> **threeonethree said:**
> which has best support out of the box in feisty?? wep or wpa?

I havent had problems with either. But WPA is more secure than WEP. WEP has become old-school now.

---

