---
title: "WEP Key?"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by obey43 on 2006-02-22
my friend across the hall has a belkin router, that is connected to the wall via ethernet.  the only things connected to it are two xbox's which are connected to it via ethernet.  

my wifi radar can't connect to it, because i believe it has a WEP key i need...
he doesn't know it....

how should i go about obtaining it?

---

### Post by matthew on 2006-02-22
Ask your friend for the WEP key. Anything else is unethical at best and possibly illegal as well.

EDIT: I reread your post and realize you may be saying your friend doesn't know the WEP key rather than my initial interpretation that your friend doesn't know you are trying to use his wireless router. Could you confirm one or the other?

---

### Post by obey43 on 2006-02-22
I asked im if i could connect and he said of course, but he doesn't know the wep key.  i asked him if he knew it, and he thought i was talking about a password or something. him and his roomate each thought the other one knew it, but they don't.

---

### Post by carlosqueso on 2006-02-22
if you had a crappy router like mine, unplugging it and plugging it back in would work, but most I believe remember their settings when you lose power.

---

### Post by matthew on 2006-02-22
[quote=carlosqueso]if you had a crappy router like mine, unplugging it and plugging it back in would work, but most I believe remember their settings when you lose power.[/quote]Or he should easily be able to access the router settings and set a new password if it's his router.

If it's really just a WEP passphrase it can be cracked...searching Google might help you. That sort of discussion violates forum guidelines.

---

### Post by obey43 on 2006-02-22
He doesn't know how to access it.  I have searched google and ran into a bunch a tar.gz's that I have actually been able to compile but been clueless how to run.

how exactly could I/He acess it? there are no computers connected to it?

---

### Post by matthew on 2006-02-22
[quote=obey43]how exactly could I/He acess it? there are no computers connected to it?[/quote]My first thought is to find the model number of the Belkin router and do a google search for it...maybe you can find a users manual. Or start on the [Belkin website]("http://www.belkin.com/index.asp").

---

### Post by obey43 on 2006-02-22
its a 

Belkin - Wireless G Plus Router 

can't find anythign on google...

---

### Post by matthew on 2006-02-22
These links are from the Belkin website I gave a link for in my last post

The Belkin page describing the router
[http://catalog.belkin.com/IWCatProductPage.process?Merchant_Id=&Section_Id=203274&pcount=&Product_Id=203415]("http://catalog.belkin.com/IWCatProductPage.process?Merchant_Id=&Section_Id=203274&pcount=&Product_Id=203415")

The Belkin page where you can download a user manual for the router
[http://www.belkin.com/support/download.asp?download=F5D9230-4&lang=1&mode=]("http://www.belkin.com/support/download.asp?download=F5D9230-4&lang=1&mode=")

Since I'm not there with you and the hardware my best suggestion is to do some reading

---

### Post by davetheravexxxx on 2006-02-22
Firstly I just want to say I have always had problems with that type of router and I have had six so far (only bought one but its had to be replaced).  There is one of two things you can try.

1. Try plugging the computer into the router via an ethernet port, see the gateway (/broadcast) address you receive.  Input this into a web browser, it should then bring you to the configuration page from where you can access WEP settings.  Assuming DHCP is enabled, if its not you can get gateway address from the Xbox but will need to manually set your own IP Address

2.  Reset the router via the reset button on the device, carefull though as this may remove important settings your friend needs.

---

### Post by obey43 on 2006-02-22
where would i find the gateway (/broadcast) adress?

---

### Post by davetheravexxxx on 2006-02-22
In either Ubuntu or Windows, you should be able to find it by clicking on the networking icon in the corner of the screen.

Alternatively you can do an ifconfig from the terminal

---

