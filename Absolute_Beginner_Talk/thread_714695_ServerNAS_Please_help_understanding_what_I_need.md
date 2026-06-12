---
title: "Server/NAS Please help understanding what I need"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by wolfwatcher51 on 2008-03-04
Currently, I have 3 xp computers and a network printer on a router with usb drives on each computer. By sharing certain drives, they show up in my network places and we can read, write, etc back and forth. I use sync toy to back up important files from one computer to it's usb drive and a hdd on the other computer.

I have an old computer, PIII, 800mhz, 512mb ram, that I would like to put several drives in and use it for storage from both computers and backups from both computers. That way I can get rid of the usb drives and the need to backup from one xp computer to the other. It does not need to be accessed from outside our lan, but it does have to work like the shared drives we have setup now. In other words appear like a drive in my network places and not need user name and password to access it. I do not think you can schedule xp to do a backup to a drive needing user name and password, etc. There are just my wife and I so security, at least internally on our lan is not an issue.

I really would like to dump MS and go to linux, but proprietary software for our business only comes in MS flavor...rats! So, I am trying to convert where possible. I am thinking of putting Ubuntu on the old box and using Samba to do the sharing. Is this the way to go? I know I will have to give up a disk to ext3 for the ubuntu install, right? What about the other disk(s) that are shared? Can they be ntfs, or do they have to be ext3 and will I be able to share,read, and write to them from xp?

Given the specs on the old box, which flavor linux would you recommend? I tried using the 7.10 server edition, but I did not see how to use the command line while trying to follow a tutorial, the author assumed too much and I knew too little. I am leaning towards the GUI editions rather than the server ones because I think they would be better for me for now.

Or, should I go with something like freeNAS, or something like it and forget the server route? Any and all comments would be greatly appreciated. Thanks in advance, Chris.

---

### Post by hyper_ch on 2008-03-04
What do you want a gui for? I mean once you have setup the server to your liking you don't need the gui at all.... it will do the backups and it will be available for sharing its drives... no gui needed there...

---

### Post by igknighted on 2008-03-04
A GUI server doesn't gain you anything... there are no GUI configuration applications (for an xserver, at least).  The way you admin a server through a GUI is with a web-based control panel, like webmin, or application specific ones like PHPMyAdmin.

As for your particular project, I might suggest looking up SME Server.  It provides an incredibly simple and easy to setup file and directory server.

Oh, and don't worry about the file systems on the drives, that means nothing.  Samba is the program that will share the files to windows computers, and it would prefer them in ext3.

---

