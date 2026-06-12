---
title: "No internet connection"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by Preksus on 2006-02-19
I am 3 hours into using ubuntu.  I am connecting using a router D-link DSL G604T.  Where do I enter account details and do any configuring of hardware.  I need some help as I am a complete newby.

---

### Post by bernardfrancois on 2006-02-19
In most cases you don't need to configure anything if you are using a router.

Try executing this command (first open a shell: ALT+F2, enter 'xterm', press return):
**sudo ifup eth0**

Then test your internet connection, for example with **ping -c 1 [www.ubuntu.com](www.ubuntu.com)**. If you get 'one package received', your internet connection works.

If it doesn't work, please post the output of **ifconfig -all**.

---

### Post by moephan on 2006-02-19
I'm not sure exactly what you are trying to do, but I think that the dialog you are looking for is under System->Administration->Networking.

For example, if you are trying to configure your DSL model, assuming it's plugged into your ethernet port, you do this:

1. Go to top Menu, pick System->Administration->Networking.
2. If you get prompted to enter a password, enter the password that you use to log in
3. In the Network Settings dialog, click on "Ethernet Connection" to select it, then click the Properties button.
4. In Ethernet Properties, click the checkbox "Enable this Connection"
5. In Ethernet Properties, set the Cofiguraiton dropdown to "DHCP".
6. In Ethernet Properties, click OK
7. In Network Settings, set the Default gateway device to eth0 (that's your ethernet card).
8. In Network Settings, click OK.

Network Settings has tabs for setting hosts and your DNS as well.

HTH

Cheers, Rick

---

### Post by mhl12 on 2006-02-19
I've had a similar situation. Try uplugging your router or modem from the power outlet for about 5 minutes. Then restart your computer and see if it's connected.

---

### Post by Preksus on 2006-02-19
Thanks for your advice guys, I re-installed ubuntu and followed instructions, unfortunately I still can't get on the internet though I can get access to my router.  Something is stopping me from gaining net access.

---

### Post by Kenzo on 2006-02-20
I had the same problem.  Can you ping say [www.ubuntu.com?](www.ubuntu.com?)  I could ping okay but couldn't connect.

I changed the DNS in the netrworks setting to the primary and secondary DNS of my ISP.  Then I got connected ok.  But when I rebooted the setting was lost and no connection.  The DNS was automatically set back to 192.168.1.1.  

Does anyone know if there is there a way to make the DNS setting stick? Thanks

---

### Post by manicka on 2006-02-20
I have the same router. You will need to set up you're connection properties and dns settings manually as this particular router does not pass the dhcp settings properly to Linux. Specifically you'll find that it sets itself as the dns server rather than using your providers dns server address and domain. This won't stick unless you manually set your connection properties to use a static ip address as well

---

### Post by Kenzo on 2006-02-20
Cool.  Thanks Manicka

---

### Post by Preksus on 2006-02-20
Thanks Manicka the DNS was the problem, I am now online typing this reply.  Just one problem !  Everytime I close down my PC the software looses my DNS address and resets back to 192.168.1.1 for my router, how do I enter the DNS and make it stick.

---

### Post by romdos on 2006-02-20
I think that your problem is that you are still using dhcp to configure your networking
device.  This alows your router to reset your dns addresses every time you boot or bring up networking.

To fix this go to System > Administration > Networking
 
click on your networking device and then on properties and change configuration to: Static IP Address

give your networking device an ip address in the same network as your router: 192.168.1.10
set your netmask to: 255.255.255.0

set the gateway address to your router's ip address

when you save these settings and set the proper DNS addresses they *should* stick on reboot.

---

### Post by Preksus on 2006-02-21
Thanks for your advice guys.  I am now a very happy Ubuntu user with a permanent internet connection.  Help yourselves in the drinks cabinet.

John Knowles

---

### Post by mikes34 on 2006-03-03
Hi, I have the same problem, I tried everything you mentioned, but anything have worked :( I think my problem is not using dhcp configuration...  internet connection works, when I test it by ping, I recieve packages, but I can't join the web sites by mozila... I had the same problem when I was using FC 4 but only with mozila, konqueror worked... can anybody help me? pleeeease 
I have DSL internet connection using ADSL Router D-Ling DSL-546T.

---

### Post by Q4U on 2006-03-03
does it work if you go to terminal and type sudo dhclient? Q4U

---

