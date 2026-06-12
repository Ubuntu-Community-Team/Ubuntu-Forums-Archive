---
title: "how do you setup up adsl internet connection"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by sts71 on 2006-10-28
Hi Guys

After much frustration and pulling of hair, I finally have ubuntu dapper drake 6.06 installed!

The peasants rejoiced!

Now being a total windoze user Im trying to connect to the internet and being a total newbie having trouble getting connected to the net.

Details

IBM P3 300PL pc with onboard ethernet connection etc(pretty standard pc) this is only os on this machine, it repartitioned and setup itself thru text install and now I have the pretty gui thing and flying toasters screensaver (long live afterdark screensaver eh?)
Net connection is bigpond adsl modem connected via ethernet cable.
Ive tried to go thru menuas and havent got anywhere, do I need to install drivers for this? the xp machine deects it automatically and no real parameters to be set so how do I do it on linux?
Ive tried going thru other posts to find something, and hopefully my question might help other newbies, so far Im loving this linux os, has all the apps I need to start working just need to work out this net connection (im sending this via xp unit)

Thanks in advance,

Steve

---

### Post by rfruth on 2006-10-28
I had forgot about the flying toasters - anyway does Ubuntu see your ethernet card (lshw or better yet System > Admin~Network Tools) ? Here is mine & all is well (no driver)

[ATTACH]18427[/ATTACH]

---

### Post by sts71 on 2006-10-28
rfruth,
when i click admin network, a window appears with tabs devices/ping/netstat/traceroute/portscan/lookup/finger/whois

netwrok device is listed as loopback interface(lo) and if i click that there are no oother options, does this mean I need more drivers?
my network tools screen looks exactly like your attachment
thanks for replying too :)

---

### Post by NeoLithium on 2006-10-28
For ADSL, open up a terminal window, and type ```
 sudo pppoeconf 
```
It'll open up a nice little setup system that will get you connected with your ADSL :)

---

### Post by sts71 on 2006-10-28
woohoo its working thanks guys so much

now i just gotta learn about how to drive this and where and what to save to and all that kinda newbie stuff

appreciate the fast responses

cheers
Steve

---

### Post by NeoLithium on 2006-10-28
No problem :) Glad it's working; it all actually comes quite easier than someone would expect with patience and practice.

Welcome to the happy world of ubuntu!

---

### Post by psycosmyth on 2006-10-28
Mister Anderson!!




I looked for that command a while back, thanks! A key note:write commands down when your forgetful:rolleyes:

---

### Post by sts71 on 2006-10-28
thats a great idea

thanks again

---

### Post by NeoLithium on 2006-10-28
*Laughs* Yeah; I have a whole book. Everytime I end up testing distros and stuff; moving around between ubuntu releases; I always find new little tips and things that make life easier that I always right down.

---

### Post by bteck on 2007-01-28
> **rfruth said:**
> I had forgot about the flying toasters - anyway does Ubuntu see your ethernet card (lshw or better yet System > Admin~Network Tools) ? Here is mine & all is well (no driver)

[ATTACH]18427[/ATTACH]

With Ubuntu, I have problem connecting to the Internet too.  I am using an adsl wireless router.  In WindowsXP, I could connect to Internet using wireless or wired with the router.

Here are my attempts to get connected.
In Ubuntu, I first setup my network by running [System->Administration->Networking].  At the [Connection] tab, 3 connections were listed, viz Wireless, Wired and Modem.  I selected [Wireless connection] and the computer responded by showing "Activating network interface ...".  After which I clicked [Properties] and selected [Enable this connection]. I also set my [Network name], [Password type] and [Network password] correctly.  At the [Connection settings - configuration], I selected 'Automatic Configuration (DHCP)' and close the window.

I then ran [System->Administration->Network tools]. In its [Device] tab, I clicked on [Network device] and it listed 'Loopback Interface (lo), Ethernet Interface (eth0 and eth1)'.  At the [Ping] tab, I set [Network address] to 192.168.1.1 to point to my router's built-in home page, and clicked [Ping].  I did get proper responses '64  192.168.1.1  1  0.782ms'
(By the way, if I disable the [Wireless connection] via [System->Administration->Networking], then when I ping 192.168.1.1, I did not get a response.  This clearly showed that my wireless connection to the router was ok.)

From Firefox, I could access this router's built-in home page and ran its diagnostics.  Test results were: Interface (PC to Modem): Pass; Modem: Pass; Modem to ADSL line connection: Pass.  Also, at the router home page, it shows DSL: Up; Internet: Connected.

But, when I tried to connect to yahoo, google, or any Internet sites, Firefox reported 'The connection has timed out' 

I repeated the above test using [Wired connection] and disabled the [Wireless connection].  The results were similar, meaning it seemed I was able to connect to my router but not the Internet.

I also tried running 'sudo pppoeconf' in the Terminal.  It reported 'I found 2 ethernet devices: eth0, eth1'.  'Are all your ethernet interfaces listed above?'  I pressed 'Yes' to the question.  It then scan the devices and finally reported: "Sorry, I scanned 2 interfaces, but the Access Concentrator of your provider did not respond. ..."

What was the problem and what can I do to establish connection to the Internet?

Thanks in advance for any asssitance.

---

### Post by bteck on 2007-01-30
I am so happy! I am finally able to connect to the Internet.  The problem was due to ipv6 setting  in Firefox. Thanks to 'linuxpimp' for the solution.

My experience here may be helpful to some newbees.  To start with, my first attempt at installation of Ubuntu 6.10 to my Acer Travelmate 6000 was smooth.  Now that things are working fine, I can confirm that Ubuntu was able to automatically and properly setup my LCD screen resolution, and it also detected my ethernet and wireless card properly.  

However, at the time when I was struggling with my Internet connection for 2 days, I did not realize that the actual problem was due to the ipv6 setting in Firefox.  I was attempting to connect to Google.com and Yahoo.com without any success.  Firefox just timed out!  On the 2nd. day, I tried a local site and was somehow able to connect to it after numerous attempts.  But connection to Google and Yahoo are still not possible.  This same problem was also reported by others in Ubuntu forum.  That's how I found the answer.

I repeat linuxpimp's solution below for the convenience of some. 
1. Run Firefox
2. At its address bar, type "about:config" (without the " marks).  You should see a listing of names
3. At its filter bar, type "ipv6".  This should show you the reference name "network.dns.disableIPv6" with its value shown as 'False'
4. Double-click this 'False' value and it will change to 'True'
5.  That's it.  Try connect to the Internet now.  

I found another suggestion by linuxpimp to speedup Firefox to be useful too.  Google search for 
"firefox" "hack" "pipelining" at [http://www.hackaday.com](http://www.hackaday.com) for the tips.

Thank you linuxpimp. Keep up the good works!

---

### Post by blueyoda on 2007-02-27
Thanks guys I've had soo much trouble getting the internet to work that I almost thought about packing it in. 

I found it interesting that when I tried to use [pppoefing] it didn't fine anything but I could ping my router from both cable and wireless conections. My problem was resolved with the change to my Firefox settings :) nice one

Thanks again all, you have saved another soon to be very happy Ubuntu user.

---

