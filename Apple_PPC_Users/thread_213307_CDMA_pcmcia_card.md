---
title: "CDMA pcmcia card"
date: 2006-07-11
forum: Apple PPC Users
---

### Post by davidmaxwaterman on 2006-07-11
Hi,

I'm in China and want to be able to get wireless internet using the mobile network. I'm not 100% sure about all the technical details, but I think they use CDMA (but not 3G), if that makes any sense.

I want to use it on my Apple TiBook G4/800 DVI which is running ubuntu (the latest released one - forget the name).

Does anyone have any recommendations? If I need to give more info, please ask.

Thanks!

Max.

---

### Post by kagashe on 2006-07-11
Hi,

I am from India. We also have 2 CDMA mobile operators (Reliance and Tata Indicom) who supply imported cards and some work on Linux. The most popular was Sierra wireless card.

Recently, I have tested HUAWEI EC321 card supplied by Tata Indicom which works on Dapper Live CD. Here is [my post]("http://ubuntuforums.org/showthread.php?t=208749") regarding this card.

Please post the name and model of the card you would like to use or search on Google adding "Linux" to it so that its usability in Linux could be determined.

Please note that generally manufacturers/suppliers do not care whether the card will work on Linux or not so you have to do your homework before buying.

kagashe

---

### Post by davidmaxwaterman on 2006-07-11
> **kagashe said:**
> Hi,

I am from India. We also have 2 CDMA mobile operators (Reliance and Tata Indicom) who supply imported cards and some work on Linux. The most popular was Sierra wireless card.

Recently, I have tested HUAWEI EC321 card supplied by Tata Indicom which works on Dapper Live CD. Here is [my post]("http://ubuntuforums.org/showthread.php?t=208749") regarding this card.

Please post the name and model of the card you would like to use or search on Google adding "Linux" to it so that its usability in Linux could be determined.

Please note that generally manufacturers/suppliers do not care whether the card will work on Linux or not so you have to do your homework before buying.

kagashe

OK, wonderful :)

The HUAWEI EC321 is reported to work well here, but I've only heard reports on MS Windows/Intel.

You mention that you rebooted to Windows in order to get the DNS server's IP addresses. That would mean you're not using a PPC based Apple (or not an Apple at all)...note that I am asking about a TiBook.

Any guesses as to whether it would work in a TiBook? It has a slot, which I assume will take a PCMCIA card.

Thanks for your help!

Max.

---

### Post by kagashe on 2006-07-11
> **davidmaxwaterman said:**
> OK, wonderful :)

The HUAWEI EC321 is reported to work well here, but I've only heard reports on MS Windows/Intel.

You mention that you rebooted to Windows in order to get the DNS server's IP addresses. That would mean you're not using a PPC based Apple (or not an Apple at all)...note that I am asking about a TiBook.

Any guesses as to whether it would work in a TiBook? It has a slot, which I assume will take a PCMCIA card.

Thanks for your help!

Max.When you connect to internet through pppd on any Linux system the DNS servers are automatically copied in /etc/resolv.conf file and used by the browser. When you use live CD pppd can't write to this file so I had to put it manually. Since the machine on which I tested this card had Windows XP in dual boot I rebooted to Windows XP just to get the DNS nos. Had it been a purely Linux machine I would have called the ISP on phone to get the DNS nos.

I think this card should work on any machine on which Ubuntu 6.06 is installed.

Oh! This is my 100th post.

kagashe

---

### Post by davidmaxwaterman on 2006-07-11
> **kagashe said:**
> When you connect to internet through pppd on any Linux system the DNS servers are automatically copied in /etc/resolv.conf file and used by the browser. When you use live CD pppd can't write to this file so I had to put it manually. Since the machine on which I tested this card had Windows XP in dual boot I rebooted to Windows XP just to get the DNS nos. Had it been a purely Linux machine I would have called the ISP on phone to get the DNS nos.

I think this card should work on any machine on which Ubuntu 6.06 is installed.

Oh! This is my 100th post.

kagashe

OK, great. Based on this, I think I'll go ahead and get one :D

Thanks!

Max.

PS. Congrats on the 100th :)

---

### Post by kagashe on 2006-07-12
> **davidmaxwaterman said:**
> OK, great. Based on this, I think I'll go ahead and get one :D

