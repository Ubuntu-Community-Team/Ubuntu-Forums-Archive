---
title: "Cant connect to the internet"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by blunt1 on 2006-09-14
:confused: I can't connect to the internet on ubuntu?! Any ideas?! 

I have a broadband internet connection using a Motorola Surfboard (SB5101E) Cable Modem connected to a D-link (DES-1008D) 10/100 Fast Ethernet switch.
I am using a Win XP PC (This is what I am using to post on here!) and Ubuntu PC which are both connected to the Ethernet switch via RJ45 Network cables.

What do I need to do to get online?! I am a total beginner!:confused: 

My network card (eth0) is activated in Networking...

Let me know if you need anymore info!:) 

Thanks,
JB

---

### Post by RobsterUK on 2006-09-14
Try doing this:
Open a terminal via Applications > Accessories > Terminal

Type: ping -c3 [www.google.com](www.google.com)

this will tell us if its a browser problem or internet access generally

---

### Post by xpod on 2006-09-14
I think typing "ifconfig" in the terminal shows your active network stuff.

I just recall being told to use it myself to check my network connections.
Not sure what you would do after that though but at least you`ll have more info

---

### Post by Najand on 2006-09-14
yes, "ifconfig" and "netstat" are the commands you need to see to be able to say what  is the problem.

---

### Post by blunt1 on 2006-09-14
> **RobsterUK said:**
> Try doing this:
Open a terminal via Applications > Accessories > Terminal

Type: ping -c3 [www.google.com](www.google.com)

this will tell us if its a browser problem or internet access generally

after doing this it says:

ping: unknown host [www.google.com](www.google.com)

---

### Post by blunt1 on 2006-09-14
> **RobsterUK said:**
> Try doing this:
Open a terminal via Applications > Accessories > Terminal

Type: ping -c3 [www.google.com](www.google.com)

this will tell us if its a browser problem or internet access generally

> **Najand said:**
> yes, "ifconfig" and "netstat" are the commands you need to see to be able to say what  is the problem.

I have done this... is there anything I should look for in particular?

---

### Post by Najand on 2006-09-14
Is it possible to send the output here?

---

### Post by ComplexNumber on 2006-09-14
**blunt1**
go to the command line, and type in: 'ping 66.102.9.99'

thats one of the addresses of google.com

---

### Post by blunt1 on 2006-09-14
> **ComplexNumber said:**
> **blunt1**
go to the command line, and type in: 'ping 66.102.9.99'

thats one of the addresses of google.com

It says: 
connect: Network is unreachable

---

### Post by petri on 2006-09-14
And all the cables are connected? Switch cables between the machines.

---

### Post by blunt1 on 2006-09-14
> **petri said:**
> And all the cables are connected? Switch cables between the machines.

yes

---

### Post by blunt1 on 2006-09-14
> **Najand said:**
> Is it possible to send the output here?

Whats the best/quickest way to do this without typing it all out?!

---

### Post by rccharles on 2006-09-14
> **blunt1 said:**
> I have done this... is there anything I should look for in particular?

You want to see if you have your ethernet card configured.  Like...
robert:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:FF:A5:13:1C  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:ffff:fea5:131c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:986 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:108534 (105.9 KiB)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:286 errors:0 dropped:0 overruns:0 frame:0
          TX packets:286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20266 (19.7 KiB)  TX bytes:20266 (19.7 KiB)

The first 'paragraph' is eth0.  It is a lan card. Notice that I have a network address of 192.168.1.3 and recieved 986 packets.

Try some more ping commands to narrow down where things are failing.  

ping -c3 198.182.196.56
ping -c3 [www.linux.org](www.linux.org)

The 198.182.196.56 is [www.linux.org](www.linux.org).

Try pinging your windows box.  In windows, you can get a command line  (maybe under accessories ).  Do an 
ipconfig
to get the ip address.  

ping your linux box
ping 192.168.1.3
for example.


ping your windows box from linux
if you do not type in -c3, use control c to stop.

I assume you have a cable connection.  Swap cables.  

Robert#-o

---

### Post by xpod on 2006-09-14
> Whats the best/quickest way to do this without typing it all out?!

Right click in the terminal after you have listed "ifconfig" and "select all"

then you can either right click again to copy if you only have 2 mouse buttons or you can use you middle mouse button to paste at once without having to right click then paste

EDIT:..In fact you might still need to drag your mouse to highlight it all..
dont seem to be a "select all" option...just as simple though to drag your curser from top corner to bottom

---

### Post by blunt1 on 2006-09-14
> **rccharles said:**
> You want to see if you have your ethernet card configured.  Like...
robert:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:FF:A5:13:1C  
          [COLOR="Red"]**inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0**[/COLOR]
          inet6 addr: fe80::203:ffff:fea5:131c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:986 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:108534 (105.9 KiB)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:286 errors:0 dropped:0 overruns:0 frame:0
          TX packets:286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20266 (19.7 KiB)  TX bytes:20266 (19.7 KiB)

The first 'paragraph' is eth0.  It is a lan card. Notice that I have a network address of 192.168.1.3 and recieved 986 packets.

Try some more ping commands to narrow down where things are failing.  

ping -c3 198.182.196.56
ping -c3 [www.linux.org](www.linux.org)

The 198.182.196.56 is [www.linux.org](www.linux.org).

Try pinging your windows box.  In windows, you can get a command line  (maybe under accessories ).  Do an 
ipconfig
to get the ip address.  

ping your linux box
ping 192.168.1.3
for example.


ping your windows box from linux
if you do not type in -c3, use control c to stop.

I assume you have a cable connection.  Swap cables.  

Robert#-o


I dont have the bit i have coloured red in the above quote. Everthing else looks the same!

The ping command to an IP (198.182.196.56) comes back with "connect: Network is unreachable" the same happens if i try to ping the windows pc
and to a url ([www.linux.com](www.linux.com)) "ping: unknown host www.linux.com"

i have swapped the cables over and the windows pc still connects instantly! :-k

---

### Post by blunt1 on 2006-09-14
> **xpod said:**
> Right click in the terminal after you have listed "ifconfig" and "select all"

then you can either right click again to copy if you only have 2 mouse buttons or you can use you middle mouse button to paste at once without having to right click then paste

EDIT:..In fact you might still need to drag your mouse to highlight it all..
dont seem to be a "select all" option...just as simple though to drag your curser from top corner to bottom

I am on a different pc, i should have explained properley! how would i copy the text from the linux pc to the widows pc? no floppy...

---

### Post by Najand on 2006-09-14
I think he cannot copy/paste the output here because he is notconnected to the internet from his Dapper. 
how to  do that? If he has a thumb memory he can do it easily... 
Use the command:
```

