---
title: "Dialup Internet (with LAN) Need some help!"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-06-16
How can I make it so my computer uses a dial up contention via wvdial. Instead of the LAN internet connection?

I have a cable internet connection that goes into my server. From there my server is plugged into a switch. Allowing all my other devices to have access to the internet.

When my traffic for the given month is used up, I turn off my cable modem preventing myself from having a huge bill.

I want to use dial up in the cases that this should happen.

I setup a Dial up connection on one of my main computer. The dial up connection is fine. But when I go into Firefox or ping, it attempts to do so thought my cable internet and fails. How do I tell my machine to use the Dial up internet instead of the LAN?

Thanks

---

### Post by klytu on 2007-06-16
> **guysmiley25 said:**
> How can I make it so my computer uses a dial up contention via wvdial. Instead of the LAN internet connection?

I have a cable internet connection that goes into my server. From there my server is plugged into a switch. Allowing all my other devices to have access to the internet.

When my traffic for the given month is used up, I turn off my cable modem preventing myself from having a huge bill.

I want to use dial up in the cases that this should happen.

I setup a Dial up connection on one of my main computer. The dial up connection is fine. But when I go into Firefox or ping, it attempts to do so thought my cable internet and fails. How do I tell my machine to use the Dial up internet instead of the LAN?

Thanks

Try ```
sudo network-admin
``` highlight your modem and click ¨properties¨. On the options tab tick ¨set modem as default route to internet¨. You´ll need to clear the same option to connect to the internet via your cable modem.

---

### Post by guysmiley25 on 2007-06-16
I'm using wvdial to connect.

I do not understand what happens and how network admin works? How do I select what modem I want to use? I have two modems .My cellphone, and my normal modem. When I configured network-admin with the phone number username and password. It tries to use my cellphone. Not only that it does so incorrectly.

I would prefer to use wvdial to connect to the internet.

After I run wvdial I could disable eth0 and then enable ppp0 but then I wont have access to my network. And this might not work.

Any other ideas?

Thanks for the response.

---

### Post by klytu on 2007-06-17
> **guysmiley25 said:**
> I'm using wvdial to connect.

I do not understand what happens and how network admin works? How do I select what modem I want to use? I have two modems .My cellphone, and my normal modem. When I configured network-admin with the phone number username and password. It tries to use my cellphone. Not only that it does so incorrectly.

I would prefer to use wvdial to connect to the internet.

After I run wvdial I could disable eth0 and then enable ppp0 but then I wont have access to my network. And this might not work.

Any other ideas?

Thanks for the response.

Yes, I have one more idea. :-) Try```
 sudo gedit /etc/ppp/options
``` At the end of the file add > replacedefaultroute Save and close the file, then try using wvdial with your cable modem turned off and see if you can connect to the internet.

---

### Post by guysmiley25 on 2007-06-19
Thank you klytu that worked perfectly.

How would I make it so it uses the DNS server that is given from the dial up ISP instead of the one my DHCP gives.

This is required because I have my own DNS server.  But the times I use dial up is because the internet to the server is down.

Thanks.


Also when I dial with wvdial a lot of the time it says line busy and attempts to dial again. I just left it do this over and over again until it connects. I had just assumed that it was because the was was busy. However sometimes it could take a whole day to connect!!! So I thought before I complain to my ISP I would check to see if it was there fault.

So while it was connect I would listen on with the other phone and this is what seems to happen.

wvdial dials the number. before the call is answered wvdial tries to connect and fails. The call is then answered but wvdial thinks the line is busy so dials again.

This happens over and over again, does anyone know how to fix this?

Here is my configuration
```

Modem = /dev/modem
Phone =  xxxxxx
Username = guysmiley25
Password = xxxx
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Baud = 460800
ISDN = 0
Carrier Check = no
Stupid mode = on

```

Thanks

---

### Post by klytu on 2007-06-20
> **guysmiley25 said:**
> Thank you klytu that worked perfectly.

How would I make it so it uses the DNS server that is given from the dial up ISP instead of the one my DHCP gives.

This is required because I have my own DNS server.  But the times I use dial up is because the internet to the server is down.

Thanks.


Also when I dial with wvdial a lot of the time it says line busy and attempts to dial again. I just left it do this over and over again until it connects. I had just assumed that it was because the was was busy. However sometimes it could take a whole day to connect!!! So I thought before I complain to my ISP I would check to see if it was there fault.

So while it was connect I would listen on with the other phone and this is what seems to happen.

wvdial dials the number. before the call is answered wvdial tries to connect and fails. The call is then answered but wvdial thinks the line is busy so dials again.

This happens over and over again, does anyone know how to fix this?

Here is my configuration
```

Modem = /dev/modem
Phone =  xxxxxx
Username = guysmiley25
Password = xxxx
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Baud = 460800
ISDN = 0
Carrier Check = no
Stupid mode = on

```

Thanks

I think you can also make the adjustments for both situations using ```
sudo gedit /etc/ppp/options
``` I use gnome-ppp or pon/poff the rare times I connect to the internet via a dial-up modem, so I have minimal experience in directly setting up the correct options in this file. I read through it though, and it appears to be well self-documented. There are many options in the file that are commented out by default; those have a # symbol in front of them. To use an option you need, you would just edit the line as appropriate and delete the # at the beginning of the line. ```
man pppd
```  Will give you information on all the available options you can use and configure.

---

