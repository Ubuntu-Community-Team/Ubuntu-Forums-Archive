---
title: "configuring internet connection"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by nycrunner87 on 2006-06-27
Hi

i just installed ubuntu on my home desktop after considerable trouble. now i love everything except internet doesnt work:-k 
if there are a certain set of commands to configure my wired ethernet adapter i would really appreciate it if someone can point me to it. i tried searching previous threads but i couldnt find much. im totally new to ubuntu and linux so i have no idea where to even begin.

as i was searching previous threads, i saw several references to a quick starter guide. if such a thing really does exist (i couldnt find it after searching here and on google), could someone please point me to that too? would that have information on configuring ethernet?

thanks!

---

### Post by WADemosthenes on 2006-06-27
I'm not entirely sure (I'm a noob myself :P) but if it's wired it should be very simple.  You need to find some kind of networking program in gnome (your default GUI, I use Xfce so I don't know where your's is)  somewhere under settings or system, and configure it to be eth0 using dhcp.  You shouldn't have to use the cammand line.

---

### Post by arochester on 2006-06-27
You may need the program PPPoe

---

### Post by rccharles on 2006-06-27
[QUOTE=arochester] internet doesnt work[/QUOTE]

Ubunto is setup to configure your internet communications autamatically.  Windows is set up this way too.  Does a window box work on you internet without configuration?  For automatic configuration to work, you need  a dhcp server on your lan. 

First, I'd try to verify that the cabling works.  I'd try using the same cabling as a previously working Windows box.
 
Get yourself in to the terminal application. See:
[http://www.psychocats.net/ubuntu/terminal.html](http://www.psychocats.net/ubuntu/terminal.html)

Issue the command:
ifconfig
and post the result back here.

This command will tell you the status of the internet connections.

Also, a copy of 
cat /etc/network/interfaces

This file shows how you communication interfaces are configured.

The command:
ping 127.0.0.1
and control-c to stop.
will show if you commication software has been installed correctly.

Also, the command man interfaces may provide some more info.
man interfaces

Robert:)

---

### Post by nalmeth on 2006-06-27
[http://www.ubuntuforums.org/showthread.php?t=87643](http://www.ubuntuforums.org/showthread.php?t=87643)

---

### Post by nycrunner87 on 2006-06-27
I tried typing in "pppoeconf"; it seemed to be some kind of network configuring tool. it recognized the presence of "eth0", my wired card, butafter it ran, the utility came back unsuccessfully with an error and said:

Not Connected
Sorry, I scanned 1 interface, but the Access Concetrator of your provider did not respond. Please check your network and modem calbes. Another resaon for the scan failure may also be another running pppoe pprocess which controls the modem.

The box is a linux/xp dual boot box, and everything works fine in windows.

ifconfig had the following result:
eth0   Link encap: Ethernet  HWaddr 00:09:A1:OF:C7:92
         inet addr: 192.168.2.8  Bcast 255.255.255.255  Mask 255.255.255.0
         inet6 addr: fe90":209:a1ff:fe0f:c782/64 Scope: Link
         UP  BROADCAST MULTICAST  MTU:1500 Metric:1
         RX packets: 26 errors: 286 dropped:0 overruns:0 frame:0
         collisions:0 txqueuelen: 1000
         RX Bytes: 4142 (4.0 Kib) TX bytes: 2854 (2.7 Kib)
         interrupt: 177 Base address: 0xd800

lo
         Link encap: Local Loopback
         inet addr: 127.0.0.1  Mask: 255.0.0.0
         inet6 addr:  :: 1/128 Scope: Host
         UP LOOPACK RUNNING MTU:16436 Metric:1
         RX packets: 31 errors:0 dropped:0 overruns:0 frame:0
         collisions:0 txqueuelen:0
         RX bytes: 2756 (2.6 KiB) TX bytes: 2756 (2.6 KiB)


cat etc/network/interfaces
auto lo
iface l0 inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



and i was able to ping 127.0.0.1. (im assuming this is localhost?)
and im looking into the man interfaces
THANKS A LOT FOR YOUR HELP GUYS (and GIRLS possibly)!

ps: kinda unrelated but i noticed that the file /etc/network/interfaces is a one that i caon only read. i dont have admin access to this. how is this possible?? i only made one account when ubuntu installed and it never said anything about making another root account.

---

### Post by rccharles on 2006-06-28
[QUOTE=nycrunner87]

ps: kinda unrelated but i noticed that the file /etc/network/interfaces is a one that i caon only read. i dont have admin access to this. how is this possible?? i only made one account when ubuntu installed and it never said anything about making another root account.[/QUOTE]

sudo gedit /etc/network/interfaces

enter your logon password.

sudo will give you root access for one command.  To do multiple root commands, do:
sudo bash
...
exit 

to end.

Robert:)

---

### Post by linuxunil on 2006-06-28
you can try using the network tools under gnome by going to system administration and networking tools. You might try deactivating and reactivating the card as well as entering the dns servers (assuming you know them).  Also any information on what kind of ISP you have and what hardware you have.  If your not sure on how to figure this out pm me and i'll walk you through it.

---

### Post by rccharles on 2006-06-28
[QUOTE=nycrunner87]
ifconfig had the following result:
eth0   Link encap: Ethernet  HWaddr 00:09:A1:OF:C7:92
         inet addr: 192.168.2.8  Bcast 255.255.255.255  Mask 255.255.255.0
         inet6 addr: fe90":209:a1ff:fe0f:c782/64 Scope: Link
         UP  BROADCAST MULTICAST  MTU:1500 Metric:1
         RX packets: 26 errors: 286 dropped:0 overruns:0 frame:0
         collisions:0 txqueuelen: 1000
         RX Bytes: 4142 (4.0 Kib) TX bytes: 2854 (2.7 Kib)
         interrupt: 177 Base address: 0xd800
[/QUOTE]

Edit:  I no long believe that the gateway address will appear here.

Have you followed nalmeth advice?  
   [http://www.ubuntuforums.org/showthread.php?t=87643](http://www.ubuntuforums.org/showthread.php?t=87643)

I hope you figured how to copy a command output to disk. 
ifconfig >outputfile.txt

[QUOTE=nycrunner87]
and i was able to ping 127.0.0.1. (im assuming this is localhost?)
[/QUOTE]
yes

Robert:)

---

### Post by nycrunner87 on 2006-06-28
oh wow that copy to a text file command is the greatest thing good to know
i ll follow these suggestions and see where i get. i ll be out of town for a while so im not going to try them out right away. but thank a lot for your input and help!!
signing off for now
have a good weekend

---

### Post by rccharles on 2006-06-29
[QUOTE=nycrunner87]
cat etc/network/interfaces
auto lo
iface l0 inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

[/QUOTE]
Do you have more than one ethernet card on your system?  Maybe you could remove all but one. 

Perhaps Ubuntu cannot figure out which lan card to use.  

You may want to try the Ubuntu networking forum.
[http://www.ubuntuforums.org/forumdisplay.php?f=136](http://www.ubuntuforums.org/forumdisplay.php?f=136)

Have a good weekend.

Robert:)

---

### Post by nycrunner87 on 2006-07-04
haha oh wow somehow ubuntu automatically connected to the internet. i did nothing but now im proud to say im posting this comment from my linux box. ha

now i ll just fidget around with teh sound and this comp will be ready to go
thanks a lot!

---

### Post by rccharles on 2006-07-05
[QUOTE=nycrunner87]haha oh wow somehow ubuntu automatically connected to the internet. [/QUOTE]Happy surfing.
Robert:D

---

