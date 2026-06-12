---
title: "Ndiswrapper USB Wireless problem"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2006-03-18
I've been wrestling with some Ndiswrapper complications for 1 whole month now.
Trying to solve my USB pentype Wireless in Ubuntu.
And also the so called chipset List link in the Wiki I found this about my wireless:

> Card: Asus WL-161, 11mbps

* Chipset: Sis162u USB
* [COLOR="Sienna"]usbid: 2821:0161[/COLOR]
* Driver: CDRom, WinXP driver. (sis162u.inf, original at [www.sys.com](www.sys.com))
* Other: Use [COLOR="Sienna"]"ndiswrapper -d 2821:0161 sis162u"... to get Hardware present.[/COLOR] It works perfect on 11 mbps!
With those fact you might be able to see what I'm doing wrong.
OK, so these are the procedures that I did but didn't make the Internet work.

> mike@Compaq:~/Linux$ **cd drivers**
mike@Compaq:~/Linux/drivers$ **ls**
sis162u.inf sis162u.sys
mike@Compaq:~/Linux/drivers$ **sudo ndiswrapper -i sis162u.inf**
Password:
Installing sis162u
mike@Compaq:~/Linux/drivers$ **sudo ndiswrapper -l**
Installed ndis drivers:
sis162u driver present
mike@Compaq:~/Linux/drivers$ **sudo modprobe ndiswrapper**
mike@Compaq:~/Linux/drivers$ **sudo depmod -a**
mike@Compaq:~/Linux/drivers$ **sudo modprobe ndiswrapper**
mike@Compaq:~/Linux/drivers$ **ifconfig**
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:11519 errors:0 dropped:0 overruns:0 frame:0
TX packets:11519 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1033987 (1009.7 KiB) TX bytes:1033987 (1009.7 KiB)

When checking for the Asus USB Wireless I can't find the name wlan0 anywhere:
> 
mike@Compaq:~$** lsusb**
Bus 001 Device 005: ID [COLOR="Sienna"]2821:0161[/COLOR]
Bus 001 Device 004: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 4 50L Optical Mouse
Bus 001 Device 002: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 001 Device 001: ID 0000:0000

What am I doing wrong? I've spent almost 2 months reading up in Wiki on all the material of Ndis and I don't want to go over the whole experience of trying to uninstall Ndiswrapper and compiling the newest version again. That attempt occupied one whole month without solving anything and worst there wasn't any support for that.
So with that in mind my ifconfig knowledge is minimal at this point :cry:

---

### Post by Zelut on 2006-03-18
Well lets see if we can get it figured out..

From your post above I do notice that when using 'ndiswrapper -l' it only lists the driver as being present, not the hardware.  Thats a pretty critical stopping point right there.

Did you get the driver to match your usbid or the chip?  In many cases the usb/pcid is the critical part.  You can disregard any chip manufacturer/make/model as long as the usbid matches on the ndiswrapper wiki.

We'll need to find YOUR usbid and then try to match the driver.  I have a small script that tries to output the correct ID for you.  Its found in my signature (on my home page).  What is your exact make/model/version?  Maybe I can help you find the right driver..

---

### Post by katarot on 2006-03-18
i have this exact same problem only with broadcom
you install it and it seems to be correct but wlan0 just wont show up 
i found a native broadcom driver somewhere 
just google for a native driver  im still stuck on how to install it tho

---

### Post by Zelut on 2006-03-18
katarot - you should be able to use my howto (in my sig) to get your broadcom working.  I use a broadcom chipset and it works for me everytime.

I suggest trying the Wireless 10 step combined with the script I wrote.  Let me know if does/doesn't help.  I'm sure we can get you working with broadcom.

---

### Post by dralaroc on 2006-03-18
Hey jingo,

I am a lin-rookie and if I may offer my .02.  I wrestled with my wireless adapter in breezy & dapper for 3 weeks.  I finally got it to work last night.  Try removing the Win Xp driver (inf) and go with the Win2K version of the .inf file.  When you do the "sudo modprobe ndiswrapper" & "sudo depmod -a"  thing disconnect your adapter and reboot.  Once logged in plug the adapter back in and see what happens.  

laroc

---

### Post by jingo811 on 2006-03-19
Tnx for your quick replies ppl :D
**kuyaedz>>>**
If I'm thinking what you're thinking then I don't think it's neccessary that I'll have to go through all the steps that you wrote maybe....
See my first post again I re-edited the USB id parts that you might have missed into the color [COLOR="Sienna"]brown[/COLOR].  I might not see wlan0 but I can see the specific USB id when typing in lsusb, [COLOR="Sienna"]2821:0161[/COLOR] would be my guess.
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#A](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#A)
number 36

But I will follow your steps more accurate if you think that I still need to, it's just gonna take some time.  Day job is kind of taking all of the time so I might reply with my test results very late in the future, weekly-late.

