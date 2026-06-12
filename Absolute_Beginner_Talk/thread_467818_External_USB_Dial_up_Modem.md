---
title: "External USB Dial up Modem"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-06-08
I'm after a good quality external USB dial up modem.

Anything I have to look out for in term of chip sets etc for compatibility?

Thanks

---

### Post by laidback on 2007-06-08
If you can possibly manage it get a router/modem instead. Mine cost around £30 and has made a huge difference, but I do have broadband too.

---

### Post by guysmiley25 on 2007-06-08
router/modem?

hmm can it connect to your lan, and have some means to access, eg web interface? And then plug into your phone line to connect to your ISP via Dial Up? That would be really cool because then I could share the dial up Internet with all my computers with no need for a master computer!

If not then I'm just after a basic good old 56k modem. Just wanted to make sure I could just go out and buy anything.

Thanks

---

### Post by laidback on 2007-06-08
Not sure about the dial up modem issue but I have 3 computers on my home network, 2 run Linux and the other one is errrrr another sort. All access the internet via the router/modem. They come with a number of ethernet ports in them, mine has 4, but I believe that you can find them with a greater number should you want that. Mine requires and ADSL connection.
Many years ago my work had a dial up that was shared amongst about 6 users over a Windows for workgroups network. Only one person could access the internet at a time but it did work. We used a hub to connect all the pc's together but I'm afraid I don't have any details of the configuration, it was a long tiime ago now. But I do remember that we had an old pc that managed the modem connection, a sort of server on the network side of the modem. I'm sure that there are people around who could suggest suitable system for you.

---

### Post by guysmiley25 on 2007-06-09
I think I'm just after a normal 56K modem, just wanted to know if I could buy anything and it will work fine?

---

### Post by rich.bradshaw on 2007-06-09
Normally you can get one free from your ISP... Not sure if dial up routers exist though.

---

### Post by guysmiley25 on 2007-06-10
Yeah I did not think they exist either.

Still wondering if there is a certain type of modem that I should buy that will work well with Ubuntu

---

