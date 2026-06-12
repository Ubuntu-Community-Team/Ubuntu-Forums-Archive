---
title: "how to connect from my modem"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by faraz_k86 on 2007-11-30
ok now that i installed ubuntu on my laptop, its modem appears to be supported by ubuntu,

now i dont know how to connect to my ISP???


in windows i just enter the username, password and phone number and press connect and tthats it.


but that is not the case n ubuntu??  how do i connect via modem??

---

### Post by faraz_k86 on 2007-11-30
ok i would like to add that i read the help file and it tells me to add the DNS servers of my ISP,


I dont know the dns of my isp??

this was handled automatically by windows??

---

### Post by phidia on 2007-11-30
you need to install gnome-ppp. look for it by opening synaptic (the package manager)
and searching for gnome-ppp. I believe it's on the install cd but not installed by default anymore. There are not as many dial up users as there once were. 

I hope you're correct about your internal modem being supported-lot's of winmodems can be make to work but they're not plug & play. If you need additional help list your modem specs and/or go to [www.linmodems.org](www.linmodems.org).

To set up dial up you need to run pppconfig from a terminal. There are several ways to find your dns address but may the easiest is to look in your windows control panel files. I haven't used windows for a while now so I'm not sure exactly where it's stored.

---

### Post by Irihapeti on 2007-11-30
Are you using dialup? If so, then the Network Manager application doesn't work for many people.

You can use pppconfig to set up your connection details. To do this, type "sudo pppconfig" in a terminal (without the quotes). Once you are set up, you can type "pon provider" to log on, and "poff" to disconnect.

You may want to download Gnome-PPP to have a GUI way of connecting to the Internet.
It's in the repositories.

If you are on broadband, sorry I can't help. Maybe someone else can.

Phidia: beat me to it!

---

### Post by faraz_k86 on 2007-11-30
thx guys, so i need gnome ppp to connect.

do i still need my dns number for that?

---

### Post by Irihapeti on 2007-11-30
> **faraz_k86 said:**
> thx guys, so i need gnome ppp to connect.

do i still need my dns number for that?

Click on "automatic DNS" in the "networking" tab when you set it up. That should take care of it for you.

Oh, and there's another trick to Gnome-PPP which can drive you slightly nuts if you don't know about it. If you find that you get disconnected immediately after logging on, click on "Ignore terminal strings(stupid mode)" in the "options" tab.

---

### Post by faraz_k86 on 2007-12-04
ok so i looked in my ubuntu 7.10 and there is no such option in the synaptics network manager for gnome ppp.

there is a wvdial though, and it is installed, but bi cant find it on the system.

can anyone plz tell me how to connect to my isp, which requires only my username and password and the phone number of the isp.??

---

### Post by faraz_k86 on 2007-12-04
ok again i did some searching and found that wvdial is my answer.

so i entered in the terminal: wvdial conf

which wrote a file to /etc/wvdial.conf

i edited the file there and i am attaching that file here.

now again in the terminal when i type wvdial i get the following lines, which at the end says no dial tone, while the line is connected properly.

plz help.

> root@faraz-laptop:~# wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT#13177777
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT#13177777
WvDial Modem<*1>: NO DIALTONE
WvDial<Err>: No dial tone.
WvDial<*1>: Disconnecting at Tue Dec  4 10:22:53 2007



---

### Post by Irihapeti on 2007-12-04
Gnome PPP is in the Gutsy repository, according to packages.ubuntu.com You need to have the universe repository enabled.

