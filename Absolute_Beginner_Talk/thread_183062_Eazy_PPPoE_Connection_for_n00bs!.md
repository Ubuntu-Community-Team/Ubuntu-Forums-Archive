---
title: "Eazy PPPoE Connection for n00bs!"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by %hMa@?b&lt;C on 2006-05-27
I will try to make this as straight foreward as possible, although I am not the greatest of explainers. This guide is due to my hours of frusteration with my PPPoE setup and with the horrible tool that is "pppoeconf"

Here is what you need: 
1: Your ISP must provide you with PPPoE (the point-to-point over ethernet protocal)
2: I have a modem, I think you need one, but a USB modem will probably not work
3: You need your ISP's username and password, in this guide for username i will use "username" and for password "password"

OK LET'S GET STARTED :KS 

Step 1, get the software!
```
sudo apt-get install build-essential
```
we will be using some software not from the Breezy Repos. it is called "roaring penguin pppoe" to download it run this from terminal.
```
wget http://www.roaringpenguin.com/penguin/pppoe/rp-pppoe-3.8.tar.gz
```
then extract it
```
tar xzf rp-pppoe-3.8.tar.gz
```
now lets enter the directory
```
cd rp-pppoe-3.8
```

Step 2, run the software!
to run the setup tool type
```
sudo ./go
```
press enter to skip all information except entering your username and password and firewall info. for username you do not need the @xxx.com from my experiences i just typed my username. for firewall you want to choose option 1

Step 3, test your internet connection!
run this 
```
sudo pppoe-start
```
if it doesnt work, go back to step 2 and make sure all of the info you put in was correct

Step 4, add PPPoE connection to startup!
you will need to make this pppoe client run with sudo without a password for a seamless connection at startup, first we need to edit out sudoers file
```
export EDITOR=gedit && sudo visudo
```
paste the following lines at the bottom of the file, replacing "username" with your username
```
username ALL= NOPASSWD: /usr/sbin/pppoe-start

username ALL= NOPASSWD: /sbin/ifconfig
```
save and exit.

next will will actually add it to startup.
at the top gnome-panel, you will need to go to 
System>Preferences>Sessions
from there go to the "Startup Programs" tab
click "Add"
paste this in
```
sudo pppoe-start
```
make the priority 50
now press "OK"
click "Add" again
paste this in 
```
sudo ifconfig lo localhost
```
again priority is 50
press "Ok"
click close
REBOOT, you should be automaticly connected to the internet!

---

### Post by Iarwain ben-adar on 2006-05-27
Thanks for the explenation :-)

Will try it right away ^^



Iarwain

---

### Post by %hMa@?b&lt;C on 2006-05-27
anyone who was tried this guide please provide feedback, did it work? if not what went wrong?

---

### Post by chiok on 2006-06-05
Howdy.  Thanks for this.  pppoe has always given me trouble on Ubuntu.

