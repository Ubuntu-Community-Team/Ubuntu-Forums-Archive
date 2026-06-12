---
title: "What kind of router should I go for?"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by Stolengoat on 2006-08-03
Hi all

I am a complete newbie, and I have just installed 64 bit Dapper Drake.  I once dabbled with Hoary Hedgehog and I got the impression at the time and since that it was almost impossible to get online using a Speedtouch USB modem (supplied by Tiscali).  In an effort to take the path of least resistance I have resigned myself to getting a router, but if at all possible I would prefer to go for a wireless model.  Can anyone recommend a trouble free wireless set-up, or is it best to stick with a wired one (until I become more expert!)

Many thanks - sorry for being so incompetent!

---

### Post by Handyman's Special on 2006-08-03
Hi,

I found another solution to the 'Windows Modem' problem - an external modem. It connects with a Serial cable. Have had no problem with that, once I started using the Gnome PPP DialUp Tool. The dialup connector found at Administration\Networking would not remember my selections, however.

I have gotten very curious about this 'router' business, though. What would be the advantage of using one?

Cheers,
Handyman's Special

---

### Post by carlosqueso on 2006-08-03
@Stolengoat:

Either a wireless or wired one will work fine (especially since most wireless ones also have wired ports). If you think you'll want wireless at some point, spend the extra $10 and get a wireless one. You pretty much just plug in the DSL or cable modem into the router, and the router to the computer and go.  My D-Link wireless router has a real easy setup program (that you do through a web browser), and most others do too.

@Handyman:

A router allows more than one computer to share the same internet connection. It also creates a home network.  If you're using dial-up, it doesn't make much sense to get one, as your connection would slow waaaay down with more than one computer on it at the same time.

---

### Post by mjm115 on 2006-08-03
I have a [Buffalo WHR-G54S]("http://www.newegg.com/Product/Product.asp?Item=N82E16833162173") which I absolutely love.  It's a wireless router and it's cheaper than the Linksys, Netgear, and D-Link equivalents, but just as good.  I flashed it with the open-source [DD-WRT]("http://www.dd-wrt.com/") firmware, so it can do everything the others can do.

I've never had any issues with this router.

---

### Post by anaconda on 2006-08-03
The problem with a wireless router is that your neigbours can also use your internet connection, if they want to..

Even if you use the crypted password protected mode. By monitoring the dataflow it is possible to get the password.. maybe not wery likely.. but it is one reason why I prefer the wired choise.. in addition to the cheaper price... 

One more advantage is that you can buy a router with a firewall for added security.. with linux it may not be necessary, but if you ever use windows..

---

### Post by John.Michael.Kane on 2006-08-03
You could build your own firewal-router if you have a spare unused machine. there's many firewall distros out there for this.
Monowall
IPCop
SmoothWall
Pfense

---

### Post by dave2010 on 2006-08-04
Okay, I've had enough of messing with speedtouch stuff.
I'm getting a wireless router+adsl modem.
can anyone tell me if this one works with dapper amd if you've had any experience with it please.

