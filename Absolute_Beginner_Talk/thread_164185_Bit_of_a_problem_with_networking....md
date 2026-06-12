---
title: "Bit of a problem with networking..."
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by Melhisedek on 2006-04-22
Hi mates,
just installed latest beta to my Dell Inspiron 8100. To my suprise nvidia driver was installed and configured perfectly! Great job!

Now I was thinking of downloading some programing tools and such as default install seem to lack them. And here comes the problem...

I can't get Internet to work. I used that "network manager" (right upper corner, next to date and clock) and set up "eth0" with my IP adress, Gateway, DNS servers and Submask (all the info I have). Activated it, but no go. Rebooted still no go. Network connector on my laptop is blinking so I guess it works (it works in Windows)

Probably some newb mistake, first of many ;)

---

### Post by uteck on 2006-04-22
Open a terminal and run 'ifconfig' and post the results back.

---

### Post by Melhisedek on 2006-04-22
Hmmm. I'm typing this of the laptop screen so it might not be 100% but I'll try..

eth0:

```
Link encap: Ethernet   HWaddr 00:20:E0:70:90:9E
inet addr: 82.182.xxx.xxx (rest of my IP) Bcast: 82.255.255.255 Mask: 255.0.0.0
UPBORADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 orverruns:0 frame:0
TX packets:0 errors:0 dropped:0 orverruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b)    TX bytes:0 (0.0 b)
```

than the other one is "lo" with inet addr:127.0.0.1 hope I didn't need to write that one down as well :)

Anyway this Bcast is a bit strange... no idea what it is or does. Mask should be 255.255.255.0 but I was fooling around and trying different stuff, so I changed it to 255.0.0.0 which is what program itself generated.

That would be it, hope it helps

---

### Post by Melhisedek on 2006-04-22
Well I've been trying to do some research and come up upon this thread:

[http://www.ubuntuforums.org/showthread.php?t=162137&highlight=broadcast](http://www.ubuntuforums.org/showthread.php?t=162137&highlight=broadcast)

guy, seem to have same problem as I do. Anyway he solves it with:

[I]
And, it was the 'sudo pppoeconf' followed by the 'pon dsl-provider' commands that did the trick. [/I]

I tried the same thing. Now pppoeconf thingie asked me if eth0 was my default network connection, I said yes. It than proceeded with 2 tests that kinda timed out. And in the last step it said that it couldn't connect/find (can't really remember) to my device, that I should check cablage or there was another instance of pppoeconf that was using the device.

After that I ran "pon dsl-provider" all I got was plenty of crap in console window and nothing else. I couldn't stop it with CTRL-C so I went with ALT-F4 :)

Tried pinging gateway, it time-outed. Pinged my own IP and all went well... Hope extra info helps.

P.S. I changed Mask to 255.255.255.0 and Bcast changed to 82.182.xxx(3numbers from my IP).255
RX and TX values changed after I did pinging...

---

### Post by uteck on 2006-04-22
A few more questions.
Just to clarify things, you do have DSL? If not, the pppoe stuff is useless.
Are you connecting the computer directly to the DSL modem, or do you have a router of some sort set up.
Have you tried setting eth0 to use DHCP?  
Did you have to enter the network info for windows or did it auto configure itself?
In windows start a commend shell (start->run, type 'cmd').  Then type "ipconfig" in the shell and compare that to what you got in linux.

---

### Post by Melhisedek on 2006-04-23
Ok... I have ADSL, and computer is connected directly to modem.

I haven't tried DHCP, will do that in a second... What is DHCP for BTW?

I had to enter network info in Windows, Control Panel->Network Connections->Local Area Connection->Internet Protocol (TCP/IP)

Well after running ipconfig things looks the same except for that Bcast thing, that I can't find in Windows...

Wish me luck :) Will be back with results in a zippy ;)

---

