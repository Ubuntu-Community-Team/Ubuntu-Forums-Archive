---
title: "Introduction, DSL Connectivity Question"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Justin86 on 2007-11-04
Hello all,

Here's a bunch of "introducing myself" junk, followed by my connectivity question.

I'm brand-spanking new to the Ubuntu community. I had an old laptop that I'd just reformatted, but I was still looking at 5 minute boot times and security issues, etc, the litany of problems that come with Windows. I decided to make the jump to Ubuntu just in time for the release of Gutsy Gibbon. Since I was looking at a fresh reformat as it was, and I store all my important documents online (backup via flash drive) anyway, I decided to dive in and make the switch. I'm loving the fast boot time, the particular software included (GIMP is a wonderful thing!), and the security included. I've taken baby steps learning my way around the terminal  (the various tutorials on the board are great), but I'm still very noob in that regard. Anyhow, ON TO THE QUESTION!

To recap: running Gutsy Gibbon on an Avertec 3200, 512 MB. I'm trying to get a wired connection up and running in Gutsy, but sudo ppoeconf doesn't seem to be doing the trick:

> js1986@lappy:~$ sudo pppoeconf
/usr/sbin/pppoeconf: 520: modconf: not found
/usr/sbin/pppoeconf: 520: modconf: not found
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: Cannot assign requested address

I'm not sure how to interpret this. Is Gutsy not recognizing my ethernet card?

For further background here's the output I got with ifconfig, iwconfig & lspci:

> js1986@lappy:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:45:18:CA:ED  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1233 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xd800 

eth0:avah Link encap:Ethernet  HWaddr 00:40:45:18:CA:ED  
          inet addr:169.254.8.220  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

js1986@lappy:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID: off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr: off   Fragment thr: off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0

js1986@lappy:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 20)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)


Again, this doesn't mean much to me, but I'm guessing the various "invalids" next to eth1 aren't a good sign. Any help would be greatly appreciated.

Thanks! I look forward to being an active, if green, part of the community here.

---

### Post by gate on 2007-11-04
I am not familiar with pppoeconf, but it appears to need the modconf program, which doesn't seem to be installed by default on my system, try this:

```

sudo apt-get install modconf

```

 then do pppoeconf


 Question: Why are you trying the command line version of getting networking up? Has Ubuntu not done that for you with the restricted drivers manager and the network manager?

---

### Post by Justin86 on 2007-11-04
Hi Gate, thanks for your reply.

> Question: Why are you trying the command line version of getting networking up? Has Ubuntu not done that for you with the restricted drivers manager and the network manager?

Indeed, Ubuntu has *not *automatically recognized my ethernet connection. I saw ppoeconf suggested as a Plan B of sorts, so I'm giving it a shot. I'll give your fix a try as soon as I get back to the laptop tonight, thanks again.

---

### Post by Justin86 on 2007-11-05
Hey guys,

Thanks again for the suggestion, gate, but I'm still stuck. Here's my output.

> 
js1986@lappy:~$ sudo apt-get install modconf
[sudo] password for js1986:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package modconf
js1986@lappy:~$ sudo pppoeconf
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: Cannot assign requested address


As I suggested above, I've enabled DHCP. Nothing happens. If I enable roaming the computer freezes. If I manually type in my IP address, it freezes.

Again, any help would be wonderful.

---

### Post by gate on 2007-11-05
That the system freezes makes me much more worried than the internet not working. If I come up with anything I will let you know.

---

### Post by gate on 2007-11-05
OK then, I just reread your posts and realized that I have not been paying attention properly :)

 I have a close wifi card to yours, and the restricted drivers manager picked it up on Gutsy on day one ( <3 Gutsy). So first thing I would do is double check system->administration->restricted drivers manager.