A few things.  First, I *think* you need to install build-essential first.  Every other guide to install rp-ppoe says you have to, so I did.  Second, you need to add sudo to "./go".  Third, the instructions are Gnome specific.  I was in xfce and while there is a place to edit Sessions, there wasn't a "Startup Programs" tab.  And lastly, when I went over to Gnome there wasn't a place to set the priority.  (I'm using Dapper, so maybe they got rid of the option to set the priority.)

Anyway, I am now connected to the internet after a reboot.  Huzzah!

---

### Post by mjunior on 2006-08-17
This is a KDE only supported feature? I tried to install into Drapper Gnome and I got a "C compiler missing" message !

---

### Post by mgor on 2006-08-17
> **mjunior said:**
> This is a KDE only supported feature? I tried to install into Drapper Gnome and I got a "C compiler missing" message !

like the previous poster wrote, install build-essential first,
```
sudo apt-get install build-essential
```

---

### Post by dfreidus on 2006-08-17
I tried what they said, but i was not able to install build-essential first as I don't have an ulternative connection to the internet on that computer. So I still get an error. Thanks

---

### Post by dfreidus on 2006-08-18
Hi, I have now managed to install build essential.
However, after I type in ./go, it starts to run the program but I eventually encounter the following before I can input anything:
[I]
On this platform, the following targets will be built:
pppoe pppoe-server pppoe-sniff pppoe-relay
Type 'make' to compile the software.
Running make...

Type 'make install' as root to install the software.
Running make install...

Type 'make install' as root to install the software.
mkdir -p /usr/sbin
/usr/bin/install -c -m 755 pppoe /usr/sbin
/usr/bin/install: cannot create regular file `/usr/sbin/pppoe': Permission denied
make: *** [install] Error 1
Oops!  It looks like make install failed.
[/I]
Please can someone help me.
Thanks

---

### Post by %hMa@?b&lt;C on 2006-08-18
sorry, you need to run ./go as root so try
```
sudo ./go
```

---

### Post by dfreidus on 2006-08-19
Hi,

Thanks so much for replying. After adding the sudo line the program runs well. It asks me for the info which I give it. However, when typing in 'sudo pppoe-start' it still doesn't connect to the internet it says '.........TIMED-OUT'.
Please help me again.
Thanks very much.

---

### Post by %hMa@?b&lt;C on 2006-08-19
what is the output when you type 
```
ifconfig
``` into the terminal?
if you post that, i think I know what the problem may be!

---

### Post by catlett on 2006-08-19
Hi Jeff,

This appears to work well and be helping. Now that you have worked out your posts "bugs" and have it edited, don't forget to post it as a "how to" in [http://www.ubuntuforums.org/forumdisplay.php?f=100](http://www.ubuntuforums.org/forumdisplay.php?f=100) 

Take care.

---

### Post by %hMa@?b&lt;C on 2006-08-19
> **catlett said:**
> Hi Jeff,

This appears to work well and be helping. Now that you have worked out your posts "bugs" and have it edited, don't forget to post it as a "how to" in [http://www.ubuntuforums.org/forumdisplay.php?f=100](http://www.ubuntuforums.org/forumdisplay.php?f=100) 

Take care.

thanks **catlett**! I posted in the HowTo's just now!

---

### Post by dfreidus on 2006-08-20
Hi,

the output is as follow:

saaddick@desktop:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

Thanks

---

### Post by dfreidus on 2006-08-20
Hi,

I managed to get my internet working. I just had to install the drivers for my specific modem.

Thank you very much for your help, you have now inabled me to continue using ubuntu.

---

### Post by %hMa@?b&lt;C on 2006-08-20
Glad to have helped! Congratulations on your success.

---

### Post by mjunior on 2006-08-21
Oh sorry, had forgotten the first step..

Ok.. now I have the build-essential package and the installation guide goes smoothly till the end.., but despite I have a green link status on pppoe-start (on go-gui), I have no ping or web browsing to the net..

I have a windows partition on my pc, so I'm sure the username and password are granted using the pppoE dialup tool on WinXP-pro. Also, I tested the PPPoE authenticantion through the adsl cpe and works fine too.

Any idea?

---

### Post by %hMa@?b&lt;C on 2006-08-21
Your DNS is the problem. 
what is your ifconfig output
i can help you from there

---

### Post by mjunior on 2006-08-21
DNS??

I have no response even for simple ip ping test either..I also tried on the go-gui the "from server" and "specify" options with no luck...
As I said on last post..from adsl cpe I can manage to connect using internal pppoe authenticator...
Using the cpe or the eth0 dns proprieties to force a few dns servers doesn't work as well.

My ifconfig output is as below:

marcelojunior@mjunior:~$ ifconfig
eth0       Encapsulamento do Link: Ethernet  Endereço de HW 00:50:EB:0E:30:BF
          inet end.: 10.1.1.3  Bcast:10.255.255.255  Masc:255.0.0.0
          endereço inet6: fe80::250:ebff:fe0e:30bf/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:13192 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:16701 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000
          RX bytes:4631489 (4.4 MiB) TX bytes:9722315 (9.2 MiB)
          IRQ:201 Endereço de E/S:0xd400

lo         Encapsulamento do Link: Loopback Local
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:11 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:11 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0
          RX bytes:572 (572.0 b) TX bytes:572 (572.0 b)

ppp0       Encapsulamento do Link: Protocolo Ponto-a-Ponto
          inet end.: 201.27.163.24  P-a-P:200.204.210.250  Masc:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Métrica:1
          pacotes RX:4 erros:12 descartados:0 excesso:0 quadro:0
          Pacotes TX:4 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:3
          RX bytes:114 (114.0 b) TX bytes:61 (61.0 b)

---

### Post by %hMa@?b&lt;C on 2006-08-22
ok, i have no idea how to read spanish :( but i still know what your problem is.  go to System>Administation>Networking click on your eth0 connection
hten properties.  Change it to a static IP.  Make the IP address 10.1.1.3 and the gateway mask 255.255.255.0 press ok then reboot.  If that doesnt work, do 
System>Administration>Networking click on your eth0 connection, set it to dchp. pressok then set the default gateway to eth0. that should fix it!

---

### Post by MaximB on 2006-08-22
it's nice - but it's too long
why not to use just :
"sudo pppoeconf" ???

---

### Post by %hMa@?b&lt;C on 2006-08-22
> **MAXDDARK said:**
> it's nice - but it's too long
why not to use just :
"sudo pppoeconf" ???

If sudo pppoeconf works for you then it is great!
I had loads of trouble with it in breezy, i couldnt connect to localhost after using pppoeconf and i would have to run pppoeconf every time i rebooted to connect.  I wrote this a while ago when I was having the problems.

---

### Post by MaximB on 2006-08-22
you know - I too had a problem after "sudo pppoeconf"
my ISP's DNS address kept reseting itself every 15 minutes.
what I did was simply after I made all the network configurations I made the .conf file to be "read only".
it works great !

---

### Post by thijs on 2006-08-22
us ```

 1 make
 2 sudo make install 
``` to install it.

---

### Post by mjunior on 2006-08-23
It works!!

Ok, it works...but i still intrigued..
Since now I know for sure that the problem wasn't the dns issue we thoght at first sight..the remaining questions are:
- Why the ppp connection connects but don't allow browsing??
- Why while using DHCP I couldn't surf the web and using static went normally?


I need another tip..How can I add a icon on my desktop to call the go-gui script? 

Thanks so far!

---

### Post by %hMa@?b&lt;C on 2006-08-24
> **mjunior said:**
> It works!!

Ok, it works...but i still intrigued..
Since now I now for sure that the problem wasn't the dns issue we thoght at first sight..the remaining questions are:
- Why the ppp connection connects but don't allow browsing??
- Why while using DHCP I couldn't surf the web and using static went normally?


I need another tip..How can I add a icon on my desktop to call the go-gui script? 

Thanks so far!

question 1.  That was the DNS problem.  You were connected to teh internet, and if you tried to ping google.com you couldnt, but if you tried to ping Google's IP address that would work
question 2. I have no idea, but that is how it worked for me.
If you follow the latter part of my guide then it adds the non-graphical utility called "pppoe-start" to your bootup.
If you really want, I will write a shell script to run go-gui.

---

### Post by Malac on 2006-08-24
> **mjunior said:**
> 

I need another tip..How can I add a icon on my desktop to call the go-gui script? 


Right-click on the desktop and select "Create Launcher".
In the form change the command field to
 "go-gui" (without the quotes) [You may need the path also depending on where it is.]
Choose a new icon if you want.
Then name the link (e.g. "Connect") and save it.

That should do it.

---

### Post by mjunior on 2006-08-24
Thank you jeffc313...

About the dns..as I said on previous posts..I have no ping eighter from IP addresses..so that's why I doubt it was a dns issue anyway.
About the icon..I don't want the pppoe client to start on boot up..just want to set an icon to call it when needed.

Malac, I tried to add a laucher as you said..
/home/marcelojunior/rp-pppoe-3.8/go-gui
But when I click the icon..nothing happens.

---

### Post by %hMa@?b&lt;C on 2006-08-24
> **mjunior said:**
> Thank you jeffc313...

About the dns..as I said on previous posts..I have no ping eighter from IP addresses..so that's why I doubt it was a dns issue anyway.
About the icon..I don't want the pppoe client to start on boot up..just want to set an icon to call it when needed.

Malac, I tried to add a laucher as you said..
/home/marcelojunior/rp-pppoe-3.8/go-gui
But when I click the icon..nothing happens.

you need to have it run as root if i recall correctly

---

### Post by Malac on 2006-08-25
> **mjunior said:**
> Malac, I tried to add a laucher as you said..
/home/marcelojunior/rp-pppoe-3.8/go-gui
But when I click the icon..nothing happens.

Change command line to:
```
gksudo  /home/marcelojunior/rp-pppoe-3.8/go-gui
```

---

### Post by mjunior on 2006-08-25
> **Malac said:**
> Change command line to:
```
gksudo  /home/marcelojunior/rp-pppoe-3.8/go-gui
```

Thanks Malac..it works!

---

### Post by mjunior on 2006-08-25
Ok guys..

As I said I'm still intrigued about my issue..so i kept doing tests

Here's a more comprehensive detail I found today:
I changed the dhcp mode at my cpe (Dlink DSL500G) from server to relay..
So now I'm not using nat or receiving private IP addressing from modem but directly a valid IP from the telco.
Now I can surf using dhcp on my eth0...

My first hop now isn't the cpe anymore..

marcelojunior@mjunior:~$ traceroute [www.google.com](www.google.com)
traceroute: Warning: [www.google.com](www.google.com) has multiple addresses; using 64.233.161.99
traceroute to [www.l.google.com](www.l.google.com) (64.233.161.99), 30 hops max, 40 byte packets
 1  200-204-210-250.dsl.telesp.net.br (200.204.210.250)  49.739 ms  31.211 ms  20.258 ms
 2  200-204-115-101.dsl.telesp.net.br (200.204.115.101)  49.366 ms  26.368 ms  24.870 ms
 3  200-204-20-197.dsl.telesp.net.br (200.204.20.197)  22.861 ms  21.555 ms  20.127 ms
 4  200.207.250.69 (200.207.250.69)  38.868 ms  23.700 ms  25.314 ms
 5  200-148-160-117.bbone.tdatabrasil.net.br (200.148.160.117)  25.821 ms  21.666 ms  25.551 ms
 6  So2-3-0-0-grtsanem1.red.telefonica-wholesale.net (213.140.51.105)  36.322 ms  23.898 ms  29.389 ms
 7  213.140.43.149 (213.140.43.149)  129.526 ms So5-2-0-0-grtmiabr3.red.telefonica-wholesale.net (213.140.36.13)  132.401 ms 213.140.43.149 (213.140.43.149)  130.295 ms
 8  P9-0-grtwaseq1.red.telefonica-wholesale.net (213.140.36.50)  158.894 ms  170.571 ms  154.665 ms
 9  So6-2-0-0-grtnycpt3.red.telefonica-wholesale.net (213.140.37.53)  163.245 ms  163.556 ms  158.126 ms
10  72.14.197.73 (72.14.197.73)  160.290 ms  160.704 ms  159.627 ms
11  72.14.236.212 (72.14.236.212)  160.541 ms 72.14.236.214 (72.14.236.214)  164.941 ms 72.14.236.212 (72.14.236.212)  165.904 ms
12  216.239.46.137 (216.239.46.137)  166.884 ms 66.249.94.235 (66.249.94.235)  166.264 ms  171.325 ms
13  72.14.238.232 (72.14.238.232)  163.268 ms  164.010 ms  165.988 ms
14  72.14.236.200 (72.14.236.200)  165.247 ms  164.418 ms 72.14.236.202 (72.14.236.202)  165.763 ms
15  216.239.48.190 (216.239.48.190)  172.076 ms  171.894 ms  168.199 ms
16  64.233.161.99 (64.233.161.99)  169.938 ms  168.609 ms  165.245 ms



The strange thing is that the previous scenario (using dhcp server and nat) I had connection normaly while using WindowsXP pppoe authenticantion and by using Ubuntu, the only way I found was forcing private IP range from cpe on my eth0..

---

### Post by funk19 on 2006-12-02
If you have installed RP-PPPoE but don't have a GUI interface the following post will provide a GUI for you to use. Because we are all unique I am going to include my full install procedure below.

I compiled RP-PPPoE from source as follows:

wget -c [http://easylinux.info/uploads/rp-pppoe-3.6.tar.gz](http://easylinux.info/uploads/rp-pppoe-3.6.tar.gz)
sudo tar zxvf rp-pppoe-3.6.tar.gz -C /opt/
sudo chown -R root:root /opt/rp-pppoe-3.6/
cd /opt/rp-pppoe-3.6/src
sudo ./configure
sudo make
sudo make install

Once done I then setup the GUI interface as follows:

In terminal run:

gksudo gedit /usr/share/applications/RP-PPPoE.desktop

* Insert the following lines into the new file that opens

[Desktop Entry]
Name=RP-PPPoE
Comment=RP-PPPoE
Exec=sudo tkpppoe
Icon=pppoeconf.xpm
Terminal=false
Type=Application
Categories=Application;Network;

* Save the edited file
* Find your new application in Applications -> Internet -> RP-PPPoE

You can then setup as many pppoe connections as you like and connect/disconnect as needs be. For a tutorial on how to add connections I found a help file at: /opt/rp-pppoe-3.6/gui/html/tkpppoe.html

---

### Post by TygerBS on 2007-05-08
Thanks for this thread.

I am and advanced pc user, but this is my first move into the linux world.

After following the instructions in this thread, i managed to get the alternative dsl connection working.
Only problem i had from thes instructions, is the wget for the pppoe package didnt work, i had to download it manually through the browser.
The standard ubuntu dsl connection aslo worked for me.

The problem i still have is that the dns servers drop/change and i can no longer resolve any dns queries after about 2 minutes of being connected.

How do i resolve this?
Is there a config file i can manually input my dns server address, and save it?

At the moment this is frustrating my attempt at evaluating and using ubuntu.

---

### Post by Madejyalook on 2007-06-03
Will this work with a live CD? There's several things that have to be installed, where do they go? The hard drive that has windows on it? That sounds like it would cause trouble. I started this, but got a bit scared when it said it would take up 47.1 MB of space, and I have no idea where it's going.
Also, just wondering, how can the "wget http://www.roaringpenguin.com..." work when there's no internet connection?
Sorry if this should be obvious. I guess I'm a tad slow.

---

### Post by zvacet on 2007-06-04
> I had loads of trouble with it in breezy, i couldnt connect to localhost after using pppoeconf and i would have to run pppoeconf every time i rebooted to connect. I wrote this a while ago when I was having the problems.

This is the way to set net without rp-pppoe.

System>administration<network setting>select your modem>properties>select your type of connection(dhcp or static)>close>DNS tab>delete address you find there and put your nameservers instead>close

```
pppoeconf
```

---

### Post by island3 on 2007-09-13
Gee, I'm glad you spelled it*** eazy***, because it doen't seem very easy to me.

I haven't tried the suggested method here yet, but wanted to ask about* ppoe conf*.

When I type it in the terminal after* sudo* I get * command not found*

The prgram manager says it is installed.

I have a connection with a modem using a* lan* to connect to my ISP ( with PPoe protocol). I use an ip address, login and password over an adsl line. 

I don't know if the ethernet card is installed on my machine or if it is present in the Windows XP Os which has a working connection. How would I find out?

Any help would be much appreciated, because I really want to try Feisty 7.04 and get off of depending on Windows, though I have megatons to learn about computers. 

:)
Thanks.

---

### Post by island3 on 2007-09-13
Found another thread and resolved the "pppoe not found" command, but the Internet connecton is still not set up. There was no place in the terminal text set-up to enter the address and subnet; not sure if these would be found automatically? And I got a "authentication failed" in the log.

Does anyone know if I might to do something extra because my connection is over a Local Area network ( only used to connect to my IP)?

Any help would be appreciated. I have the 7.04 Feisty.

:)

---