Thanks!

Max.

PS. Congrats on the 100th :)
Ok. Here is how you should proceed.

If you boot into Ubintu 6.06 with the card plugged-in please note that the card is detected as "ttyUSB0". (You can also confirm this from /var/log/messages file).

The HUAWEI EC321 card should have the CDMA SIM card of your mobile operator inside it and you should get the activation instructions from them. The activation instructions of Tata Indicom here are very simple and are as follows:
> Telephone No to be dialled #777
Userid: internet
Password: internet
and it is set up in Ubuntu 6.06 as follows:
> Click on System/Admonistration/Networking
If you have any ethernet connection to internet please select and Deactivate it.
Click on DNS tab
If you have anything in DNS Servers (you might have the servers of your current ISP) please select and Delete all the entries.
Click on Connections tab
Select Modem connection
Click on Properties
Check Enable this connection
Enter Phone number: #777
Enter Username: internet
Enter Password: internet
Click on Modem tab
Enter Modem port: ttyUSB0
Click on: Ok
Click on: Activate

Now check your internet connection by pinging [www.google.com](www.google.com) and/or by surfing. If you could not access Google/any other site.

Click on System/Admonistration/Networking
Click on DNS tab
Please see whether DNS server entries of your mobile operator have appeared or not. (Generally pppd gets them when you click on activate).

If you don't see the DNS servers please call the ISP and get them and enter manually and it should work.

If your mobile operator has anything other than Userid and password (e.g. a pin number for activation) please get the card pre-activated. There are ways in pppd to pass on the pin number etc. but I can't guide you for this because pppd is too complicated for me to understand this aspect.

Best of luck with your new HUAWEI card.

kagashe

---

### Post by davidmaxwaterman on 2006-07-15
Well, I bought the card today, and it works 'out of the box' so to speak.

Awesome :D

Thanks for the advice!

Max.

---

### Post by kagashe on 2006-07-15
> **davidmaxwaterman said:**
> Well, I bought the card today, and it works 'out of the box' so to speak.

Awesome :D

Thanks for the advice!

Max.
You are welcome.

Not exactly "out of the box" but close enough. Did Ubuntu detect the modem at "ttyUSB0" or you entered the "Modem port" manually? I mean did you try the "autodetect" button on "Modem" tab?

kagashe

---

### Post by davidmaxwaterman on 2006-07-15
> **kagashe said:**
> You are welcome.

Not exactly "out of the box" but close enough. Did Ubuntu detect the modem at "ttyUSB0" or you entered the "Modem port" manually? I mean did you try the "autodetect" button on "Modem" tab?

kagashe

I just had to copy the wvdial config file from my friends computer (he used the USB version, which also worked fine).

After that, I just ran 'wvdial cdma' ('cdma' is the name in the configuration) from a terminal and it just worked.

Max.

---

### Post by kagashe on 2006-07-16
> **davidmaxwaterman said:**
> I just had to copy the wvdial config file from my friends computer (he used the USB version, which also worked fine).

After that, I just ran 'wvdial cdma' ('cdma' is the name in the configuration) from a terminal and it just worked.

Max.

Got it. The wvdial config file which you used must be pointing to the right device (ttyUSB0).

The method suggested by me also works fine when you enter the modem port (ttyUSB0) on the modem tab and you don't need wvdial or kppp etc.

kagashe

---

### Post by davidmaxwaterman on 2006-07-17
> **kagashe said:**
> Got it. The wvdial config file which you used must be pointing to the right device (ttyUSB0).

The method suggested by me also works fine when you enter the modem port (ttyUSB0) on the modem tab and you don't need wvdial or kppp etc.

kagashe

OK. I've now had a few moments to try the network admin panel to configure it.

However, as before, I find the network admin panel to be extremely flakey. It takes a long time to switch locations and it often just doesn't seem to do it.

For example, in this case, I created another location called 'cdma' - I disabled (on the 'properties' button) 'wireless connection' and 'ethernet connection', and configured 'modem connection' as you described. Clicking 'ok' made it think for a while, then the window disappears. When I check the interfaces (/sbin/ifconfig), only lo0 exists.

I don't recon much to that tool :|

I wonder if anyone else has any trouble with it?

Max.

---