I think you can edit some of the settings in wvdial.conf by hand, using gedit or nano, even though it says not to! (Someone else please correct me if I'm wrong.)

Here is my own wvdial.conf, with personal bits removed, of course:

```
[Dialer Defaults]
Modem = /dev/ttySHSF0
ISDN = off
Modem Type = Analog Modem
Baud = 460800
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = 
Init4 = 
Init5 = 
Init6 = 
Init7 = 
Init8 = 
Init9 = 
Phone = xxxxxxxxxx
Phone1 = 
Phone2 = 
Phone3 = 
Phone4 = 
Dial Prefix = 
Dial Attempts = 1
Dial Command = ATM0L0DT
Ask Password = off
Password = xxxxx
Username = xxxxx
Auto Reconnect = off
Abort on Busy = off
Carrier Check = on
Check Def Route = off
Abort on No Dialtone = on
Stupid Mode = on
Idle Seconds = 0
Auto DNS = on
;Minimize = on
;Dock = on
;Do NOT edit this file by hand!
```

You could try changing some of the settings and see if it helps.

Personally, I have found pppconfig easier to set up. There is futher info at [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

Irihapeti

---

### Post by faraz_k86 on 2007-12-05
thx for the reply Irihapeti.

so to install gnome ppp i need the universal repository enabled.

k so how do i do that.?

---

### Post by Irihapeti on 2007-12-05
> **faraz_k86 said:**
> thx for the reply Irihapeti.

so to install gnome ppp i need the universal repository enabled.

k so how do i do that.?

System -> Admin -> Synaptic package manager
Choose "repositories" in the Settings menu and check the "community-maintained open-source software (universe)" box in the Ubuntu software tab. You'll need to click on the reload button for the new programs to show up in your list.

---

### Post by faraz_k86 on 2007-12-09
ok so i did the repositories thing and even then the gnome-ppp did not show up...


so i just downloaded it from packages.ubuntu.com


now the problem is the same that was with wvdial.


i get a no dialtone error, even in gnome-ppp, can anyone please help me with this.

why cant i connect to the internet even after my modem has been detected?????

---

### Post by faraz_k86 on 2007-12-09
no one????

---

### Post by Irihapeti on 2007-12-09
Try unchecking "abort connecting if no dial tone".

Also, try using pppconfig. I've found that for some reason, wvdial doesn't work properly on my PC unless I set up pppconfig first. I don't know why.

---

### Post by Bartender on 2007-12-10
faraz -
What makes you think your modem is supported?  Just because Ubuntu identifies it doesn't mean it'll work.
And if you're trying to set it up via Network Manager that's not gonna work either.

Take a read thru my dial-up [diary]("http://ubuntuforums.org/showthread.php?t=480717")

It's important to understand the problems with dial-up.  If you go into it expecting it to "just work" like  that other OS your frustration level is just going to increase.
Best to get the bad news all at once.  

*Some* people have succeeded in getting *some* winmodems to work.  My hat's off to them.

---

### Post by rockinlinux on 2007-12-10
this is what i think you should do, i have got many modems working in ubuntu.

go to [this site](www.linuxant.org) and follow the steps to figure out your modem chip set and get the correct driver.

then, i would not use gppp, in gusty it has a bug the wont ever let it close when your connected. It will just say "connecting" and look stupid being n the middle of the screen. Instead of GPPP use KPPP, its in the repos, just do:

```
sudo apt-get install kppp
```

And just like Bartener said, modems are not easy to get to work in linux, they are not really supported like windows. I use a dial up connection right now becasue im not living at home but to be totally honest with you dial up is almost a dead technology. 

A note about the linuxant drivers: The free driver is limited to 14kbs, this is very slow.....to get the full 56k it will cost you $20. if this is your main connection then it is worth the money. I also heard that dell has the drivers for free, but im not sure what modem they are for or what version of ubuntu they are for. 

good luck! :)

---

### Post by Bartender on 2007-12-10
Hi, rockin -
How's the OP going to get KPPP from the repositories without an internet connection?

faraz, if you have a thumb drive and access to broadband elsewhere, try downloading/burning a Kubuntu alt-install CD, then follow what I did on page 3 of my dial-up diary to get KPPP installed on your dial-up PC.  Worked for me.

However

KPPP is not going to solve your problems if you have a winmodem that's not set up correctly.  All KPPP can do for you is automate the dialing part.  If the pesky winmodem isn't configured (or can't be configured) to work in Linux a better dialer gets you nowhere.

---

### Post by rockinlinux on 2007-12-10
well i know its not going to solve his problems but its a better dialer for when he has his modem working. I was in the exact case....no connection and needed a dialer. I went to [http://packages.ubuntu.com](http://packages.ubuntu.com) and downloaded all the files for kppp (very frustrating)...maybe thats what.

the best bet is to download the program at linuxant that will tell you what chip you have. then go you [www.linmodems.org](www.linmodems.org) and get on the mailing list and they will walk you through it step by step. Getting a winmodem to work is not a easy or fast thing to do. it will take time and patience. 

bartender-
thanks for pointing out the no internet thing....i must have mised it :)

---

### Post by Irihapeti on 2007-12-10
There's a patched version of Gnome-PPP for Gutsy available at: [http://launchpadlibrarian.net/10692409/gnome-pppfixedforgutsy_0.3.24-1_i386.deb](http://launchpadlibrarian.net/10692409/gnome-pppfixedforgutsy_0.3.24-1_i386.deb)
that fixes the problem mentioned above.

---

### Post by rockinlinux on 2007-12-11
> **Irihapeti said:**
> There's a patched version of Gnome-PPP for Gutsy available at: [http://launchpadlibrarian.net/10692409/gnome-pppfixedforgutsy_0.3.24-1_i386.deb](http://launchpadlibrarian.net/10692409/gnome-pppfixedforgutsy_0.3.24-1_i386.deb)
that fixes the problem mentioned above.

wow....i did not know. I think ill still stay with kppp though...thanks for letting me know! :)

---

### Post by faraz_k86 on 2007-12-13
yes i agree that it sucks to configure dial up in ubuntu but it is the only option i have.


i did pppconfig and still i have no net and get the same no dial tone error.


WHAT NOW???



oh and during pppconfig when i asked it to autodetect my modem port it returned with no modems found that could be used with pppconfig, so i had to enter the port number manually.


whereas wvdial finds the port and detects the modem.


help

---

### Post by Bartender on 2007-12-13
faraz -
I'm thinking that either the modem is still not properly configured,
 
or

You don't have the right phone # plugged in.  The fact that it's getting to the point of dialing makes me think your modem might actually be working (I'm skeptical because most of them don't without jumping thru all sorts of hoops) but it's not dialing the right number.
Can you hear the modem speaker?  That's a good tool for diagnosis until you get it going.  There's a setting in the Linux dialers to turn the modem voulme up or down but I don't remember it right off the bat.

---

### Post by Irihapeti on 2007-12-13
Bartender:
I'd be inclined to agree that the OP's modem is working,or nearly working. I have a winmodem on my PC, and before I got the (Conexant) driver, Ubuntu thought that there was no modem installed at all.

Faraz:
pppconfig not detecting the modem automatically is quite usual - a bug, maybe. It happens to me all the time.

I'd like to be able to help more, but I think I've got to the limits of my knowledge.

---

### Post by rockinlinux on 2007-12-14
so did you install the linuxant driver? I think this is the only way you are going to be able to get this modem working. If you are going to use wvdial (or gppp) you will need to edit the wvdial.conf file. There you will put your username, password and phone number. When you install the linuxant driver your modem will be listed here: /dev/ttySHSF0 . you will also need to put that in whatever dialer you are using, (wvdial, GPPP, KPPP etc.). Right now Your modem might be working or might not be. The fact that your getting a dial tone eror is a good thing. *I think* it means that the computer found your modem, however just because it found your modem does not mean it will ever work without the linuxant driver :(  I understand that the dial up is your only choice, it was mine too and im sure with some patients and trail and error you will get it to work.

please tell me the following:

did you get the linuxant driver installed and if so correctly? please note that after the .deb installs you must go to a terminal and run:

```
sudo hsfconfig -license
```

here put FREE and it wil make your driver work.

after this edit the wvdial.conf file (if your using wvdial or GPPP)

try these things and come back and tell me what you figured out. Even after you have the river installed me may nee to change some permisions on some file before you can actually connect.

good luck.

---

### Post by Bartender on 2007-12-15
rockin -
Is it possible that the Dell modem drivers might work?  It's the right kind of modem, isn't it?

---

### Post by AnonCat on 2007-12-15
Sorry about the double post. I don't see an option for deleting my message.

---

### Post by AnonCat on 2007-12-15
I managed to get my smartlink winmodem working using the drivers at [http://linmodems.technion.ac.il](http://linmodems.technion.ac.il) 

Unfortunately, their precompiled driver for Gutsy at that site is missing some files and I had to compile those from other sources.  If you have a smartlink chipset I can help you get that modem working. I can't connect to their site right now, but they have a utility for detecting information about your modem.  If you paste the information in the modemdata.txt file here I should be able to help you further.

---

