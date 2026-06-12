---
title: "connecting to internet"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by stanleyhugh on 2007-06-22
I am completely new to Ubuntu, which I have now installed,on an old machine, but cannot connect to the internet.  On the same machine, using IE or Firefox I can.

The old machione I am using is made up of a revitilised Windows 98  10.2 GB drive upgraded to XPSP2, being used as the master, connected internally to a 40GB slave and externally to a Maxtor II 300GB. The machine is wireless connected to others within the home via the one that is connected by cable to the internet, and all work well,  as does this machine using IE or Firefox.

What should  I do to connect this old hotchpot of a machine to the internet using Ubuntu?

---

### Post by lixy on 2007-06-22
> **stanleyhugh said:**
> I am completely new to Ubuntu, which I have now installed,on an old machine, but cannot connect to the internet.  On the same machine, using IE or Firefox I can.

The old machione I am using is made up of a revitilised Windows 98  10.2 GB drive upgraded to XPSP2, being used as the master, connected internally to a 40GB slave and externally to a Maxtor II 300GB. The machine is wireless connected to others within the home via the one that is connected by cable to the internet, and all work well,  as does this machine using IE or Firefox.

What should  I do to connect this old hotchpot of a machine to the internet using Ubuntu?

To make sure we're on the same page, you're trying to hook up a machine to the net wirelessly. Am I right.

To be able to help you we're gonna need a few more details. What's your hotspot using? WEP? WPA? What's your wireless card/chipset model? Also, are you able to ping your router?

From the main menu try  System  -> Administration -> Networking. Select "Wireless connection"  then click on properties. Are you able to see your access point in the drop down list?

---

### Post by wormser on 2007-06-22
To get the details of your wireless card:  Applications> Accessories> Terminal

```
lspci
```

Post the results.

---

### Post by stanleyhugh on 2007-06-22
Hi Lixy!

"To be able to help you we're gonna need a few more details. What's your hotspot using? WEP? WPA? What's your wireless card/chipset model? Also, are you able to ping your router?

From the main menu try System -> Administration -> Networking. Select "Wireless connection" then click on properties. Are you able to see your access point in the drop down list?"
__________________

WEP, D-Link AirPlus G Adapter.

System> Administration> Network>. Select  'Wireless connection' click properties.

Menu reads Network name (correct) Password type (WEP Key [ascii] Netword password, connection settings, Confguration (Automatic configuration (DHCP) IP address (correct) Subnet mark (255.0.0.0)
Gateway address (blank)

Went to Firefox browser - How to participate.

_Message_ Firefox can't find the server at www,ubuntu.com.

Same answer when using the google box.

[As previously stated, there is not trouble accessing the net when using Windows on the same computer.]

---

### Post by stanleyhugh on 2007-06-23
[QUOTE=wormser;2891464]To get the details of your wireless card:  Applications> Accessories> Terminal

```
lspci
```

Thanks.

I tried that, and it came up with

(username)@(username):~ $

to which I added 1spci then, making sure I was not doing it incorrectly, Ispci

with the result

bash: 1 (or) I spci: command not found.

---

### Post by BobCFC on 2007-06-23
it's definately a lowercase l for lemmming that you want.  Try copy and paste. 

```
lspci
```



TIP: you can click middle mouse-button to paste in terminal or right-click and use menu if you prefer.

---

### Post by stanleyhugh on 2007-06-23
> **BobCFC said:**
> it's definately a lowercase l for lemmming that you want.  Try copy and paste. 

```
lspci
```



TIP: you can click middle mouse-button to paste in terminal or right-click and use menu if you prefer.

Thanks.  The lower case l for lemming gave me the clue.

Information found:

00.00.0 Host bridge: VIA Technologies,Inc. P4M266 Host Bridgfe
00.01.0 PCI bridge: VIA Technologies,Inc. VT8633 [Appollo Pro 266 AGP]
00.09.0 Network controller: RaLink RT2561 rev B 802.11g
00.0a.0 Modem: Smart Link Ltd. Unknown device 2800 (rev 02)
00.0b.0 Communication conmtroller: Agere Systems LT WinModem (rev 02)
00.10.0 USB Controller: VIA Technologies,Inc VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00.10.2 USB Controller: VIA Technologies,Inc VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00.10.3 USB Controller: VIA Techologies,INC USB 2.0 (rev 82)
00.11.o ISA bridge: VIA Techologies,Inc VT8235 ISA Btridge
00.11.1 IDE interface: VIA Technologies,Inc VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00.11.5 Multimedia audio controller: VIA Technologies,Inc VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00.12.0 Ethernet controller: VIA Technologies,Inc VT6102 [Rhine -  II   ] (rev 74)
01.00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM 266/KL266]

---

### Post by hasala on 2008-02-06
(if you use this method you can forget about the rpms no rpm will be needed to be installed for you to get the modem running.)
RATHER THAN EXTERNAL MODEMS internal modems offloads a lot of funtionality to the software driver.it has always been a big problem to configure those internal modems or(WINMODEMS/LINMODEMS) to work with linux because of manufacturers not supporting linux (and also the driver being pretty much more complex than ) But due to a great person Linux maintainer Sasha Khapyorsky writing the neccassary drivers needed to work the winmodem , now using a internal modem in linux has become as easy as ABC.


Linux maintainer: Sasha Khapyorsky. Get his updated software from:
[http://linmodems.technion.il/packages/smartlink/](http://linmodems.technion.il/packages/smartlink/)


what to do.

1. download a software called scanmodem from the foresaid site.

2. Browse [http://linmodems.technion.ac.il](http://linmodems.technion.ac.il) and  download scanModem.gz .
 Within a Linux partition open up a console and type in the following commands
    gunzip scanModem.gz
 To make it executable:
    chmod +x scanModem
 Run diagnositics with:
    ./scanModem 
3.scanmodem will check your hardware and software and then write its diagnostics to a subdir called modem.

4.open the ModemData.txt file.and go to   -----------end Softmodem section----------- part .

5.it will give the softwares you need to download and install.

6.if u have not installed the source at the installation of the distro. please install it.(source of the kernel) from the installation cd/dvd.

7.then install the downloaded software.

8.go to scanmodem/modem and open the diagnostic file chipsetname.txt eg:Smartlink.txt/conexant.txt .

9.In the start of the doc it gives the commands you have to run at the console to load the drivers that u downloaded and installed.

10.make sure that the smpppd, pppd services are installed and running.else install both and remember to enable them.

11.dial up using kinternet(i prefer it) or kppp. put to stupid mode option..now configure kinternet and the modem properly.to do that 
 goto yast->network devices ->modem.
           1.choose your modem device and press edit.
              enter modem device as /dev/ttySL0 and enter the details of the isp. if you are not sure call customer support for internet of your isp (internet provider) and get the required details such as number to dial and prefix.username
and password.

           2.remember to definitely check the box for stupid mode.

now every thing is set up

enjoy the internet with a great browser like firefox/opera.!!!!!!!
(with this you do not need any rpm for you to download,what you compile is enough)
if u have any comments or questions please mail to:dharmawardena_06@elect.mrt.ac.lk

						or [email]hasaladharmawardena@yahoo.com[/email]
or //(hasalaid@gmail.com).

hasala dharmawardena
faculty of engineering
department of electrical engineering([www.elect.mrt.ac.lk](www.elect.mrt.ac.lk))
University Of Moratuwa
SRILANKA

regards from srilanka , hasala.         ([www.hasala.bravehost.com](www.hasala.bravehost.com))

---