### Post by hyper_ch on 2008-03-04
[http://www.howtoforge.com/fileserver_with_sme_server7.1](http://www.howtoforge.com/fileserver_with_sme_server7.1)

---

### Post by msubzwari on 2008-03-04
SME server is not a bad idea but FreeNAS may be a better & purpose built option for your PIII 800Mhz System.

[http://www.howtoforge.com/network_attached_storage_with_freenas]("http://www.howtoforge.com/network_attached_storage_with_freenas")

Another review/howto:

[http://www.smallnetbuilder.com/content/view/30179/75/]("http://www.smallnetbuilder.com/content/view/30179/75/")

---

### Post by wolfwatcher51 on 2008-03-05
Thanks for all the feedback and the links. 

I looked at SMEserver andfreeNAS and they look interesting and possibly the solution to my needs.

Sorry for being so uninformed, at least in this arena, but they both look like you have to log into the "server" to access the files. I need the files to show up in network neighborhood like the shared drive we are currently using. I use synctoy to backup/sync a copy of very important work files from my wife's computer to a usb hdd attached to her box and to a hdd in my box.

I just built my first computer, to replace my first computer, the PIII 800Mhz machine. Now that it is available, I want to use it to hold hdds and do storage and backing up to files on it. I want to give it a fixed ip address, connect it to the linksys router and have it be available, like the lan printer, to the other computers. All three of the other computers run xp pro, so atleast the OSs are the same.

Then, when scheduled, the backup software can see the drive/file and sync to it without logins, passwords, etc. Can SMEserver do this, simply? Can freeNAS do this, simply? Thanks in advance, Chris.

---

### Post by igknighted on 2008-03-05
You should map the drive on any client PC.  Just make sure the the server is configured to share to the workgroup you are using (usually WORKGROUP unless you have configured it differently), then go to My Computer and select "map network drive" from one of the pull downs.  Select the drive letter you wish to use, then enter the share you want, in this format: \\servername\sharedfolder.  Make sure reconnect at login is enabled, then that folder will be mounted under the selected drive letter each time you log in.

---

### Post by wolfwatcher51 on 2008-03-05
OK, I decided to try SME Server.

I went through the tutorial and was looking pretty good right up to ip address for server and ip address for the gateway.

I have a hughes satellite modem, linksys router, then two xp computers and a network printer. The two xp boxes are set up to obtain ip and dns automatically. The linksys router is set up as a gateway with dhcp enabled. The hughes modem is setup with dhcp enabled also. The two xp boxes both work fine and no problem accessing the internet or reading/writing files between them.

I have tried numerous combinations of ip addresses and gateway addresses and it fails the internet connection every time. Should both the hughes modem and the linksys router both be set to dhcp enable?

From the ip address given to the two xp boxes, the linksys router is assigning them because they arre in the range shown in the linksys information. The linksys also shows that the gateway address is 192.168.0.1 which is the address of the hughes modem.

Linksys shows starting address of 192.168.1.20 thru 192.168.1.69. The gateway, hughes modem, has an address of 192.168.0.1. When entering values in SME, the third digits have to be the same, both 0 or both 1. I have tried several combos of both 0 or both 1 and always failed.

What to do, please? Thanks, Chris.

---

### Post by hyper_ch on 2008-03-05
enter for example 192.168.1.5 as IP for your server and 255.255.255.0 as local subnet and use 192.168.1.1 as gateway.

---

### Post by wolfwatcher51 on 2008-03-05
hyper_ch, 
Thanks for the reply, I tried it and it failed also.

I think the problem is with the linksys router and the hughes modem both doing dhcp. I cannot do anything about the hughes, but can make changes to the linksys.

I think that I need 192.168.1.x for the sme server and 192.168.0.1 for the gateway (hughes) modem.
A way to make that happen is to change the sub net mask from 255.255.255.0 to 255.255.0.0. What do you think?

Early in the sme router tutorial they mentioned that if you want it to be the gateway for your lan, your computer would need two nics. This is similar to my old setup when I had starband. Starband used a crossover cable to connect their modem to your computer (nic-1). You then used a second nic card (nic-2), called it the gateway and then manually configured the ip address, dns, and used the gateway address you gave the second nic card. This required that the computer used to connect to the starband modem be powered up all the time for the other computers to have internet access.

I do not know if the starband modem was set to dhcp or not, not much info made available.

Do you think that if I disabled dhcp on the linksys and left it configured as gateway that the hughes modem would provide ip addresses and dns to the computers on the lan THRU the linksys? The choices on the linksys for internet connection type are: Auto config-dhcp, static IP, PPPoE, PPTP, L2TP, and Telestra Cable.

Thanks for the help and I hope I have explained how things are and provided enough info. Thanks, Chris.

---

### Post by hyper_ch on 2008-03-05
I have really no clue how you setup your network... best is to have your computers and server attached to a router... make it 10.0.0.x network
The router then gets inet data from the modem... that way you have completly different set of ips... not interference...

---

### Post by wolfwatcher51 on 2008-03-05
That is how it is. The hughes modem connects to the internet connection on the linksys wrt54g and the two xp boxes and the sme server connect to the ports on the 54g.
 I can see that the 54g is giving the ip addys to the two xp boxes-192.168.1.20  because they are in the range listed in the 54g. But, the gateway listed in the 54g is the hughes modem gateway addy-192.168.0.1 
The sme server will not allow 192.168.0.1 and 192.168.1.25 because the subnet is 255.255.255.0 and  the third number in the addysa is different. I trie 255.255.0.0 but that did not work either.
Do you know how to see the gateway addy being used in the windows boxes when the tcp/ip is set to obtain automaticalloy, thru dhcp? I see the ip addy but do not know where to go from ther.
Thanks, Chris.

---

### Post by hyper_ch on 2008-03-06
(1) replace the linksys firmware with some decent one (open-wrt, dd-wrt, tomato).

(2) Set the linksys to accept dhcp from the modem and change it's ip range to 10.0.0.x

(3) set your sme to 10.0.0.5 (or some other dedicated IP that is not in the linksys dhcp range) and set its gateway to 10.0.0.1 (assuming that's the IP you give to the linksys router)

---