### Post by HotShotDJ on 2007-06-10
You'd be best off buying an external serial (DB9) modem.  USB modems can be hit-or-miss.  I've NEVER had problems with standard serial port modems.  (If your computer doesn't have serial ports, you can add them using a PCI card -- unless you have a laptop, then your options are more limited).

---

### Post by Bartender on 2007-06-10
I don't know what's available in UK vs. US, but I followed advice given many times on this forum and bought a couple of 56K USRobotics external modems.  Got them used on eBay.  Sportster model #0701.  If you find beige colored ones, make sure they're labeled as 56K.  I found lots of 33.6K models.
If you find black ones, those are newer models.  
I hooked mine up to my Windows machine, found the USR support site, and used the stand-alone flash software to flash the modem firmware to the latest version.  There's a Linux flasher but not familiar with it.  I asked USR, and was told either version does the same thing to the brains of the modem.

I haven't seen this with my own two eyes, so take it for what it's worth... if you have a newer PC without serial ports it's supposedly possible to run a serial modem thru a USB port by using a serial-to-USB dongle or adapter.  As I said, I'm not sure about this.

There are other external modems, but only a few brands run without hassle on Linux.  The USR's are supposed to be the most trouble-free.

---

### Post by guysmiley25 on 2007-06-11
Do you think that [this]("http://www.ascent.co.nz/productspecification.aspx?ItemID=334085") guy will work?

I do have in two other computers a 56K modem, however they have the conexant chip set. This driver cost money for full support. I would rather go with a modem that is already supported. 

From the sounds of things a serial modem should work fine however I found [this]("http://www.ascent.co.nz/productspecification.aspx?ItemID=111579") guy. It says it uses the conexant chip set, but it is also serial?

Although I have a serial port, just in case in the future I want to use it with a modern computer. Has anyone successfully used a serial modem with a serial-to-USB dongle?

I found a [USRobotics]("http://www.ascent.co.nz/productspecification.aspx?ItemID=334499") one. Cost quite a bit more. Will that work if the others will not?

Thanks for all the help guys.

Chears

---

### Post by guysmiley25 on 2007-06-12
Anyone got any comments?

I'm a poor student so I do not wish to purchase something that will cost me too much time and money.

If I buy something that was cheap but a pain to setup, I will not happy. Also if I buy something expensive, where something cheaper will do the trick with not much effort. I will also not be happy.

That is why I beg for any information.

Like I said before I would like to avoid the conexant chipset.

Also my laptop uses the sl-modem-daemon, could I get a modem that uses this, as it was really easy to setup?

I'm tempted to get this [D-Link DFM-562E]("http://www.ascent.co.nz/productspecification.aspx?ItemID=334085"). But still frighten that it will not work.

Also add I want to go external, but it need be will go with PCI. I do have a serial port.

Thanks again everyone.

---

### Post by phil66 on 2007-06-12
Have you looked at these US Robotics

I have the external serial it works not only with Windows but Ubuntu, Pc Linux OS and others

Price is about 50% cheaper at other stores rather than buying at Robotics

Hope this helps


[http://www.usr.com/products/analog/p-56k-menu.asp?show=sub_content_4](http://www.usr.com/products/analog/p-56k-menu.asp?show=sub_content_4)

---

### Post by guysmiley25 on 2007-06-12
The only US Robotics modem I can find avaible here in NZ is the [US Robotics 5630B Fax, 56K Modem]("http://www.ascent.co.nz/productspecification.aspx?ItemID=334499"). It is almost twice the cost of the [D-Link DFM-562E, 56K Modem]("http://www.ascent.co.nz/productspecification.aspx?ItemID=334085").

Both are Serial.

Can anyone say for sure that at lease one of theses will work?

phil66 what is the model of your US Robotics modem? What version of Ubuntu are you running?  What drivers did you have to install if any?

Thanks.

---

### Post by LaidbackBill on 2007-06-12
Don't know if they are sold in NZ but I just recently bought a "Trendnet TFM-560x" from Newegg after reading the reviews of it.  It replaced a Zoom serial modem that I borrowed from my Windows and had set up.  Plugged it in and it worked otb.  It was also one of the cheapest 56k serial modems that Newegg carried $27.00.  You might look around as the some of the name brands are overpriced in my opinion.

Good Luck, Bill

---

### Post by guysmiley25 on 2007-06-12
Thanks LaidbackBill. I've had a look at the [Trendnet TFM-560x]("http://www.trendnet.com/en/products/TFM-560X.htm") and it indeed looks good.

Even there website say it supports linux witch is a good start.

I'm going to have a look around to see if I can find one here in NZ

Chears

---

### Post by phil66 on 2007-06-12
The serial modem I am currently using is the US Robotics model # 5686e 56K v.92 external Fax Modem.

It comes with a disc to install needed drivers etc.

I have used it for Ubuntu Breezy.Ubuntu Dapper Drake ,Ubuntu Fiesty Fawn.Pc Linux OS

I can use it from the network dial-up and the gnome-ppp software.

I am currently running Ubuntu 606.lst as I found Fiesty to be a little to shakey for my needs.

The url I gave you will give you all the info about the modem by that I mean spec data and etc

Hope this helps

---

### Post by guysmiley25 on 2007-06-12
phil66 For the [US Robotics 5686E]("http://www.usr.com/products/home/home-product.asp?sku=USR5686E"). How did you have to install the driver? Did it add a module to the kernel? DId you have to compile something? Did it have a .deb file?

I think I will go with the [Trendnet TFM-560x]("http://www.trendnet.com/en/products/TFM-560X.htm") But just incase I can not find it the [US Robotics 5686E]("http://www.usr.com/products/home/home-product.asp?sku=USR5686E") might be the runner up.

Thanks.

---

### Post by guysmiley25 on 2007-06-12
Oh but don't forget about the [D-Link DFM-562E]("http://www.ascent.co.nz/productspecification.aspx?ItemID=334085"). As this is a modem I could by today. Just need the word, that it will work with no worries!

Thanks

---

### Post by phil66 on 2007-06-12
I have a dual boot system with Windows XP sp2

I installed the modem through the add hardware wizard in Windows
When it asked for a disc I inserted it and let it run

In order to use it for linux all I had to do was to configure a dialer and everything worked

I have another modem on an older computer its a zoom serial and it also works
The folks at cnet forum told me as long as it was a serial modem it would work
They were right on my computers

Lots of luck finding one that works for you

---

### Post by guysmiley25 on 2007-06-12
Thanks for all the help guys it been very helpful.

---

### Post by Bartender on 2007-06-13
Hi, guy -
Chances are very high that the driver CD included with any serial modem will be worthless to you.

If you can borrow someone's broadband connection, download the "gnome-ppp" package.  It'll make dial-up connection easier.  Or go to PCLinuxOS or MEPIS or another KDE based distro that includes KPPP right off the bat.

The GUI-based dialer in Ubuntu has been broken since Dapper.

Sorry that nobody could confirm the USB-to-serial dongle thingie but a few people have told me that it does work.  This is something I want to check out for myself but haven't spent the money yet.

---

### Post by Bartender on 2007-06-14
Take a look at this thread

[http://www.mepislovers.org/forums/showthread.php?t=6847&highlight=dial-up](http://www.mepislovers.org/forums/showthread.php?t=6847&highlight=dial-up)

---

### Post by guysmiley25 on 2007-06-14
Thanks Bartender.

However gnome-ppp, kppp wvdial, etc. All theses are just software that connects to a ISP using your modem. They do not setup or install drivers for your modem. And without the modem being detected, these programs are useless.

It has come to my understanding that a serial modem should work with Ubuntu without any need to install any drivers etc.

As for the USB-to-serial dongle, it might just be a case of symlinking /dev/modem to ttyUSBx or something. Not sure about this though.

Thanks

---

### Post by Bartender on 2007-06-15
Yeah, guy, understood -
Apart from the fact that dial-up will always suck, there are basically 2 big hurdles.  Well, 3.

#1  Finding a modem that Linux can identify and talk to.  External serial seems to be the "least hassle" method.  Finding a way to go serial-to-USB would allow one to move on to newer machinery.  A desktop could accept a PCI card with serial ports, but a laptop doesn't have that flexibility.
  
#2  Finding a program that works for you, whether it's KPPP, wvdial, gnome-ppp, etc.

#3  Finding an ISP that won't cut you off in the middle of a 10-hour update  :(

---

### Post by guysmiley25 on 2007-06-15
Hmm, even if they did cut you off, could you not just resume your update?

aptitude/apt-get grabs the packages first and then installs them doesn't it? So if you got cut off while downloading the packages, if you start again wont it just download the remaining packages?

I do indeed have broadband, but I want the dial up for when I go over my cap. Also I want to use the fax features of a modem.

Thanks.

---

### Post by strangerep on 2007-06-18
I came late to this thread, but I can add a couple of things...

The Netcomm AM5055 USB modem does NOT work with Linux.

My old Dynalink 56K e-modem II works fine with Edgy (ordinary external
serial modem) on an older Gateway GP6 PC.

My new machine (running Feisty) has no serial ports, so I bought a Sunix
4079T PCI serial card, (which Feisty seemed to recognize ok) but now a
weird thing happens when I try to use it with the Dynalink e-modem....

Everything initially works fine. I can configure PPP and connect to
my ISP. The first web page loads fine at the usual dialup speed
I'm used to on the older machine running Edgy. But then something
seems to go wrong on the new machine. Hardly any data gets through
(the SD/RD lights on the modem only light up occasionally, even though
I'm still trying to download other webpages). After a while, PPP shuts it down,
and the PPP log says "serial link appears to be disconnected. No response
after 4 echo requests". After a short pause, it re-dials, re-connects
ok, the first page loads ok as before, but subsequent ones have
the same problem. And so it continues. This never happens with exactly
the same modem using Edgy on my older PC. I'm wondering whether
there's something wrong with the Sunix PCI serial card. (?)

Anyway, the reason I'm posting this here in this thread is that
someone asked whether USB-to-serial dongles definitely worked.
I don't know, but I'm willing to gamble some money to try it if
someone tells me more precisely what to buy. Is "USB-to-Serial Dongle"
the correct term for this thing, or does it also go by other names?

And separately, does anyone know of a PCI serial card that *definitely*
works fine with Feisty?

---

### Post by Bartender on 2007-06-18
[http://www.usbgear.com/computer_cable_details.cfm?sku=U232-P9AP&cats=199&catid=199%2C601%2C461](http://www.usbgear.com/computer_cable_details.cfm?sku=U232-P9AP&cats=199&catid=199%2C601%2C461)

Says it's supported in Linux kernel 2.4 and higher.  Try it out for us and report back, OK? :D

Here's another.  Although the article is about Palm devices specifically it still might be helpful - mentions where you are likely to find the device after hooking up via adapter.  Also mentions Keyspan as a source for Linux-compatible dongles.  Keyspan keeps showing up in my searches.

[http://www.askdavetaylor.com/can_i_run_linux_on_my_palm_v.html](http://www.askdavetaylor.com/can_i_run_linux_on_my_palm_v.html)

---

### Post by strangerep on 2007-06-18
> **Bartender said:**
> [http://www.usbgear.com/computer_cable_details.cfm?sku=U232-P9AP&cats=199&catid=199%2C601%2C461](http://www.usbgear.com/computer_cable_details.cfm?sku=U232-P9AP&cats=199&catid=199%2C601%2C461)

Says it's supported in Linux kernel 2.4 and higher.
Try it out for us and report back, OK? :D
Hmmm. I smell a rat. It says that the device derives its power from the usb port.
I have a Netcomm AM5055 USB modem which also derives power from the
computer's USB port. Under Vista, (after installing Netcomm's drivers), the AM5055's
power light and terminal-ready lights came on and stayed on.

But on the same machine (after ditching Vista and installing Feisty), the modem's
power & terminal-ready lights came on, then went off after a few secs, then came
on again, and so on cyclically.

On a different machine running Edgy, the modem's power light comes on stays on.
But the terminal-ready light comes on initially, then goes off and stays off.
"lsusb" shows something at a usb device address, but when I attempt to use it
for PPP to establish dialup, the PPP log file just says ppp timed out after sending the
initial "ATZ" string and waiting for an "OK" to come back. So something
(different) was also seriously wrong on Edgy.

Some kind of driver appears necessary on Feisty just to keep power to the
USB port, and to keep the modem in terminal-ready state. (Nothing else was
on the USB bus in either case.) So something is clearly deficient/absent in
the Ubuntu kernel.

Here's another possible piece of the puzzle: over on linux-usb.org, they say
that the "CDC" and "ACM" modules must be present in the kernel. When I
do an "lsmod" on Edgy and Feisty, nothing even remotely like "cdc" or "acm"
appears.

Linux-USB.org also says:

> You need to select the **USB Modem (CDC ACM) support**
kernel option. If you build as modules, you need to install the acm.o option.

So... is there an easy way to find out what options a given Ubuntu kernel
was built with? (I presume Ubuntu takes the kernel source from Linux HQ,
and then builds it with Ubuntu's choice of options?) If so, maybe it's a case of
"*kernels ain't kernels, regardless of what the version numbers might be*".
It might depend on what options are compiled-in by default with each distro.

---

### Post by Bartender on 2007-06-19
But does your Netcom modem fail because it's not a hardware modem?

Or because of some weird power problem like you describe?

EDIT: From what I can see at the Netcomm website that modem doesn't appear to be full hardware...

---

### Post by strangerep on 2007-06-19
> **Bartender said:**
> But does your Netcom modem fail because it's not a hardware modem? Or because of some weird power problem like you describe?
From what I can see at the Netcomm website that modem doesn't appear to be full hardware...
I think that last bit is right. The Netcomm modem is not a full hw modem.
If I could find an external full-hardware USB 56K modem I would try it.

The phenomenon I found curious is that the power light comes on and stays on
under Edgy on my old PC, but slowly blinks on/off for my new PC under Feisty.
I can't load Edgy on my new PC because the older kernel doesn't have the drivers
for the newer motherboard's chipset. And I can't risk loading Feisty on my older
machine because it's the only working computer I've got right now.

The only other USB device I've tried on the newer machine is a (wired) mouse,
whose LED comes on, stays on, and functions perfectly all the time on both
machines. So now I'm thinking maybe it's not hardware problem, at least
not on the motherboard and USB ports.

I guess what you're implying is that if I bought a USB-to-serial adapter it might
work ok with my serial Dynalink modem? If so, the thing I'm still not crystal
clear about is whether those adapters need some kind of driver, or whether
they function quite independently after merely plugging them in - drawing
only a small amount of power from the USB port. (?)

EDIT: several hours later, I now understand the USB->Serial dongle thing
a bit better. I figured out how the linux kernel dynamically loads and
unloads ".ko" modules, and found out where they live. The upshot is that
support for Belkin, Keyspan, and ATEN USB->serial devices has been
around for a while now. In the case of the ATEN UC-232A, one needs to
know that it actually uses the Prolific PL-2303 chip, and the relevant
linux kernel module is called pl2303.ko. I found a brief message on a
local linux user group:

 [http://lists.slug.org.au/archives/slug/2006/11/msg00477.html](http://lists.slug.org.au/archives/slug/2006/11/msg00477.html)

which says that the ATEN UC-232A works out of the box (including
the ability to pass through a 'break'). So I'm going to invest in
one of these to try out. It will probably take several days to get
hold of it though, but I'll report back here eventually. :-)

<End Edit>


[Oh, and thanks for your ongoing help and patience, BTW.]

---

### Post by Bartender on 2007-06-20
> **guysmiley25 said:**
> Hmm, even if they did cut you off, could you not just resume your update?

Good question.  Our ISP (Juno) does not play nice with Linux so I don't have any real-world experience.  Any dial-up folks care to respond??

---

### Post by earther on 2007-06-21
I understand your problem very well.   After much frustration, I found a $3.95/150hr month connection from VTISP.  No email, no tech support, just a bare connection.  Works with Linux and Windows.  Can't remember ever being dropped. I keep Juno as a backup connection for times that I'm on Windows. (Yeah  . . . still have one foot in each world.)

---

### Post by strangerep on 2007-06-23
I promised earlier to report back on what happened with
an ATEN UC232A usb<->serial adapter,

Short answer: it works **perfectly**, right out of the box.
I.e: it works fine on both my old machine running Edgy,
and my new machine running Feisty. (This is with an
external serial full-hardware modem, a Dynalink 56k
e-modem II.)

Although it comes with a CDROM, you don't need it
for modern versions of the linux kernel. The only
thing on the CDROM relevant to linux is the driver
source and a Makefile. But that driver is already
included with modern linux kernels.

As soon as I plug in the usb side, I get a new
device called /dev/ttyUSB0. (If you have other
usb tty devices, I guess the number would be
different.) Then, after reconfiguring PPP to use
this new device, my dialup internet connection
works fine.

(Actually, I had a couple of software config
problems with PPP on Edgy when it silently
removed a "noauth" statement from my
/etc/ppp/peers/ppp0 file. But that's nothing
to do with the hardware. Once I added the
statement back into that file, everything
worked perfectly.)

EDIT: For thoroughness, I just re-tried again using
my Sunix 4079T PCI serial I/O card. It still fails
in the same way: some data gets through initially,
but then gradually dries up. Conclusion: I won't
be buying a Sunix product again.

---