### Post by nalmeth on 2006-04-23
don't know if this can help you for sure, but it is a good guide to troubleshooting your internet, and may fill you in on some stuff:
[http://www.ubuntuforums.org/showthread.php?t=87643](http://www.ubuntuforums.org/showthread.php?t=87643)

---

### Post by Melhisedek on 2006-04-23
I've run it before and everything goes well untill pinging the gateway where it just stands there for 10 minutes...

Here comes the info:

cat /etc/network/interfaces  
gives

```

auto lo
iface lo inet loopback

iface eth0 inet static
address 82.182.xxx.xxx  (my IP)
netmask 255.255.255.0
gateway 82.182.xxx.1

auto eth0

iface dsl-provider inet ppp
provider dsl-provider


```

ifconfig eth0
gives

```

Link encap: Ethernet   HWaddr 00:20:E0:70:90:9E
inet addr: 82.182.xxx.xxx (rest of my IP) Bcast: 82.182.xxx.255 Mask: 255.255.255.0
inet6 addr: fe80::220;e0ff:fe70:909e/64 Scope:Link
UPBORADCAST MULTICAST MTU:1500 Metric:1
RX packets:31 errors:0 dropped:0 orverruns:0 frame:0
TX packets:1423 errors:0 dropped:0 orverruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1860 (1.8 b)    TX bytes:133890 (130.7 b)


```


and route -n 
gives

```

Kernel IP routing table
Destination    Gateway        Genmaks         Flags Metric Ref Use Iface
82.182.xxx.0  0.0.0.0          255.255.255.0 U       0       0   0     eth0
0.0.0.0         82.182.xxx.1  0.0.0.0           UG     0       0   0      eth0

```



and testing 
sudo mii-tool eth0

gave me 

```
eth0: negotiated 100baseTx-FD, link ok
```


That would be it... Starting to get a little worried here :/ 

Worst case scenario... I fail to set up network connection... Can I download bunch of repositories (or how do you spell them) and run them from DVD or extern disc? I want to install a few programs and start learning Linux :)

*edit*
few more things that might be helpful...
1. When I turn off computer, there is this list going on that gives "OK" after each line. There is one line saying "Reconfiguring Network xxxx (something)" and there is no OK after it... 

2. I didn't configure network settings during installation... I did it after the installation. When I first booted the Ubuntu.

---

### Post by uteck on 2006-04-23
Here is one more thread that might help;
[http://ubuntuforums.org/showthread.php?t=138](http://ubuntuforums.org/showthread.php?t=138)

I think the reconfiguring network line in the shutdown is if you were using dhcp.

---

### Post by uteck on 2006-04-23
I forget to mention that you you can download packages easily.  If you burn them to CD you can add them to your apt list from the terminal with  'sudo apt-cdrom add'  and then you can use adept to add the packages.

---

### Post by Melhisedek on 2006-04-25
Ok now, this is new.
After trying utecks ling again, sadly I couldn't get connection to work :( So I took my computer to work, where I know we have some funky network stuff (no static IPs)... Went there connected the laptop, changed settings to DHCP, changed FireFox settings to "Auto detect..." and voila. Everythings works fine and dandy. And not only that I downloaded stuff way faster than I ever did on Windows :) 117 Kbps vs 86Kbps

I did install all the updates and a few development proggies. So now I'm content for a while.

Anyway we can rule out that my hardware/cablage is malfunctioning, as it did work yesterday, almost out of the box :P Stupid as I am I forgot to check "ifconfig" to see how does it look like... :/

So only thing is software. Don't think it is the driver as network card works flawlessly. I think problem lies somewhere in settings... I mean IP/DNS/Gateway nr... Somewhere there I hope.

So anyone have some new ideas based on new info ? :)

Thank you for your time!

---

### Post by lxndr on 2006-04-25
[quote=Melhisedek]
[code]Link encap: Ethernet   HWaddr 00:20:E0:70:90:9E
inet addr: 82.182.xxx.xxx (rest of my IP) Bcast: 82.255.255.255 Mask: 255.0.0.0
[/quote]
 
Next time xxx-ing out your HWaddr is a good idea also, IP's easily change, MAC addressess don't (officially)

---

### Post by Melhisedek on 2006-04-25
I see, didn't know what it was for :)

---