ifconfig > ~/IFCFG.txt

```
and then copying the IFCGF.txt to his memory and  then oopen it iin his other computer using  internet with...

---

### Post by teddycat24 on 2006-09-14
I have just recently loaded distro 6.06 i think anyway the one that is called dapper dan. as you can tell i have never worked w/ linux before. 
My situation is almost exactly the same with a few variations, but i did write down all that terminal jazz. I have linux running on the same comp, a macbook w/ the dual processers.

I believe that it could be a firewall/security issue with and maybe blunt 1 also, but that is only a intuitive reflex. anyway i am running linux under parellels, which is very quick w/ my box.

This is going to be a dumb quextion but i don't need any kind of cables do i? As i said i am a Mac user and very, very ignorant of linux. any help would really be appreciated. 

oh, i have cable modem and am using comcast as provider. right now i am in the local library running on wi fi as people love to say.BTW the mac does not use cards and when i did check networking on the ubuntu side it was activated just not get out or in. thank you for any input,
(all you experts pls have mercy)

teddycat24](*,) ](*,)

---

### Post by Najand on 2006-09-14
Hmm, is it a cable modem? Oh I think I have an idea... It happened to me a while ago, and I am not sure if it works in your case too.... 

Shutdown your computer (Linux computer).
Turn off your Modem
Stay waiting for 1 minute.
Turn on your modem.
Boot you computer again.

---

### Post by blunt1 on 2006-09-14
> **Najand said:**
> I think he cannot copy/paste the output here because he is notconnected to the internet from his Dapper. 
how to  do that? If he has a thumb memory he can do it easily... 
Use the command:
```

