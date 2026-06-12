---
title: "Problems connecting to the internet"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by darkchest on 2006-06-13
I am a linux newbie.  My computer has 2 hard drives, master -- XP, slave --Ubuntu 6.0 with xp as the default boot (set up thru the grub).  I have an ethernet card.  The computer - internet connection is

COMPUTER <-->LINKSYS WIRELESS-G BROADBAND ROUTER 2.4GHz <--> WESTELL MODEL 6100 <--> PHONE JACK.

My internet provider is Verizon.  It uses DHCP.

I have tried all that i have searched for and it is becoming frustrating for about 2 weeks and nothing seems to work.  I need to connect to the internet thru Ubuntu so that i can read and try stuff at the same time, not restarting my computer to ubuntu anytime i want to try something.

I dont know if the discription i gave above is enough.  I have been searching this forum, and u guys seem awesome.  I hope someone points me to the right direction.  Desperately need your help.  I am having nightmares because of this stuff (literally).

---

### Post by halfvolle melk on 2006-06-13
Google tells me that linksys router are at 192.168.0.1 . I don't know if that's true, but you may (check the manual if you don't know). You say you have an ethernet card so I'll assume you're using LAN and not WLAN.

Did you try using a static IP? If not, open a terminal (Applications -> Accessories -> Terminal) and type:
```
sudo gedit /etc/network/interfaces
```
Find the section that looks something like this (I don't know what DHCP looks like)
```
auto eth0
iface eth0 inet ?
address x.x.x.x
netmask x.x.x.x
gateway x.x.x.x
```
and make it look like this:
```
auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1
```
Save the file. Then, again in a terminal, type this:
```
sudo ifdown eth0
ifup eth0
```
Hope this is even remotely near the spot.

---

### Post by Ptero-4 on 2006-06-13
Is the wireless configured in ubuntu? Does it need NDiswrapper?

---

### Post by darkchest on 2006-06-13
i did what u asked and this is the result:

sudo gedit /etc/network/interfaces:

the result i got looked like this....

[B]auto lo
iface lo inet loopback

auto eth0 (repeated for eth1 & 2)
iface eth0 inet dhcp  (repeated for eth1 & 2)

auto wlan0
iface wlan0 inet dhcp

iface dsl-provider 
provider dsl - provider[/B]

i didnt see anything that looked like **address x.x.x.x; netmask x.x.x.x or gateway x.x.x.x**.  (I tried what u told me with and without altering the code.  I got the same result.  When i changed the "...inet dhcp" to "inet static", and the "sudo ifdown eth0" wrote SIOCDELRT - no such process")

i also did the "sudo ifdown eth0" and i got:

[B] .... Listening on LPF/eth0/00:15/f2:60:6b:2C
Send on LPF/eth0/00:15/f2:60:6b:2C
send on Socket/fallback[/B]

i then tried the "sudo ifup eth0"
** DHCPDISCOVER on eth0 to 255.255.255.0 port 67 interval 4** (repeated for 4, 9, 15, 12, 17)
[B] No dhcpoffers received
No working leases in persistent database - sleeping [/B]

PS:  the ip addresses i have seen with the router is 192.168.1.1 (if that is relevant)

---

### Post by drtvasudevan on 2006-06-13
i am not sure it will work for you but..
i had problems connecting.
went to the url box in firefox
typed about:config
typed ipv in the filter box
double clicked to toggle value to true
closed firefox; restarted; connected to net.

tv

---

### Post by darkchest on 2006-06-14
it didnt work

---

### Post by physcsdrk on 2006-06-14
I work as technical support for Verizon DSL so I should be able to help you, but really, who knows?  I'm pretty new to Ubuntu but its worth a shot. :) 

Go to System -> Administration -> Network Tools
At the top it will say network device.  Post what the device is (i.e. loopback or ethernet).  Also can you post what it says under the ip information section next to the protocol IPv4?

In the meantime:  Open a browser and  in your address bar type in 192.168.1.1.  If a username and password box pops up the un is left blank and the pw should be admin.  Probably nothing will happen, but if something does pop up it indicates a problem with your firefox settings, not your connection to the router.
(You might try doing this while in windows as well.  Sometimes the linksys router ip addresses will be different.  Try 192.168.2.1 if the .1.1 one doesn't come up in windows.)

---

### Post by darkchest on 2006-06-14
Im sorry it took me soo long to reply.  I am just coming from work.

In reply to physcsdrk, i really appreciate ur presence in my thread.  I did wat u said and this is the result i got....

For the Network tools:
 By default, Network device: **loop interface (lo)**, but in the drop down, there is **Ethernet interface (eth0)**

Ip address information is, there are two rows (i will indicate them by (1) & (2) suffixing the result.
[B]Protocol -->(1)IPv4  (2)IPv6
IP address --> (1)127.0.0.1 (2)::1
Network/Prefix --> (1) 255.0.0.0  (2) 128
Broadcast --> Empty
Sccp --> (2) Host [/B]

Below, this information was displayed
[B] Hardware address: Loopback
Multicast:  Disabled
MTU: 16436
Linkspeed: [empty]
State:  Active[/B]

I tried putting in 192.168.1.1 in firefox in ubuntu and it displayed "Unable to connect"

I tried putting it in firefox in windows and it showed a "westell webpage".

---

### Post by physcsdrk on 2006-06-15
In windows (sorry, the only way I know how)
open a command prompt and type in ipconfig
write down you ip address, subnet mask, and default gateway.

In ubuntu 
open up your network Tools, select eth0 and click configure
make sure the connection is enabled.  (if it wasn't, enable and just try that first)
change from dhcp to static
type in the information you wrote down while in windows.

That should work but if it doesn't we can try something else. :)

---

### Post by tommcd on 2006-06-15
Have you been able to connect to the net at all with Ubuntu? If not, try the simple way first. Hook the computers wired ethernet port directly to the westell modem. Set eth0 to use DHCP. Open terminal and type:
sudo pppoeconf
You then answer a series of questions (answer defaults to all) Enter your verizon username & password when prompted (backspace out 'username' and 'password' first). This should get you online. Verizon uses PPPoE so you need to configure that. I have verizon DSL and that is how I did it. I don't use a router though.
After you are online from the westell modem, then hook up the router, there should be a way to set the router for DSL/PPPoE, or just DHCP, whatever the manual says or however you do it with windows. Hope this helps.

---

### Post by physcsdrk on 2006-06-15
Actually Verizon sometimes uses dhcp and sometimes PPPoE, depending on your area.  Verizon is in the process of upgrading all dhcp areas to PPPoE.  And with the westell modem that darkchest has it actually stores the un and pw for authentication with verizon if darkchest is PPPoE.  As far as the computer to router/modem connection is concerned, darkchest is dhcp because thats how ip addresses are assigned to computers on the lan.

---

### Post by tommcd on 2006-06-15
So physcsdrk, does darkchest not have to configure Ubuntu for PPPoE at all because the info is stored in the westell modem? I have a westell 2200 and each time I boot up I have to type: 'pon dsl-provider' to get online.
 Should his modem connect automatically then, even without configuring Ubuntu for PPPoE? Perhaps he should try getting online directly through the westell modem first anyway then, just to make sure he can establish a connection.

---

### Post by darkchest on 2006-06-15
actually...tommcd...i tried gettin online directly from the westell modem while readin all the posting that doesnt seem to work.  I also tried the "sudo pppoeconf" and the reply that option gives me is "TIMED OUT" (maybe not the exact words but means the same.  It shows this red bar on a blue screen that loads up to 100%  and writes timed out, then starts again and times out again.  Then says that if failed to establish a connection.  and u have to click "Yes" and it returns back to your command line.

I got the router bcos i wanted to see if i could connect with it, but it is still giving me stress.  (Connecting to the internet thru the modem after trying everything i read from this forum and online research, was not bring positive results).  And now, the airport on the mac in the house isnt working.  (That is another thread for another forum.)  Even after calling tech support...they only know a lot about windows....they dont know much about mac, and linux is out of the question.

I feel that this is a major "discouragers" to linux.  Not having enuff hardware being recognized (at least the basic components like internet).  That is one of the things that would make windows rule the market for sometime.

physdrk>>im posting this in reply to tommcd.  I believe i have tried your method, but im going to do it again just to make sure.  But i know i have done a lot of configuring in everyplace.  But maybe i need to follow a specific pattern.  Brb soon

---

### Post by darkchest on 2006-06-15
Some freaking ***t just happened.  Right now i am posting this message from my ubuntu os.  I am sooo freaking happy that i just had to place this reply.  I would check my settings to find out what happened, but i saw my brother playing around with modem and stuff.

Right now i am connected directly from the modem, not thru the router.  Maybe there was something i changed while i was on the router that is actually meant to be for the modem.  SOmething funny happend when starting my computer.  It said there was a problem with my cmos settings, but i set it up the date, and that was it.  Ubuntu loaded and then i saw there were updates ready for my computer, then i knew that was it.

I will post my theory and settings on the internet, maybe that would help similar people with the same problem.  I will also ask my brother what he did to the modem, bcos he also knows the settings of the modem.  As soon as i get back, i will do just that.  That should be about 15hours of posting this msg.

Thanks to all of you, physcsdrk, tommcd and drtvasudevan, you guys were great.  Sorry about posting a little bit of frustration on the internet, but its true.  "Ubuntu-lites", i know it is not easy, but auto driver recognition is seriously needed.  Maybe there is a reason for them not putting it on, but if you want to improve marketability to the world, it is needed.

Till i get back.  Gotta head to work now. 

PS:  If there is any other problems, i will surely bring it to your attention.

---

### Post by tommcd on 2006-06-16
Glad you finally got online Darkchest. Guess you must use DHCP as Phycsdrk suggested. I thought all verizon DSL used PPPoE. Let us know how you got it to work. I am interested to find out what the solution was.

---

### Post by physcsdrk on 2006-06-16
Darkchest modem is already configured because he can connect via windows.  If  you want to configure your modem this is what you do.
open browser
type 192.168.1.1 in your address bar
un is admin
pw is password
it will come up to a change pw screen.  type admin in all three boxes. 
(so tech support can help you later if you have a windows box)
click profile editor
type your un and pw (admin and admin)
click edit or if there is no edit button click new connection
account id is your verizon un
account pw is your pw
click save or new 
click disconnect (if its there) and then click connect
close the screen. 
you shouldn't have to do anything else to always be online again

---

### Post by darkchest on 2006-06-16
Should i say it was a false alarm.  After restarting the computer twice, the same problem started again.  The good news is that the modem works with ubuntu, but i dont know y i cant connect to the internet anymore.  Another round of research on the way.

---

### Post by darkchest on 2006-06-16
U remember when i said that i did some cmos setup.  That was actually the give away.  I tried everything i could to get back on the internet, then there was this particular thread that i saw the clause "when u shutdown, your computer is not necessarily turned off".  That triggered me to turn off the computer, remove the cord from power supply and wait for sometime, like 30mins.  (At least for the little green light that is forever on to fade out)

I turned it back on, the computer prompted me to update my cmos set up, and i booted directly to ubuntu and 'wala' im back posting this reply from my linux drive.

It is a weird solution but i am almost sure that it will work again.  All those out there having the same problem with a dual boot pc (xp and linux) try it and reply if it would work for you.

---

### Post by tommcd on 2006-06-16
I saw a thread once about a bug in a particular brand of ethernet adapter (don't recall what brand). In a dual boot setup with XP and Ubuntu, Windows would leave the ethernet adapter in a non-functioning state, and Ubuntu would not be able to connect to the net. The solution was to power down and unplug the power cord, as you did Darkchest. Perhaps this is the cause of your problem. Did you go online with XP after getting online with Ubuntu?
I can't think of anything else! If you get online with Ubuntu again, don't boot XP for a while and see if the problem goes away.

Physcsdrk, would that proceedure you described, going to  192.168.1.1, be the same for any Westell modem? Just curious, I also have a westell 2100 and a 6100.

---

### Post by physcsdrk on 2006-06-16
There are many different models of westell but basically two different kinds: "smart" and "dumb".  tommcd both of your modems are smart but I will post about both in case anyone else reads this thread.  

Dumb modems have a light marked ready and smart modems have a light marked dsl.  

Everything I am writing is for people with PPPoE.  

Dumb modems: 
Use pppoeconf to configure your internet connection.
If you want to use a router hook it up and configure as usual. More on router configuration at the bottom of the post.


Smart modems: 
type 192.168.1.1 in the address bar of your browser.  Default un and pw is admin and password.  (if this doesn't work reset the modem.  reset button is on the back, you'll need a pen or something, and you need to hold it in for 15 FULL seconds)  A change pw screen will come up, if you have a windows box type admin in all of the boxes so you can call tech support if you ever need too.   Click profile editor, pw and un box comes up, type in admin and admin.  Click edit, your account id is your verizon pw, your account pw is your verizon pw.  click save.  click disconnect, when your ppp status says down click connect.   At this point you should be online.


Routers:
Dumb modem:
hook it up, type in the address of the modem (192.168.1.1, 192.168.2.1, 192.168.1.254, 192.168.0.1, 192.168.1.100) and try any combination of admin and password to log in including leaving un and or pw blank.  change from automatic configuration or dhcp to PPPoE.  Type in verizon un and pw.  save and go to your status tab.  click connect.  voila

smart modems: 
smart modems have to be configured to work with a router.  type 192.168.1.1 into a browser, log into the modem and change the pw.  click configuration then vc configuration.  click the first edit button.  change your protocol from PPPoE to bridge.  click set vc.  its going to reset your modem at this point.
click configuration and then dhcp configuration.  Change your dhcp server from private lan to off.  click configuration and then private lan configuration.  the top box should NOT have a checkmark in it.  save and hook up the router.  configure the router as mentioned above.



I think  I am going to write a howto on verizon dsl but above is the condensed version.  
Hope this helps some people.  :)

---

### Post by darkchest on 2006-06-17
I tried to go online on dapper after going online with windows, it didnt work.  So i did the shutdown process again and removed the cable.  Im once again online with dapper.  So the theory has been proven, it may be the bug on the ethernet card, but shutting down and removing the plug for about 5mins fixes the problem.

There is actually a green light on my board, once it goes out, i believe it is ready to put the plug back in.

But i noticed something on windows (this is not a windows question).  When i used to press standby on my keyboard, the  system goes off, even the hard drive and cpu.  To turn it on, i had to press the power button.  But now, if i standby, the cpu stays on and if i move the mouse the standby would be deactivated.  I have a Asus A8N VM CSM.  I would like to take it back to the way it was.

This is a little divergence from the topic, but i would like to fix it badly.  It is one of those annoying things that doesnt make my computer feel complete.

Great guys thanx a lot.

---

