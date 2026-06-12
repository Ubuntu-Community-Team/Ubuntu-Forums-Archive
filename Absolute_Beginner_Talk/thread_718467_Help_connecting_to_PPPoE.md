---
title: "Help connecting to PPPoE"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by swarup on 2008-03-08
For the past 48 hours I have been trying to get my Gutsy Dell laptop online using my ADSL broadband PPPoE connection. I first tried using the pppoeconf application. Everything seemed to go fine with the install, and the computer went online. But strangely, the only site it could go to was google and google-related sites like google photos, google books etc. It worked smoothly and with good speed, but would not go to ANY other website beside google. Yahoo etc, any other website it would not go.

So I found an alternate installation mode using a file called rp-pppoe-3.8.tar.gz, with which many PPPPoE users have experienced success. Again, the installation went quite smoothly with no error messages. And at the end, the installation announced (in terminal) that it had gone online successfully and everything was working fine. The test also went fine. But when I myself opened Firefox and tried to browse, it wouldn't go anywhere. Not even to google, where it used to go. I tried Add/Remove and Synaptic package manager, but nothing is working. The applet says the computer is online, and shows the packets being sent and received. But practically, the computer cannot go to any website and cannot download any software.

I am concerned that perhaps I have not put in the correct settings. My server company--VSNL--says the IP is 192.168.1.1. But I do not know: does this number belong under Connection Settings where it says "IP Address", or instead does it belong in the window for "DNS Server"?. And then there is also the "Gateway Address". 

The rp-pppoe-3.8.tar installation only asks for the "IP address of your ISP's primary DNS server". And if I put something in for that, then it gets entered in the "DNS Server" window. But then what about the "Connection Settings" where there is a window for "IP Address".

I am totally confused, and do not understand why this Gutsy machine will not go online. The same ADSL PPPoE connection I use everyday with my WinXP desktop, and the connection works wonderfully. So why not with Gutsy? I am sure it is some simple settings problem. If someone could please lend a hand, I would be so grateful.

---

### Post by mikeyphi on 2008-03-08
Have you looked at this guide? [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by swarup on 2008-03-08
> **mikeyphi said:**
> Have you looked at this guide? [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

Yes, thank you I have been there. That is the procedure I followed yesterday--the pppoeconf tool--using which I was only able to go to google. Then today I tried another tool, detailed above, which left me without any activity at all. Although in terminal when I type "pppoestatus" as a check, it comes back with "Link is up and running on inteface ppp0". So the utility thinks it is on-line--and the applet monitor shows it to be sending and receiving packets--but in the practical world neither can I surf the web, nor can I download software or get Gutsy updates.

---

### Post by mikeyphi on 2008-03-08
You must have had an Internet connection when you viewed the Google site.
Have you checked in Firefox - Edit/Preferences then under the Advanced/Network tab, see what the connection settings are.

---

### Post by swarup on 2008-03-08
> **mikeyphi said:**
> You must have had an Internet connection when you viewed the Google site.
Have you checked in Firefox - Edit/Preferences then under the Advanced/Network tab, see what the connection settings are.

Actually, since then I've found out what the problem was. Here in India, the VSNL ADSL broadband provider did not provide us with a manual, as a result of which I had no idea of what the actual settings for "DNS Server IP addresses" was supposed to be. Someone else had suggested some ad hoc values, but they really weren't working properly. Ultimately I went online with another computer and, searching google, found the actual VSNL manual and was able to properly set the settings in rp-pppoe. Now it goes online fine, and browses to any site I wish!

But my problems do not seem solved yet, because I now find that the gutsy updates are not coming. I've just installed Gutsy, and there should be loads of downloads. But not one is coming. 

I'm trying to download an application (Wine Windows Emulator) in Add/Remove, and it is downloading...but SO slowly, slower then even any dial-up connection I've seen in the past. --And this is supposed to be a broadband connection. It is downloading at rates of mostly in the range of b/s (not even kb/s). Sometimes it jumps up briefly as high as 15-18 kb/s but only briefly. It has already been an hour trying to download Wine, and still not finished. It makes me think that something may still not be proper in the pppoe setup? Because when I connect with my WinXP machine the download speeds are fine. So for some reason, my pppoe connection is not able to access fully the available bandwidth, the way the XP machine does.

---

### Post by spiderbatdad on 2008-03-08
[http://ubuntuforums.org/showthread.php?t=693309](http://ubuntuforums.org/showthread.php?t=693309)

---

### Post by swarup on 2008-03-09
> **spiderbatdad said:**
> [http://ubuntuforums.org/showthread.php?t=693309](http://ubuntuforums.org/showthread.php?t=693309)

Excellent. Solved at least various major major issues. Synaptic got updated in the terminal window with all the resources. And now the auto gutsy download update icon has shown up with** 205 updates** available. Others were saying that there are no available updates. But I knew this was not correct. You helped me in a big way. Many thanks! :)

****I would say your post should be broadly announced so that all should know about it. It should be included in the Ubuntu installer cd as a message there during the install--to go to this site you gave, so that you will be able to enable the resources. Otherwise who will know??*****

Thanks again!

---

### Post by kleo skywalker on 2008-03-09
swarup, you have another [thread]("http://ubuntuforums.org/showthread.php?t=717255") going about the same problem. I posted there twice giving the precise steps you needed to follow to find out things like IP address and DNS servers for your VSNL connection, and where to put these values.
Like I said in my post there, I got an MTNL connection going that way, and VSNL and BSNL work in a very similar manner.
Following those simple instructions would have saved you a lot of time and hassle.

---