ifconfig > ~/IFCFG.txt

```
and then copying the IFCGF.txt to his memory and  then oopen it iin his other computer using  internet with...

Sorry to be a pain Najand, how do i copy the IFCGF.txt from the memory with the 'onine' pc?

---

### Post by blunt1 on 2006-09-14
> **Najand said:**
> Hmm, is it a cable modem? Oh I think I have an idea... It happened to me a while ago, and I am not sure if it works in your case too.... 

Shutdown your computer (Linux computer).
Turn off your Modem
Stay waiting for 1 minute.
Turn on your modem.
Boot you computer again.

Just tried this as you mentioned, still not able to go on the internet  :(

---

### Post by blunt1 on 2006-09-14
Does anone have any other suggestions?! Thanks all for your input so far, still stuggling though!

---

### Post by petri on 2006-09-14
So you have a cable modem and a switch. Do you have a router which has dhcp? If not, does your ISP provide you two IP addresses? If not then I think the first comp booted takes the IP addr. and the second one will not get any.

---

### Post by mikemac on 2006-09-14
I, myself am having the same problems.  Just switched to Ubuntu on my laptop (clean install, no MS involved.  The laptop has recognized my WIFI card (Belkin 7010), but won't seem to do anything with it. (No lights or anything).  It will not recognize my wired ethernet card at all.  Tried loading NetManager, but problems there, as well.

---

### Post by petri on 2006-09-14
Wifi-cards are sometimes like ghosts :D

For you it might be better if you do a **Search** with **Belkin 7010** and hopefully you will find a solution.

---

### Post by blunt1 on 2006-09-14
> **petri said:**
> So you have a cable modem and a switch. Do you have a router which has dhcp? If not, does your ISP provide you two IP addresses? If not then I think the first comp booted takes the IP addr. and the second one will not get any.

:D  My ISP doesnt provide two IP addresses!! I shutdown the ubuntu pc and router.
Then disconnected the WIn Xp pc from the router.
Restarted and it worked! Im posting this off the ubuntu pc now, thanks everyone for your help!! =D>

---

### Post by louistan3 on 2006-09-14
if your router has multiple ports for ethernet cables, doesnt that mean that it can give out dhcp ips? so maybe the problem isnt with the ISP but w/ the router? just a thought.. :)

---

### Post by chimerical_brio on 2006-09-14
So I too have been struggling with getting my internet to work. I have a little bit of a different problem from blunt1; my internet was working fine for a few months, and then it stopped all of a sudden. I didn't change anythign that I can think of, and I can connect to my router from my Ubuntu box, and succesfully ping my Windows computer (interestingly, the Windows computer can't connect to the Linux computer). There's an icon int he upper right hand corner that telles me there is no network connection, because no network devices could be found, even though eth0 is recognized and enabled. Help?

---

### Post by petri on 2006-09-15
I recommend you to start a new thread.

Then please tell us more about your hardware
- do you have a router/firewall? I don't mean a modem.
- do you use internet sharing in one pc?
- and more and more, maybe the output of **lspci** and **ifconfig** at your new thread

---

### Post by LookTJ on 2006-09-15
try resetting the router to its default settings

---

### Post by mikemac on 2006-09-15
I finally made it on.  I don't know if I went about it the *right* way, but I am now happily on the internet on my Ubuntu laptop.  My card was showing up as ath0.  I edited the file: etc/network/interfaces and remarked out the settings under auto ath0, and placed the same settings into auto wlan0.  The interfaces file wound up looking like this:

auto ath0
iface ath0 inet dhcp
wireless-essid ACTIONTEC
#wireless-essid actiontec
#wireless-key 6a 3d fc 2b ca

auto wlan0
iface wlan0 inet dhcp
wireless-essid actiontec
wireless-key 6a 3d fc 2b ca

I don't know if this particular "fix" will apply to anyone, but here it is anyway!=D>

---

