---
title: "Networking vista and xubuntu"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Dionysus135 on 2007-08-20
Hi im very new at networking in general.Im planning to network my windows vista and my xubuntu.Does anyone know any tutorial where to start?Also what hardware do i need to buy?Do i need a router?If i need a router which routers come with Wifi?I want to connect my psp to online using the router:).

---

### Post by jdfreshwater on 2007-08-20
I'm not sure about vista, but I know that windows genrally will network with filesharing via Samba on the linux machine.  The best way to hook up multiple machines would be a router.  There are many varieties out there and people who will tell you one is better then the other.  The best way to choose a router is to get a Wireless G or N router, that you feel comfortable with.  The best way in choosing is to view a few reviews and check out your local electronics store.

---

### Post by rickyjones on 2007-08-20
When you say "networking" you'll need to be more specific with what you want to do.

Do you want to share your internet connection (say, DSL or Cable) with more than one computer?

Do you want to share files and/or printers from one computer to another?

Now, for the infrastructure to connect two computers in a residential setting I recommend using the Linksys WRT54G router. It's a wireless router (802.11G), a 4-port switch, and pretty secure router. I've had countless installs and not a single problem with it.

Once installed if everything is set to DHCP or Obtain IP Automatically then both machines should easily talk to each other over whatever protocol you want to use.

I hope this helps!

-Richard

---

### Post by bumanie on 2007-08-20
Just networked a dual boot ubuntu and windows with a vista machine.
Used a netgear wgr614v7 router with usb dongle attached to the vista machine. 
Easy to configure, although you need to download vista drivers etc from the netgear website and burn them to cd.

---

### Post by Dionysus135 on 2007-08-20
> **rickyjones said:**
> When you say "networking" you'll need to be more specific with what you want to do.

Do you want to share your internet connection (say, DSL or Cable) with more than one computer?

Do you want to share files and/or printers from one computer to another?

Now, for the infrastructure to connect two computers in a residential setting I recommend using the Linksys WRT54G router. It's a wireless router (802.11G), a 4-port switch, and pretty secure router. I've had countless installs and not a single problem with it.

Once installed if everything is set to DHCP or Obtain IP Automatically then both machines should easily talk to each other over whatever protocol you want to use.

I hope this helps!

-Richard

Yes i do want to share my internet connection with the xubuntu computer.Im using a cable modem right now.

For the 2nd question yes and no.I dont want to share any files between the two computer but i want them to share the same printer.

Oh yea another question is that is it possible to have different ip adresses on each computer? I dont want to have the two computers sharing the same ip adresses. One last question would you recommend netgear as well?

---

### Post by rickyjones on 2007-08-20
> **Dionysus135 said:**
> Yes i do want to share my internet connection with the xubuntu computer.Im using a cable modem right now.


Then a simple router will do. I still recommend the Linksys WRT54G router for this setup as I know it works quite well.

> **Dionysus135 said:**
> 
For the 2nd question yes and no.I dont want to share any files between the two computer but i want them to share the same printer.


As long as both computer are connected to the router and have the same print sharing protocol then you should be fine. I have not used Vista so I'm not sure how easy it is to share a printer or connect to a shared one but it should be similar to Windows XP, which is extremely simple. You'll need to refer to the documentation for your printer and whatever host OS you will be using for specific instructions.

> **Dionysus135 said:**
> 
Oh yea another question is that is it possible to have different ip adresses on each computer? I dont want to have the two computers sharing the same ip adresses. One last question would you recommend netgear as well?

Well, by default both computers will have a different private IP address. Example: one computer will be 192.168.1.100 and the other would be 192.168.1.101 (if you use a linksys router). They will share the same Public IP address because the router will "own" this IP address. This does not affect your local network and will be just fine. I personally do not recommend Netgear. I have not had good results with their products. However others have had the exact opposite experiences. To each his own.

Hope this helps!

-Richard

---

### Post by Dionysus135 on 2007-08-20
Thanks alot for the information! Is there any website that shows how to set up a network for beginners?And what linksys router do you recommend?I usually play online games and use my computer for school work and 2nd i want to use WiFi to connect to my psp.

---

### Post by rickyjones on 2007-08-20
> **Dionysus135 said:**
> Thanks alot for the information! Is there any website that shows how to set up a network for beginners?And what linksys router do you recommend?I usually play online games and use my computer for school work and 2nd i want to use WiFi to connect to my psp.

Well, there are a lot of websites out there. A quick google search will probably give you too many to go through! Any router that you purchase will also come with documentation that will give you the basics for setting up the network (as in, plugging in all the cables so that it works). As for sharing files/printers... that is more complicated and will depend on exactly what OS will be the host.

I still recommend the Linksys WRT54G:
([http://www.newegg.com/Product/Product.aspx?Item=N82E16833124010&Tpk=wrt54g](http://www.newegg.com/Product/Product.aspx?Item=N82E16833124010&Tpk=wrt54g))
([http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1149562300349&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0034926718B08](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1149562300349&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0034926718B08))

-Richard

---

### Post by Dionysus135 on 2007-08-20
> **rickyjones said:**
> Well, there are a lot of websites out there. A quick google search will probably give you too many to go through! Any router that you purchase will also come with documentation that will give you the basics for setting up the network (as in, plugging in all the cables so that it works). As for sharing files/printers... that is more complicated and will depend on exactly what OS will be the host.

I still recommend the Linksys WRT54G:
([http://www.newegg.com/Product/Product.aspx?Item=N82E16833124010&Tpk=wrt54g](http://www.newegg.com/Product/Product.aspx?Item=N82E16833124010&Tpk=wrt54g))
([http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1149562300349&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0034926718B08](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1149562300349&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0034926718B08))

-Richard

When i buy a linksy router do i get WiFi?

P.S 
Sorry for asking alot of questions...lol

---

### Post by rickyjones on 2007-08-20
When you buy /that/ Linksys router then yes, wifi is on the router. Most residential routers on the market today are wireless. It will say on the box whether or not it is.

-Richard

---