[http://www.microdirect.co.uk/ProductInfo.aspx?ProductID=11878](http://www.microdirect.co.uk/ProductInfo.aspx?ProductID=11878)

It is a NETGEAR DG834PN RangeMax ADSL Modem Wireless Router.

Thanks I really need to move to Linux as i've had enough of the 6 monthly re-installs, the viruses, the spyware and now this WGA crud.
J.

---

### Post by kriding on 2006-08-04
Try this [link]("http://www.billion.com/product/powerline/bipac7560g.htm") I use it and it's never let me down in the 12 months I've had it.

Mine is connected via my built in LAN and allows both my machines to access the net without any configuration at all, and best of all, the powerline ability lets me network both systems with no long runs of cat5, or any signal problems associated with wifi

---

### Post by nickpaton on 2006-08-04
Hi Stolengoat & Dave (Stolengoat eh??!! Got to be a story there:D )- Welcome!

Apologies if stating the obvious - regarding using any ADSL modem routers, since it connects to the Ethernet / LAN port on your PC, then generally the router is not affected by having a Linux OS installed on the PC.  It's making sure that the LAN board within the PC is detected by Linux OK which is important.

Whilst I have not actually used that precise Netgear router, Dave, all I can say is that I have used many models from them, wired & wireless, on Win & Linux and all fine.  Hence never use anything from anyone else.

Their interface is excellent, which makes it easy to set up and customise, and if you do have a problem, their telephone and email support are good too.

Check out other suppiers like broadbandbuyer and ebuyer - could be cheaper.

---

### Post by ske1fr on 2006-08-04
He he.  Yes, I had a Netgear DG834 - not wireless.  It lasted four months then the ADSL modem in it stopped working.  Now I have a LinkSys WAG54GS.  I don't use the wireless part, it's permanently switched off.  Cabled networking gets round all that "is my neighbour hijacking my broadband, am I encrypted enough" stuff.  Wiring is surprisingly easy to do if you can lift carpet (for those of us in cooler northern climes) and work carefully.  The power socket networking is very clever, but expensive.

Every router should in theory work with any networking operating system at all, because you don't need drivers for a router, just a working network card (wireless or wired), a working TCP/IP network protocol in your operating system, and a web browser to let you configure the router.  You can think of the router as a little dedicated computer just for networking, firewall and broadband ADSL connection, with your own computer as a terminal for it.

Whatever router you go for, make sure you understand how it works and how to make it as secure as possible.

---

### Post by Frank Golden on 2006-08-04
I use the Linksys WRT54GL router with Thibor's HyperWRT modified
firmware. Works great. If you are worried about the neighbors
hacking into you network you can always shut off the wireless
in the configuration. WEP will keep most nosy neighbors out.
The use of a router (NAT type which virtually all are today)
is a great security measure as the way NAT works any unsolicited
traffic will be dropped before getting to your machine(s).
Great "hardware firewall".

---

### Post by dave2010 on 2006-08-04
Thanks for the super quick reply, it's these forums that stop me from wiggin' out and just re-installing windows> i'm in the middle of a ccna so feel a tad 'shamed for missing the obvious on the OS independence!
Since I'm pretty cheap i've decided to get this:

Zyxel Prestige 660HW-T1 802.11g 54Mbps Wireless 4 x 10/100 ADSL Modem
[http://ebuyer.com/customer/products/index.html?rb=20821300581&action=c2hvd19wcm9kdWN0X3Jldmlld3M=&product_uid=109521](http://ebuyer.com/customer/products/index.html?rb=20821300581&action=c2hvd19wcm9kdWN0X3Jldmlld3M=&product_uid=109521)

because its 20quid cheaper and i get a free wireless usb adapter which will replace the 15 metres of cat5 to my father's PC.
It'll also be nice to sort out the snakes nest in the front room (laptop and kiss-dp1500 dvd player).

It's strange, but after years of using windows it feels geekily good to go back to CLI.
Thanks again Nick.
"Dave"

---

### Post by eXisor on 2006-08-04
[quote='anaconda']The problem with a wireless router is that your neigbours can also use your internet connection, if they want to..

Even if you use the crypted password protected mode. By monitoring the dataflow it is possible to get the password.. maybe not wery likely.. but it is one reason why I prefer the wired choise.. in addition to the cheaper price...

One more advantage is that you can buy a router with a firewall for added security.. with linux it may not be necessary, but if you ever use windows..
__________________
____________
anaconda [/quote]

A SSID broadcast off and WPA2 AES pre-shared key of 64 random characters setup is not going to be hacked by any neighbor. Even a hacking guru is going to get little joy.

---

### Post by dave2010 on 2006-08-07
Just a quick update.
Instead of buying a router i bought a flight to france.
tried this : [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)
again this time copy+pasting.
it worked.

---

### Post by jason.b.c on 2006-08-07
> **SD-Plissken said:**
> You could build your own firewal-router if you have a spare unused machine. there's many firewall distros out there for this.
Monowall
IPCop
SmoothWall
Pfense

[http://www.freesco.org/]("http://www.freesco.org/")
[IMG]http://http://www.freesco.org/home/banr/banner-468.gif[/IMG]

;)

---