**dralaroc>>>**
I will try to switch the WinXP (.inf & .sys drivers) with Win2000 drivers.  Just give me some week before I reply again with the test results.
As I explained above day Job is taking all of my personal time and on top of that I'm having technical difficulties with my (Dual boot WinXP + monitor), (a:\-drive in Ubuntu), it's 2 long stories you don't have to pay attention to.  

I'll be back with some results next weekend OK.  Tnx again ppl for your time :KS

---

### Post by jingo811 on 2006-03-21
**dralaroc>>>**
Well the WinXP driver switch-aroo to Win2000 didn't make much difference.
Nor did the disconnect and reboot make any difference. But now at least we can check away some 
possibilities.

**All>>>**
Instead I tried a combination of **dralaroc** & **kuyaedz** words of wisdoms.  And finally got both driver and hardware present when typing: sudo ndiswrapper -l
But my instincts tell me that it no longer is some hardware problems I'm having, instead I think it's more like my router doesn't let my Wireless card any automatic entry.
Since I wanted some degree of sequrity when I'm not using WEP or have turned off BBSID, so I only typed in the Wireless-serial-ID for a certain amount of PCs to access the router.

But when everything was working in Windows I noticed oftenly that there are like 3-4 other routers within my home perimeter that belongs to the neighbours.  Maybe Linux:Ubuntu is confused as to wich correct router to connect to?
Seem like I have to do some more reading at here:
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29](https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29)
Which partly helped me to find out that I couldn't access my router when I pinged it 192.168.0.1 :-k  Seems like I have to learn how to configure and stuff before I can get proper wireless access
There's no free lunch when it comes to Linux it seems  :cry:

---

### Post by jingo811 on 2006-03-24
OK ppl now everytime I start Ubuntu:Breezy and I do:
ndiswrapper -l
I get feedback that both driver and hardware is present.

These are the steps I'm trying to follow from the Wifi wiki:
[https://wiki.ubuntu.com/WirelessTrou...8wireless](https://wiki.ubuntu.com/WirelessTrou...8wireless) %29
-----------------------------
1. Check device
2. Device drivers
3. Router Connection
4. ip assignment
5. Connected but no internet
-----------------------------

**1.) Check device**
1. sudo lshw [COLOR="Olive"]% doesn't show anything that I recongnize[/COLOR]
2. sudo lshw -businfo [COLOR="Olive"]% can't see any network class[/COLOR]
3. sudo lshw -c <class> [COLOR="Olive"]% can't define class for my USB Wireless[/COLOR]

1. sudo lsusb -v [COLOR="Olive"]% I see my Wireless:[/COLOR] [COLOR="Sienna"][Bus 001 Device 005: ID 2821:0161][/COLOR]
-----------------------------

**2.) Device drivers**
1. sudo lsmod [COLOR="Olive"]% can't see anything I recongnize[/COLOR]
2. lsmod | grep <driver name from lshw> [COLOR="Olive"]% can't do much from this point![/COLOR]
3. sudo modprobe <module> [COLOR="Olive"]% didn't see my module from lsmod![/COLOR]
-----------------------------

**3.) Router Connection**
1. sudo iwconfig [COLOR="Olive"]% nothing shows up, only something about no wireless extensions.[/COLOR]
2. sudo iwlist <Asus> scan [COLOR="Olive"]% there's some problem.[/COLOR]
-----------------------------

**4.) ip assignment**
1. sudo ipconfig [COLOR="Olive"]% I'm only assigned the local stack adress I think, 127.0.0.1[/COLOR]
2. sudo dhclient <Asus> [COLOR="Olive"]% nothing good happens here.[/COLOR]
-----------------------------

[COLOR="Red"]Alice need help Mr.Wizard :confused: [/COLOR]

---

### Post by jingo811 on 2006-03-27
Need help please.  Once again I've reached no-mans-land there's no more guides , FAQs and Wikis for me to read :-k :confused:

---

### Post by clareb on 2006-03-27
I don't know if I'm stating the obvious here for you but have you tried Linuxant driverloader? 
[https://www.linuxant.com/](https://www.linuxant.com/)
I struggled with my wireless usb adaptor for days and that was the only thing that worked. I know how it feels to go round and round in circles with the how-to's, wiki and forums and all that. Hope you get it sorted out soon.

---

### Post by jingo811 on 2006-03-28
Tnx for the tip clareb :KS now I have a new goal to aim for....
on the other hand if I don't see my chipset *Sis162* being supported on Linuxants list.  Does that mean that any attempts being made will be all futile?
And that I'm screwed and have to return back my hopes to ndiswrapper again??

---

### Post by clareb on 2006-03-28
Well, I'm really new to this game, but I'd give their free trial a whirl, you never know, it'll you tell during the install whether it's gonna work. When I was going round in circles with all this I started googling everything I could think of - being very specific - I found other forums with peope trying to solve the same problem and it was really helpful. If in doubt google. Good luck.

---