second, I found a thread where someone posted a similar problem, I only had time to read a few posts, but it looks like they had some solutions:
[http://www.debianhelp.org/node/4891](http://www.debianhelp.org/node/4891)

(if you don't know, Debian is the Linux distribution that Ubuntu is built on top of, so everything should be the same/similar)

---

### Post by lyndaj70 on 2007-11-05
> eth0:avah Link encap:Ethernet HWaddr 00:40:45:18:CA:ED 
inet addr:169.254.8.220 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:11 Base address:0xd800

According to this, your wired ethernet card is detected AND working... however it cannot locate a dchp server to get an ip address from....

How are you connecting?  Are you connecting straight to the dsl modem, or through a router?  How do you normally connect to go online?

If I am correct, if you connect to a router or modem with a functioning dchp server, you should be online....

PS.  the Inet address above of 169.254...  that is a marker that the card has given itself an ip address because it cannot locate a server.... 192.168... generally indicates a standard ip address....

~Lynda

---

### Post by Justin86 on 2007-11-06
Back again.

Gate:
> 
I have a close wifi card to yours, and the restricted drivers manager picked it up on Gutsy on day one ( <3 Gutsy). So first thing I would do is double check system->administration->restricted drivers manager.

I'll give that a try first thing tomorrow morning and see what I come up with. The thread you linked to did seem to be dealing with a similar problem, but to be honest I had difficulty understanding the solutions suggested. If your first suggestion doesn't work I'll give them a closer read tomorrow.

Lyndaj70:

> How are you connecting? Are you connecting straight to the dsl modem, or through a router? How do you normally connect to go online?

I'm connecting directly into a cable modem. I'm trying at my girlfriend's place and at my own, and while I do seem to get different output depending on whose place I'm at (?!), I can't get online either way. If I'm still having difficulty after taking a look at what Gate suggested, I'll post the 'different' output here tomorrow.

> If I am correct, if you connect to a router or modem with a functioning dchp server, you should be online....

That's certainly what the documentation suggests! *shrug* I'll keep working at it. I'm lucky enough to have a handful of internet access points, so I'm in no panicked rush to get the problem solved.

---

### Post by Justin86 on 2007-11-06
I took a look at my Restricted Drivers Manager. I tried to enable the disengaged driver ("Firmware for Broadcom 43xx Chipset Family"), but got the following error message:

[IMG]http://img66.imageshack.us/img66/1310/resctricteddrivererrorek8.png[/IMG]

A little research suggests that bcm43xx-fwcutter relates to my wireless connection, so I thought I'd toy with that and see what I ended up with. No dice. Just errors that said "file or directory did not exist." I found [this tutorial]("http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D185174&ei=57EwR7igAoO6gASk8ZWnBg&usg=AFQjCNFCa3sXvbsicUXTF0FEH0lv8XazCw&sig2=t77kVAIp9wwQgtVpfI0MwQ") on getting up a wireless connection, so I'll play with that a bit this afternoon, but it seems I'm no closer to getting my wired connection up.

Thanks again for the suggestions. Any other ideas?

---

### Post by Justin86 on 2007-11-07
Hello again,

Still nothing. It seems I've Googled everything there is to Google and I can't seem to find any tutorials to help me out in this regard. Any other suggestions, anyone?

Perhaps I should install Feisty instead? I'd rather not bother if it's a hardware issue, but if it comes to it I'll give it a try.

Thanks.

---

### Post by Maestro23 on 2007-11-07
> **Justin86 said:**
> Hello again,

Still nothing. It seems I've Googled everything there is to Google and I can't seem to find any tutorials to help me out in this regard. Any other suggestions, anyone?

Perhaps I should install Feisty instead? I'd rather not bother if it's a hardware issue, but if it comes to it I'll give it a try.

Thanks.

Have you seen this thread on Broadcom: [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

---

### Post by Justin86 on 2007-11-08
Hi Maestro,

I've printed out the thread and downloaded the appropriate drivers to my flash drive just to be on the safe side, but a quick question before I proceed with the instructions: will the HOWTO work for a *wired *connection, which is what I'm having trouble with here?

Thanks for the suggestion.

---

### Post by Justin86 on 2007-11-10
Hi again,

Still no dice. The commands there have me downloading some packages -- can't download if I can't connect!

I'm hurtin now, guys. Any new suggestions?

Thanks again to all.

---

### Post by Maestro23 on 2007-11-10
> **Justin86 said:**
> Hi again,

Still no dice. The commands there have me downloading some packages -- can't download if I can't connect!

I'm hurtin now, guys. Any new suggestions?

Thanks again to all.

I take it you're on your Windows machine?  You can go to Ubuntu Packages, download the packges you need (+ their dependencies), save to a CD, flash drive, etc...  Boot up Ubuntu and copy those files off the CD, drive, etc..

Ubuntu Packages: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Not a clean, easy solution, but it is a work-around in your situation.

---

### Post by Justin86 on 2007-11-10
> You can go to Ubuntu Packages, download the packges you need (+ their dependencies), save to a CD, flash drive, etc... Boot up Ubuntu and copy those files off the CD, drive, etc..

Now I feel silly. :oops:

I'll be doing that tonight, thanks.

---

