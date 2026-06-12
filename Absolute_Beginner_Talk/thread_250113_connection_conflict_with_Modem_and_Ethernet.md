---
title: "connection conflict with Modem and Ethernet"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by tobmeister on 2006-09-03
I'm having a problem with my modem and ethernet connection.  After I boot up the sys. they both are active (Which is fine, I have a home network) the problem is, the modem will dial up but hangs after it connects and doesn't transfer any information.  If I deactivate the ehternet, the modem works just fine.  anyone have any suggestions as to what I can do to fix the problem


Thanks

Tobmeister

---

### Post by mssever on 2006-09-03
This is just a shot in the dark, but try this:
Go to System > Administration > Networking. Select your modem as the default gateway device. You might have to be connected to be able to make this selection.

---

### Post by xpod on 2006-09-03
AHHH...Someone else confused with it all.Thought it was just moi.
I just upgraded from 1meg to 4meg broadband.When i had the 1 meg it was an ethernet(i think) wire from settop box to pc but i used a little smc usb adapter as the ethernet port on pc did`nt work.

So now ive got a cable modem with both ethernet and usb ports in it but if i run my usual ethernet wire with little smc adapter it dont work that way now.Instead ive got to use the usb port on the modem to usb connector on the pc.

The mad thing is though if i look in my "network" it says im using eth1..
Indeed it is the same with firestarter....AND both the etho & eth1 are active but the third choice "modem" (ppp0) is not configured??????.
i thought i was now using a modem?????:-k :confused: 

Im just happy one way works and i clearly dont yet understand  all the
little differences but im trying(Quite new to pc`s not just ubu)

Obviously i would rather use the ethernet connection as apose to a usb one
but i cant even understand it let alone configure it.:-k 
I believe i need the driver for the actual card that sits in that slot in the pc.
Anyway i hope you get yours sussed out ok

---

### Post by mssever on 2006-09-03
You should only need a driver for your ethernet card if you have something exotic. My cable modem appears to my computer as an ethernet link. It's just plug and play. (Of course, I use a wireless router nowadays.)

---

### Post by nickpaton on 2006-09-03
@ Xpod: Please can you post the outputs of:

lspci

This lists every component detected by ubuntu on your PC.

Then:

ifconfig

This gives the output of each Ethernet port.

---

### Post by xpod on 2006-09-03
Nick to the rescue again.......:rolleyes: 

lspci
dad@dad-desktop:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:09.0 Modem: ALi Corporation SmartLink SmartPCI561 56K Modem
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
0000:00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
dad@dad-desktop:~$

And the otherdad@dad-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:20:ED:69:44:B4
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Base address:0x8f00

eth1      Link encap:Ethernet  HWaddr 00:02:8A:69:5D:61
          inet addr:82.24.21.141  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::202:8aff:fe69:5d61/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13413 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11310 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11540874 (11.0 MiB)  TX bytes:1456130 (1.3 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:508 (508.0 b)  TX bytes:508 (508.0 b)

dad@dad-desktop:~$



AHH NOW i see....................................YEAH RIGHT:confused: 
When i first got the internet on it i got left with some wires,a cd and a new broaband tv package that did`nt work.Turns out this was`nt my first"Plank" moment and they had in fact done things wrong with the box.

So i use the wires supplied quite happily for a week or two until i
 eventually realised there was a little ethernet(phone jack?)port in the back of the pc but it would only work if i used the little smc adapter in a usb port so im happy.......BUT,as i go along i begin to tipple that the
proper straight connection is the way to go but i had many other issues at that time:biggrin: SO worrying about proper types of connection were`nt on my "must learn" list

NOW though all this modem "without" modem connections AND ethernet "with" usb leads is just confusing me all the more.....(DONT say it...:-# lol)

Its no biggie but i would like to know whats going on in here(and the pc)

EDIT: my previous connection would work on all pc`s but this aint working on the kubunto for some reason

---

### Post by nickpaton on 2006-09-03
Graham - must stop meeting like this! LOL

As you can see you have a working Ethernet card:

> 0000:00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

I'm not 100% sure, but I reckon that Eth 0 is your LAN Ethernet connection, since there are no sent (tx) or received (rx) packages.

However Eth1 has a large number of tx'd and rx'd packages and therefore is probably your USB connection to your NTL router modem.

Right, disconnect your USB lead and adaptor etc, and connect in the LAN lead to the PC and the router.

Reboot the PC and router.

Go into System>Networking and set the default gateway as Eth0.

Ok that, and reboot the PC again.

What now happens?

If it does not work, please post your ifconfig again.

---

### Post by xpod on 2006-09-03
Right you...Not only are you too smart for your own good :mrgreen: but you`ve also made me all the MORE confused.....I thought this thing was a modem??

The straight lan,ethernet,wire what ever you bloody call it works on it`s own just fine me pal....It never did with windows but thats another forum eh.lol

Anyway SO could i use that wire from that port for this pc AND use the usb
wire from the usb port TO another pc........if its a router??i presumed THATS what i needed to wire the rest of them up to the net 

As i said the kubunto is here at the mo as i wanted to update it as well as reinstall it but it dont work with any of them ....i was in "network" and 
enabled eth0 it was but it aint playing......it works fine with the Ubunto live cd still so it must just be how it`s configured ...OR not...

I`ll suss THAT out as i think you done me enough for one day eh..:redface:

EDIT:firestarter shows the eth0 as detected but it wont start either:roll:

EDIT2:......OK OK yes it is ......now

---

### Post by nickpaton on 2006-09-03
WOT - me make you MORE confused - impossible LOL!

re using the two leads for two pc's at the same time, don't know - try it!

Do you know the make  model of that fancy noo piece of S**t (oops kit) NTL-Telewest gave you, and I'll look it up (just as a wee favour for ya!) - tomorrah.

Cheers M8

---

### Post by xpod on 2006-09-03
tobmeister...sorry your thread got hyjacked mate.
You just sounded as though you were having similar problems.......mind you,you`d need to be having SOME strange old problems to ever have the 
sort of probs i end up with:mrgreen: .

Nick:....i just stuck my ubunto live cd in just to check(MY workarounds are terrible eh)and it aint working on that at the same time and ive made sure internet connection sharing is on if that would have mattered(in the firewall) but it aint playing with more than one route.It dont even work now if i take the wire out THIS one but who cares...ZZZZZZZZzzzzzzz

Im going to bed as im supposed to be working in the morning....IF i remember the route to get there.......lol...cheers ...who needs classes eh=D> :p .

I`LL BE BACK!!!!

---

### Post by JR_Moneybags on 2007-09-06
I am having the same problems as the first poster.
Running 56k modem (H52PT-3020) on 64-bit Fiesty. Both the ethernet and the modem work fine - seperately. However if the ethernet cable is so much as plugged in the modem will dial and connect perfectly, however it will not send and receive data.

As far as I can tell I have set modem as default gateway to internet, I have checked the box that reads (Set MOdem as Default Route to INternet).

Any suggestions?
JR

---

### Post by mssever on 2007-09-11
> **JR_Moneybags said:**
> I am having the same problems as the first poster.
Running 56k modem (H52PT-3020) on 64-bit Fiesty. Both the ethernet and the modem work fine - seperately. However if the ethernet cable is so much as plugged in the modem will dial and connect perfectly, however it will not send and receive data.

As far as I can tell I have set modem as default gateway to internet, I have checked the box that reads (Set MOdem as Default Route to INternet).

Any suggestions?
JR

Given that this thread is more than a year old, you'd probably have better success if you started a new one.

---

