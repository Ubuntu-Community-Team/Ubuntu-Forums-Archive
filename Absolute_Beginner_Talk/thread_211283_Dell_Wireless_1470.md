---
title: "Dell Wireless 1470"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by GStubbs43 on 2006-07-08
Hi everyone, I am pretty new to linux and I have searched and read many posts and websites and I can not figure out how to get my wireless internet working!:( 

This is what iwconfig shows:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Stubbs Wireless"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

I have the windows drivers from Dell, and I have put a Broadcom 4318 driver on my desktop.

I am currently online using an ethernet cable. I really need help. Do I need Wine or ndiswrapper? How do I install those? Thanks! :-k

---

### Post by GStubbs43 on 2006-07-08
I did ifconfig and got this:

```
eth0      Link encap:Ethernet  HWaddr 00:14:22:AC:CD:F6
          inet addr:192.168.1.40  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:feac:cdf6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71623 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:100199870 (95.5 MiB)  TX bytes:4780158 (4.5 MiB)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:207 errors:0 dropped:0 overruns:0 frame:0
          TX packets:207 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:15332 (14.9 KiB)  TX bytes:15332 (14.9 KiB)

```

P.S. My network name is Stubbs Wireless if that helps.

---

### Post by mourad on 2006-07-08
> **GStubbs43 said:**
> I did ifconfig and got this:

```
eth0      Link encap:Ethernet  HWaddr 00:14:22:AC:CD:F6
          inet addr:192.168.1.40  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:feac:cdf6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71623 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:100199870 (95.5 MiB)  TX bytes:4780158 (4.5 MiB)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:207 errors:0 dropped:0 overruns:0 frame:0
          TX packets:207 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:15332 (14.9 KiB)  TX bytes:15332 (14.9 KiB)

```

P.S. My network name is Stubbs Wireless if that helps.

Well, as far as I know, if clicked on the network monitor icon (you know the 2 small computers icons) ,
 and then click on the configration tab on the bottom, then enter your system password as you will be asked for it, 
then choose wireless connection and click properties on the right side, 

then enter your network name (ESSID) and if you are behind a wep encrytion enter it as well, 
in the connection setting just below, choose DHCP if you don't have a static IP, and leave the rest for the system it will configure it automatically, 

however if you have a static Ip you should enter everything manually, the IP, the submask, the gateway, and the DNS ...
and voila ... I Hope it works for you ...

---

### Post by GStubbs43 on 2006-07-08
I have tried that (actually it was the first thing I tried when I installed Ubuntu) and it just doesn't connect...

[IMG]http://img89.imageshack.us/img89/6409/screenshot6to.png[/IMG]

---

### Post by GStubbs43 on 2006-07-08
Okay, I found this website: [http://www.allthingsalceste.com/useful-ubuntu-breezy-on-a-dell-b130/](http://www.allthingsalceste.com/useful-ubuntu-breezy-on-a-dell-b130/)
The b130 is the laptop I have...

it says this:
> Wireless

   1. In synaptic, download the ndis user tools. This allows you to use a windows driver for a wireless card.
   2. Download the driver for the Dell 1470 wireless adapter from here.
   3. Unzip the file to its own directory (yes you can unzip this execultable).
   4. In a terminal, navigate to said directory and type these commands:
          * sudo ndiswrapper -i bcmwl5.inf
          * sudo ndiswrapper -l
          * sudo ndiswrapper -m
          * sudo depmod -a
          * sudo modprobe ndiswrapper
   5. Now, navigate to System>Administration>Networking. The card should be there. Activate and configure per usual.



How do I extract the .exe? I might have to go back to Windows if I can't get this! :-k

---

### Post by GStubbs43 on 2006-07-08
I opened a terminal ad typed ```
unzip (file location)
```

This is the complete terminal screen:
```

gino@gino-laptop:~$ unzip /home/gino/Desktop/R102320.EXE
Archive:  /home/gino/Desktop/R102320.EXE
  inflating: AegisE2.dll
  inflating: AegisE5.dll
  inflating: AegisI2.exe
  inflating: AegisI5.exe
  inflating: BCMLogon.dll
  inflating: bcmwl5.inf
  inflating: bcmwl5.sys
  inflating: bcmwl5a.ini
  inflating: bcmwlcpl.cpl
  inflating: bcmwld2k.exe
  inflating: bcmwlhlp.chm
  inflating: bcmwlhoa.ini
  inflating: bcmwlhom.exe
  inflating: bcmwlhom.ini
  inflating: bcmwlntp.sys
  inflating: bcmwltry.exe
  inflating: bcmwlu00.exe
  inflating: data1.cab
  inflating: data1.hdr
  inflating: data2.cab
  inflating: DellInfo.exe
  inflating: dellinst.exe
  inflating: ikernel.ex_
  inflating: is.exe
 extracting: launcher.ini
  inflating: layout.bin
  inflating: MFC42.DLL
  inflating: MFC42U.DLL
  inflating: MSVCP60.DLL
  inflating: MSVCRT.DLL
  inflating: README.txt
  inflating: setup.exe
  inflating: Setup.ini
  inflating: setup.inx
  inflating: setup.iss
  inflating: wltray.exe
  inflating: wltrynt.dll
  inflating: wltrysvc.exe
  inflating: bcm43xx.cat
  inflating: Version.txt
gino@gino-laptop:~$

```

Now, where did it get extracted to?

---

### Post by GStubbs43 on 2006-07-08
I found launcher.ini in home/gino/ but how do I navigate to said directory in a terminal?

Terminal:
```
gino@gino-laptop:~$ /home/gino/launcher.ini
bash: /home/gino/launcher.ini: Permission denied

```

---

### Post by GStubbs43 on 2006-07-08
Okay, I have now tried to access the internet (wirelessly) on Ubuntu, Kubuntu, and Nubuntu. I'm getting frustrated...:mad:  hehe. 
Is there another Linux Distro that has better wireless capibilities? I tried DamnSmallLinux (DSL) before and it connected right to the internet without setting anything up. But I hated the setup and there were no colors so it looked horible! :rolleyes:  What do you guys think? Right now I only have one partition (with XP) and a Ubuntu LiveCD, Kubuntu LiveCD, and Nubuntu LiveCD (Which I don't like very much), sorry about sounding mean and very mad. I just want to be able to run Linux and use the internet wirelessly

---

### Post by GStubbs43 on 2006-07-08
I'm downloading the**Debian**and **Symphony OS** iso's and will try those out. Has anyone used these before? Debian will be done in about 20 minutes and Symphony OS about 2 or so hours.

---

### Post by DarkOx on 2006-07-08
From what I can see, your wireless card is working. If you try typing "iwlist scan" and something like 

Cell 02 - Address: 00:07:7B:G9:CF:T8
          ESSID:"Your Network Name"
          Protocol:IEEE 802.11b
          Mode:Managed
          Frequency:2.437 GHz (Channel 6)
          Quality:0/100  Signal level:-78 dBm  Noise level:-256 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s

shows up, then your card is scanning correctly, and it is only a matter of connecting to your network. I suspect this is your problem. What encryption are you using on your network? If you are using no encryption, or WEP encryption, you should be able to connect to it straight out of the box. If you are using WPA encryption (which is the stronger type of encryption) you should download a program through synaptic called Network Manager, which should allow you to get connected.

Other things that could be causing your problems:
1) Have you ndiswrapped a driver to get the results of iwconfig? If you haven't, you may be using the default bcm43xx driver, which doesn't work out of the box.
2) If you did use ndiswrapper to wrap the drivers, did you add "blacklist bcm43xx" to the file /etc/modprobe.d/blacklist? Otherwise the drivers will conflict and ndiswrapper won't work.

Your wireless situation sounds similar to mine, so if you post back with what style of encryption your using, and whether or not you've been using ndiswrapper I (hopefully) will be able to help you get online.

P.S. - I've found that the SUSE 10.1 distro has marginally better wireless support than Ubuntu, if only because of the YaST setup tool and network manager installed by default. However, I experienced problems  installing software and using the hibernate feature in SUSE 10.1 so I can't fully recommend it.

---

### Post by GStubbs43 on 2006-07-08
I have decided to reinstall Ubuntu on my hard drive! I am going to try it one more time and hope that it works!!! I tried to install ndiswrapper but I got confused on installing and using it.These are the instructions I have:
   1. In synaptic, download the ndis user tools. This allows you to use a windows driver for a wireless card.
   2. Download the driver for the Dell 1470 wireless adapter from here.
   3. Unzip the file to its own directory (yes you can unzip this execultable).
   4. In a terminal, navigate to said directory and type these commands:
          * sudo ndiswrapper -i bcmwl5.inf
          * sudo ndiswrapper -l
          * sudo ndiswrapper -m
          * sudo depmod -a
          * sudo modprobe ndiswrapper
   5. Now, navigate to System>Administration>Networking. The card should be there. Activate and configure per usual.


But I don't get it... I have the driver [[http://ftp.us.dell.com/network/R102320.EXE](http://ftp.us.dell.com/network/R102320.EXE)]
But that's all. Ubuntu will be on my computer again in about 7 minutes... can someone explain how to install the driver? Thanks!

---

### Post by GStubbs43 on 2006-07-08
> **GStubbs43 said:**
> I have decided to reinstall Ubuntu on my hard drive! I am going to try it one more time and hope that it works!!! I tried to install ndiswrapper but I got confused on installing and using it.These are the instructions I have:
   1. In synaptic, download the ndis user tools. This allows you to use a windows driver for a wireless card.
   2. Download the driver for the Dell 1470 wireless adapter from here.
   3. Unzip the file to its own directory (yes you can unzip this execultable).
   4. In a terminal, navigate to said directory and type these commands:
          * sudo ndiswrapper -i bcmwl5.inf
          * sudo ndiswrapper -l
          * sudo ndiswrapper -m
          * sudo depmod -a
          * sudo modprobe ndiswrapper
   5. Now, navigate to System>Administration>Networking. The card should be there. Activate and configure per usual.


But I don't get it... I have the driver [[http://ftp.us.dell.com/network/R102320.EXE](http://ftp.us.dell.com/network/R102320.EXE)]
But that's all. Ubuntu will be on my computer again in about 7 minutes... can someone explain how to install the driver? Thanks!

I installed ndiswrapper, un-ziped the exe, and then I type cd [location of ini]

and this is what shows:

```
gino@gino-laptop:~$ unzip /home/gino/Desktop/R102320.EXE
Archive:  /home/gino/Desktop/R102320.EXE
  inflating: AegisE2.dll
  inflating: AegisE5.dll
  inflating: AegisI2.exe
  inflating: AegisI5.exe
  inflating: BCMLogon.dll
  inflating: bcmwl5.inf
  inflating: bcmwl5.sys
  inflating: bcmwl5a.ini
  inflating: bcmwlcpl.cpl
  inflating: bcmwld2k.exe
  inflating: bcmwlhlp.chm
  inflating: bcmwlhoa.ini
  inflating: bcmwlhom.exe
  inflating: bcmwlhom.ini
  inflating: bcmwlntp.sys
  inflating: bcmwltry.exe
  inflating: bcmwlu00.exe
  inflating: data1.cab
  inflating: data1.hdr
  inflating: data2.cab
  inflating: DellInfo.exe
  inflating: dellinst.exe
  inflating: ikernel.ex_
  inflating: is.exe
 extracting: launcher.ini
  inflating: layout.bin
  inflating: MFC42.DLL
  inflating: MFC42U.DLL
  inflating: MSVCP60.DLL
  inflating: MSVCRT.DLL
  inflating: README.txt
  inflating: setup.exe
  inflating: Setup.ini
  inflating: setup.inx
  inflating: setup.iss
  inflating: wltray.exe
  inflating: wltrynt.dll
  inflating: wltrysvc.exe
  inflating: bcm43xx.cat
  inflating: Version.txt
gino@gino-laptop:~$ cd /home/gino/launcher.ini
bash: cd: /home/gino/launcher.ini: Not a directory
gino@gino-laptop:~$

```

I still need help please!

---

### Post by DarkOx on 2006-07-08
Anything that I've put in quotes should be typed into a terminal. First change directory to where the files are:

> cd /home/gino/Desktop

type  

> sudo ndiswrapper -i bcmwl5.inf

> ndiswrapper -l

> sudo ndiswrapper -m

> sudo depmod -a

> sudo modprobe ndiswrapper

Then, type

> sudo gedit /etc/modules

add "ndiswrapper" to the end of the list in that file, save and exit. Finally, type 

> sudo gedit /etc/modprobe.d/blacklist

add "blacklist bcm43xx" to that file, save and exit. Now restart your computer. You should be able to configure your wireless normally UNLESS you are using WPA encryption, in which case you must install and use the Network Manager program. 

Hope that helps.

---

### Post by GStubbs43 on 2006-07-08
```
gino@gino-laptop:~$ cd /home/gino/Desktop
gino@gino-laptop:~/Desktop$ sudo ndiswrapper -i bcmwl5.inf
Password:
Installing bcmwl5
couldn't copy bcmwl5.inf at /usr/sbin/ndiswrapper line 135.
gino@gino-laptop:~/Desktop$

```

and the ini file got saved in /home/gino not /home/gino/desktop

---

### Post by GStubbs43 on 2006-07-08
I went through it all anyway (with a lot of error messages + I couldn't save the last blacklist part) and nothing happened... this is the network screen:
[img]http://img288.imageshack.us/img288/9817/screenshot0cf.png[/img]

The top one doesn't work and there is no Dell Card listed. 
I REALLY NEED HELP! :mad: :mad: :mad: :mad: :mad:

UPDATE: I looked in Device Manager & It is listed as unknown. :(

[IMG]http://img276.imageshack.us/img276/766/screenshot16mp.png[/IMG]

---

### Post by GStubbs43 on 2006-07-08
Is it possible to install the .exe driver using Wine? I have it on Ubuntu, but I don't know if it will work on drivers. :confused:

---

### Post by DSn0wMan on 2006-07-08
I am not convinced that it's driver problem.

It appears from your screenshot that eth1 is not active. You can select eht1 and click activate, or go to the commandline and type ```
 ifconfig eth1 up 
```

Also for troubleshooting it may be helpfull to turn encryption off on your router.

---

### Post by GStubbs43 on 2006-07-08
When I select activate, it says activating for about 1.5 minutes and then after I press ok, it automatically deactivates and doesn't work.

---

### Post by DSn0wMan on 2006-07-08
It seems like in post #5 you had it active. What has changed?

Also, to be honest with you I really dont trust that gui network manager thing. try bringing it up from the command line. You probably need to use sudo.

---

### Post by GStubbs43 on 2006-07-08
Well, it wasn't *really* active, that was just between the time I selected Acitvate and OK.

> Also, to be honest with you I really dont trust that gui network manager thing. try bringing it up from the command line. You probably need to use sudo.

Can you explain that more? Sorry.:rolleyes:

---

### Post by DSn0wMan on 2006-07-08
I have just found that the ifconfig and iwconfig commands are more reliable. The GUI is just a way of executing those commands without learning all the switches etc. At times using the GUI has created unexpected results. So i just use the ifconfig, and iwconfig from the command line.

It's been working without a hitch for about 3 months now, so I forget some of the commands.

The one thing that helped me get it working was turning off encryption. Then adding it later when everything else checked out.

I also had long delays with clicking the "activate" button, and my drivers where working fine. I'll try to find a wiki on the ifconfig and iwconfig for you.

---

### Post by DSn0wMan on 2006-07-08
Here is a good trouble shooting guide. [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

I hope it helps.

---

### Post by GStubbs43 on 2006-07-08
Sadly, something (bad) happened to my computer and it is reformatting my whole hard drive... I need to reinstall Windows... Then reinstall Linux/Ubuntu and I'll try it again. :-? 

:(

---

### Post by GStubbs43 on 2006-07-08
Off Topic but while I am partitioning my hard drive... it is 40gb.. . Should I make two partitions now, or wait until I install Ubuntu? I can format one with NTFS (for Windows) And leave one un-formatted. Should I just use the whole hard drive for XP right now and let Ubuntu do the rest later?

---

### Post by DSn0wMan on 2006-07-08
It's better to make 2 partitions now. Widows dosn't like giving up space once it has it. Just make 1 NTFS for windows, and leave some unformated space for Ubuntu.

---

### Post by GStubbs43 on 2006-07-08
Okay, I did about 50/50 I think the Extra partition has a bit more space. ;)

> **DSn0wMan said:**
> It's better to make 2 partitions now. Widows dosn't like giving up space once it has it. Just make 1 NTFS for windows, and leave some unformated space for Ubuntu.

---

### Post by GStubbs43 on 2006-07-08
All right... I have a completley new Ubuntu OS with about 17gb. I haven't plugged in the ethernet cord yet either... What should I do first in order to get my dang internet working? :D Thanks!

P.S. <<OFF TOPIC>> What is the easiest way to get my resolution to 1280x800? My laptop didn't come with a manual but it is online... It is a Dell Inspiron 1300/B130
[http://tinyurl.com/9tvmz](http://tinyurl.com/9tvmz) <pdf and html manuals

I couldn't find anything about the dpi or resolution (which is 1280x800) or anything else I will probably need. Thanks again!

---

### Post by GStubbs43 on 2006-07-08
By the way... I have Verizon Wireless DSL with a Westell Versalink 327W Modem/Router if that helps.

---

### Post by DSn0wMan on 2006-07-08
You where not online during the install?

---

### Post by GStubbs43 on 2006-07-08
No... Should I have been?

??

---

### Post by DSn0wMan on 2006-07-08
It definately helps.

1st Get a connection with your ethernet cable.

Then update your packages ```
sudo apt-get update
sudo apt-get upgrade
```

or use System -> Administration -> Synaptic to update

Then go about configuring your wireless without encryption,and finally add the encryption.

Please refer to this trouble shooting guide should your wireless connection not work right away.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

It has a sensible way of determining what might be worng, so you don't do a bunch of un-needed driver install stuff.

If you have the time I would strongly recomment installing Ubuntu whle connected to the internet.

It may solve your wireless problems, or atleast get a wired connection set up for you.

---

### Post by GStubbs43 on 2006-07-08
I'll try that... hold on.

---

### Post by GStubbs43 on 2006-07-08
Okay, the updates are done, but I still need to be connected via ethernet cable. I *am* new at Linux but I do think it is a driver problem since it is listed as unknown in device manager. Also, do you know what the easiest way to change my resolution is (see a few posts above)? Thanks.[-o<

---

### Post by DSn0wMan on 2006-07-08
Change Resolution:

System -> Preferences -> Screen Resolution

For your connection go through the troubleshooting steps listed in the link I posted above. If you get stuck let me know where you are having trouble.

---

### Post by GStubbs43 on 2006-07-08
I fixed it! And guess what?.....

...
...
....
.....
....
...
...
It was the drivers!
I had misread the instructions for ndis!
Yay!

But for the resolution, that only shows 1024x768 and I want to get 1280x800.
How can I do that? Thanks!

---

### Post by DSn0wMan on 2006-07-08
Cool! Good news.

Now for the resolution you will want to get out your manual, or some documentation about your monitor and graphics card. 

Make a backup of /etc/X11/xorg.conf 
```

cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```

press CTRL+ALT+F1 (this will exit xwindows) and prompt you for a login

Once you are logged in.
```
sudo dpkg-reconfigure xserver-xorg 
```

This will launch the configuration for your xserver (controlls the desktop environment).

Just follow the directions carefully and chose the settings that work for you (this is where the manuals come in handy). If everything is good xserver will restart, and you hit "CTRL+ALT+F7" to get back to your desktop. If that doesn't work type starx at the prompt.

---

### Post by GStubbs43 on 2006-07-08
```
gino@gino-laptop:~$ cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
cp: cannot create regular file `/etc/X11/xorg.conf.bak': Permission denied
gino@gino-laptop:~$

```

---

### Post by GStubbs43 on 2006-07-08
Oh... and I don't have the settings for my computer... all I know is I want 1280x800 resolution which is the default in Windows

---

### Post by DSn0wMan on 2006-07-08
Sorry you will need to sudo cp to make the backup.

The documentation is just helpfull, not required. Just read the instructions carefully while going through the menus. There is a part in there to change the resolution, but it asks you alot of other questions too.

---

### Post by GStubbs43 on 2006-07-08
I fixed that by myself as well! hehe! I edited a config file and restarted the computer and it looks so much better! Thanks for all your help!

---

### Post by bob67 on 2006-07-08
Hey I have the same laptop and wireless card as you so I thought I would chime in a help you out a little bit.

You won't be able to get the 1280x800 resolution by default there is something wrong with the way the VBIOS reports its resolutions.

Thankfully, there have been individuals who have made hacks to get 1280X800 resolution. The package is called 915resolution. Read more about the package here: [http://www.geocities.com/stomljen/]("http://www.geocities.com/stomljen/")

To get 1280X800 resolution you need to do the following:

1.) Make sure you have extra repositories added to your sources.list file. If not, follow this simple guide here: [http://ubuntuguide.org/wiki/Dapper#Repositories]("http://ubuntuguide.org/wiki/Dapper#Repositories")

2.) Open a terminal (Applications>Accessories>Terminal). Type: sudo apt-get install 915resolution. Enter your password. It might then ask you a yes or no question if you want to install the package. Type 'y' for yes.

3.) It will then install the 915resolution package and set it up for you. Next you will need to restart the graphical display called the X-Server. Restart the X Server by pressing CTRL+ALT+BACKSPACE

4.) Your screen will flash black and might show your username login text on a black screen, don't type anything, just wait and it will flash back again to your normal ubuntu or kubuntu login.

5.) Log in to your desktop and at this point you should be enjoying your 1280X800 resolution. If not, you might want to try going to System>Preferences>Screen Resolution and see if there is now an option for '1280X800'. If there is, choose that and apply settings.

From here on out, your computer should start will 1280x800 resolution unless you change it otherwise.
Any questions, reply back and I'll try to answer them the best I can.

---

### Post by GStubbs43 on 2006-07-09
Just to letchya know... I got it working without having to install anything! yay! Thanks for yoour help anyway. I just had to edit a config file and restart.

---

### Post by bob67 on 2006-07-10
Cool beans man. Good luck and enjoy.

---

