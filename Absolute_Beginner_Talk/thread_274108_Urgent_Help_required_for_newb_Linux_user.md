---
title: "Urgent Help required for newb Linux user"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by BigLebowski on 2006-10-09
Hello, i am very new to linux and ubuntu, i plan to use this OS for internet and Windows for gaming but one major problem stands in the way.. i am having trouble getting my usb **D-LINK DSL200 modem** to work, dispite being fully connected and perfectly functional.(Modem runs days on end in windows without trouble)

Having a look around i can see that Ubuntu is picking up some info about the modem..

[http://img91.imageshack.us/img91/6806/screenshot1ew7.png](http://img91.imageshack.us/img91/6806/screenshot1ew7.png)

But of course still not working(Unlike my printer which worked from the get-go) so i looked around for some guides found a few which basicly had the same solution. 

So i found this guide: [http://www.linuxquestions.org/hcl/showproduct.php?product=1950](http://www.linuxquestions.org/hcl/showproduct.php?product=1950)

In step 1 it told me to download the drivers from:
[http://eciadsl.flashtux.org/download/nortek-2021/](http://eciadsl.flashtux.org/download/nortek-2021/)

Which i did and i burned them to a disc, opened the .deb file up in Ubuntu(I do not know what to do with the other files...) and got this error message: [http://img45.imageshack.us/img45/4282/screenshotrs3.png](http://img45.imageshack.us/img45/4282/screenshotrs3.png)

I have no idea why this error comes up, so i went and downloaded the newest drivers(0.11, AMD64 Version) and when i opened the .deb file up in Ubuntu i get this error:

[http://img123.imageshack.us/img123/3018/screenshot2sp6.png](http://img123.imageshack.us/img123/3018/screenshot2sp6.png)

Gah:confused: I just don't know what to do, without the Internet Ubuntu is useless to me, as which i stated before i plan to use as Internet OS(And everything non Game related) and Windows as Games OS.

Heres some information that may help any one who is trying to help me:

CPU: AMD64 3500+
HDD: 300GB Sata (Partitioned into 4, Windows, Ubuntu, Games, Files)
Ram: 1GB
GFX: Nvidia 6800GT Overclocked PCI-E
Sound: Audigy 2 ZS
Internet 512/128 ADSL


[SIZE="4"]Modem Information[/SIZE]: 
"Manufacturer:	D-Link
Model:	DSL200 rev B
Status:	  Supported (Meaning supported by [http://eciadsl.flashtux.org/](http://eciadsl.flashtux.org/) Drivers)
Driver mini:	0.11
Vid1/Pid1:	0915,2001 / 8102,5100
Vid2/Pid2:	0915,2001 / 8102,5100
Country:	Australia /
Lithuania /
Egypt /
Russia /
UK
Provider(s):	TPG /
Lietuvos Telekomas /
? /
WebPlus /
Pipex UK
VPI.VCI:	8.35 /
? /
? /
1.32 /
0.38
Synch .bin:	gs7470_synch04.bin or 06 or 17
Chipset:	GS7470
Synch alt:	5
Pppoeci alt:	1
Info:	-"


Please help a newb in need.

---

### Post by Ocxic on 2006-10-09
have you tried to use the ethernet port? If there is one try thst, ethernet is faster then USB anyway.

---

### Post by lemonsCC on 2006-10-09
The second error is a dependency issue...Is there a package called pppoe you can install?  My internet worked so I am just stabbing in the dark.

---

### Post by BigLebowski on 2006-10-09
> **Ocxic said:**
> have you tried to use the ethernet port? If there is one try thst, ethernet is faster then USB anyway.

Would a USB modem be able to plug into an ethernet port?(If i have one..)

---

### Post by gn2 on 2006-10-09
> **BigLebowski said:**
> Would a USB modem be able to plug into an ethernet port?(If i have one..)

No, it wouldn't.

Your easiest option is to buy a compatible ADSL Modem Firewall Router for example a Netgear DG834G which I can assure you is a wonderful piece of kit and is 100% Ubuntu compatible.

Obviously this will cost, but you could sell existing modem on eBay to recoup some cash?

Or spend hours mucking about to maybe get (not as good) USB modem going.

Decisions decisions.....

---

### Post by BigLebowski on 2006-10-09
Well i was actually looking for a router... and it looks like DG834G is that too, but about it being wireless.. is that just for wireless broadband.. because i have no plans to ever use wireless.

---

### Post by BackInTimeMan on 2006-10-10
> **BigLebowski said:**
> Well i was actually looking for a router... and it looks like DG834G is that too, but about it being wireless.. is that just for wireless broadband.. because i have no plans to ever use wireless.

No, it's not just for wireless, it has four wired ports as well as the wireless facility. Version 3 is the latest model. I have one and agree with gn2, it's a nice router.

---

### Post by BigLebowski on 2006-10-10
Thanks for the replys, im gonna order in that router you suggested, but it sucks that my modem works in windows and not ubuntu.

It would defeat the purpose for people(Not including me.. ill be buying Vista and dual booting with Ubuntu)that don't want to spend money on Vista(Or any other OS) because they don't like it or they can't afford it and have come here and find out they have to pay over $100 to be able to use it, but lucky for me.. i did not come to Ubuntu because it was free... id pay what ever.. because it offers a more secure method for surfing the net.

---

### Post by gn2 on 2006-10-10
> **BigLebowski said:**
> Thanks for the replys, im gonna order in that router you suggested, but it sucks that my modem works in windows and not ubuntu.

It would defeat the purpose for people(Not including me.. ill be buying Vista and dual booting with Ubuntu)that don't want to spend money on Vista(Or any other OS) because they don't like it or they can't afford it and have come here and find out they have to pay over $100 to be able to use it, but lucky for me.. i did not come to Ubuntu because it was free... id pay what ever.. because it offers a more secure method for surfing the net.

Remember that the router has a built-in hardware firewall which is a VERY good thing.

Although you have no plans to go wireless now, it might not always be that way...

If you want to have more than one PC on-line at a time you would need an additional modem anyway.

Cheaper routers are available for those on a tight budget.

Remember you can get some money back by selling the USB modem on eBay.

Wouldn't bother with Vista, a complete waste of money. 
Nothing new of any real significance, it's all Window-dressing.

---

### Post by mahy on 2006-10-10
> **BigLebowski said:**
> Thanks for the replys, im gonna order in that router you suggested, but it sucks that my modem works in windows and not ubuntu.


Agreed, but remember, D-Link's the one to blame. USB modems in general are a major headache for prospective Linux users. Stick with ethernet. Rumor has it that some people managed to get it working, but i'm yet to meet such one.

Mahy

---

