---
title: "Can't reach most WEB sites, Firefox times out"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by ldc_1 on 2006-08-28
Hello All

Over the last two weeks I built two Ubuntu boxes using the latest Dapper kit. Both machines worked well until about 2 days ago. Now Firefox will hardly reach a site, all the big sites like Google and Yahoo time out, I am able to get to some Ubuntu sites if I wait long enough. Sitting next to these two Ubuntu systems are Windows XP boxes, they can reach all these sites with little effort. I have been on the phone with my ISP, they don’t see any issues with DNS servers. I am using all stock DHCP settings and the systems did work great for several days. Also having issues with GAIM, it to was working great for a while.
Note if I use a physical address to get to sites, the internet is very fast and I get no errors.

Does anyone have any thoughts on where I should look? My ISP knows nothing about Linux, I have built 2 systems which worked, until now. I have no experience with Linux other then through the menus and I don’t know my way around them very well. 

I did run trace routes and all goes well until I hit one of my ISP routers, yet the same trace rout from the windows box has no issues. 

Is there a firewall on the Ubuntu systems that might have gone nuts? I think it strange that both systems started having the problem at the same time and both had run great for days prior.

Any Help would be appreciated
-ldc-

---

### Post by funchords on 2006-08-28
1.  In a terminal, please use the command **top -b -n 1** and copy in the first 10 lines or so.  I'm looking for a process that is hogging the CPU and giving you poor performance.

2.  Please visit [http://www.dslreports.com/tweaks](http://www.dslreports.com/tweaks) and take the Tweak test using one of your Windows boxes and one of your Linux boxes.  The test results will give you a URL that you can copy and paste here.  This will allow us to compare the different configurations.  It's very cryptic.

3.  What kind of internet service do you have?  Cable, DSL, WISP, Satellite?  

Thanks

---

### Post by ldc_1 on 2006-08-29
Hello, so far I have these two items. 
1. The infor from the terminal window on one of my Linux boxes.

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4266 root      15   0 57620  15m 8232 S  3.9  4.2  60:57.82 Xorg
 4991 larry     17   0 38268  11m 7892 S  3.9  3.1  20:24.37
gnome-nettool
10111 larry     15   0  2192  980  756 R  2.0  0.3   0:00.01 top
    1 root      16   0  1564  528  460 S  0.0  0.1   0:02.56 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.09 events/0
    5 root      11  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0
    9 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  109 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  110 root      15   0     0    0    0 S  0.0  0.0   0:00.04 pdflush

2. the network test from the XP box, still trying to get one for the Linux box.
[http://www.dslreports.com/tweakr/block:42c6743?service=dsl&speed=&os=winXP&via=normal]("http://www.dslreports.com/tweakr/block:42c6743?service=dsl&speed=&os=winXP&via=normal")

I am trying to gather the rest of the information at this time. Thank you so much for the help.
-ldc-

---

### Post by ldc_1 on 2006-08-29
Hello Again
I am running DSL, forgot to mention that. I can't get Java loaded on the Linux box, I did download the needed file to my windows box, shared the drive to the Linux box. Can't seem to install the file.

Here is a screen capture of a trace route form the Linux box.

The Linux system is so slow getting to WEB pages that getting anything done is almost impossible.

Keep the thoughts coming, all I can say is I will try.

-ldc-

---

### Post by funchords on 2006-08-29
Nothing looks alarming, but there are about 5 lines above the "PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND" that I'd like to see, too.  

Can you re-run it and give me those lines?

---

### Post by funchords on 2006-08-29
What else do these two boxes have in common?  Do they share the same router/bridge/switch?  If so, can you unplug that and plug it back in?

Also, try this command:

less /var/log/dpkg.log

When it loads, press the "End" key to jump to the end of the log.  Now scroll up the log to see what you've installed since this started action bad.  Perhaps you can identify a suspicious package or two that you might want to try to reverse.

---

### Post by ldc_1 on 2006-08-30
Hello

My network is setup like this.
- Actiontec DSL gate way router, wireles box.
- 3 feet CAT5E to a 24 port Procurve 2724 switch which feeds the house.
- Cat5E running around the house.
- In my office (about 30 feet from switch above) is a Procurve 408 8 port switch with 2 Windows and one unbunto system off it.
- The other ubunto is in my dughters room, about 80 feet of cat5E straight of the 24 port switch, she also has a Windows system in the room off a secound wire.
- We also have a Dlink hub in our living room with one Windows box and a wirless AP unit hung off it.

All of the above network gear has been in place for a year or more. We have two wirless PC that are used around the house by kids/wife. All windows boxes continue to work fine, wirles or cable, only the to ununtu boxes are having issues. Which is really to bad because the kids were getting interested in using them.

My daughters unbunto system has had only evoltion mail and gaim setup on it, the only other updates were from the system update tool.

My unbunto system has had Skype, Evolution mail and Gaim setup, along with the system updates.

NOTE, we can no longer do the system updates, nodes keep timing out. Was having the same problem trying to load Java which was needed to run Tweak.

As I mentioned both systems worked great for a while, now we can't do much with them. I might try rebuilding my daughters Thursday night to see if the problem goes away.

Thanks again for your help. Here are the logs you requested.

-ldc-

Output from less /var/log/dpkg.log

2006-08-23 22:31:25 status unpacked xserver-xorg-core
1:1.0.2-0ubuntu10.4
2006-08-23 22:31:25 status unpacked libmagick9 6:6.2.4.5-0.6ubuntu0.1
2006-08-23 22:31:25 status half-configured libmagick9
6:6.2.4.5-0.6ubuntu0.1
2006-08-23 22:31:28 status installed libmagick9 6:6.2.4.5-0.6ubuntu0.1
2006-08-23 22:31:29 status unpacked xserver-xorg-core
1:1.0.2-0ubuntu10.4
2006-08-23 22:31:29 status half-configured xserver-xorg-core
1:1.0.2-0ubuntu10.42006-08-23 22:31:29 status installed
xserver-xorg-core 1:1.0.2-0ubuntu10.4
2006-08-26 09:52:42 install libqt3-mt <none> 3:3.3.6-1ubuntu6
2006-08-26 09:52:42 status half-installed libqt3-mt 3:3.3.6-1ubuntu6
2006-08-26 09:52:43 status unpacked libqt3-mt 3:3.3.6-1ubuntu6
2006-08-26 09:52:43 status unpacked libqt3-mt 3:3.3.6-1ubuntu6
2006-08-26 09:52:44 status unpacked libqt3-mt 3:3.3.6-1ubuntu6
2006-08-26 09:52:44 status unpacked libqt3-mt 3:3.3.6-1ubuntu6
2006-08-26 09:52:44 status half-configured libqt3-mt 3:3.3.6-1ubuntu6
2006-08-26 09:52:47 status installed libqt3-mt 3:3.3.6-1ubuntu6
2006-08-26 09:52:49 install skype <none> 1.3.0.37-1
2006-08-26 09:52:49 status half-installed skype 1.3.0.37-1
2006-08-26 09:52:51 status unpacked skype 1.3.0.37-1
2006-08-26 09:52:51 status unpacked skype 1.3.0.37-1
2006-08-26 09:52:51 status unpacked skype 1.3.0.37-1
2006-08-26 09:52:51 status unpacked skype 1.3.0.37-1
2006-08-26 09:52:51 status half-configured skype 1.3.0.37-1
2006-08-26 09:52:51 status installed skype 1.3.0.37-1
(END)
------------------------------------------------------------------------------

Output from Top -b-n 1

top - 22:45:04 up 1 day, 0 min,  2 users,  load average: 0.07, 0.10,
0.08
Tasks:  80 total,   1 running,  79 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.7% us,  0.2% sy,  0.1% ni, 97.1% id,  0.0% wa,  0.0% hi,
0.0% si
Mem:    386212k total,   382800k used,     3412k free,   126324k buffers
Swap:   835340k total,        0k used,   835340k free,   111636k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 9349 larry     15   0  2188  980  756 R  2.0  0.3   0:00.01 top
    1 root      16   0  1568  528  460 S  0.0  0.1   0:02.61 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.07 events/0
    5 root      11  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.03 kblockd/0
    9 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  109 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  110 root      15   0     0    0    0 S  0.0  0.0   0:00.01 pdflush
  112 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  111 root      15   0     0    0    0 S  0.0  0.0   0:00.05 kswapd0
  699 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod
 1826 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1902 root      15   0     0    0    0 S  0.0  0.0   0:00.05 kjournald
 2128 root      16  -4  2424  912  368 S  0.0  0.2   0:00.68 udevd
 2915 root      20   0     0    0    0 S  0.0  0.0   0:00.00
shpchpd_event
 3328 dhcp      14  -2  2332  796  492 S  0.0  0.2   0:00.01 dhclient3
 3797 root      16   0  2152 1192  644 S  0.0  0.3   0:00.00 acpid
 3916 root      16   0  1680  496  412 S  0.0  0.1   0:00.03 dd
 3918 klog      18   0  2420 1348  388 S  0.0  0.3   0:00.13 klogd
 4237 root      15   0 10904 1796 1220 S  0.0  0.5   0:00.00 gdm
 4243 root      15   0 11256 2548 1912 S  0.0  0.7   0:00.04 gdm
 4268 root      15   0 57640  17m 7920 S  0.0  4.5  33:14.86 Xorg
 4280 hplip     16   0 12868  920  696 S  0.0  0.2   0:00.00 hpiod
 4284 hplip     15   0  9404 4672 1092 S  0.0  1.2   0:00.15 python
 4356 messageb  16   0  2188  856  672 S  0.0  0.2   0:00.13 dbus-daemon
 4371 haldaemo  16   0  6732 5328 1556 S  0.0  1.4   0:02.01 hald
 4372 root      16   0  2720  972  836 S  0.0  0.3   0:00.05 hald-runner
 4383 haldaemo  17   0  2004  792  696 S  0.0  0.2   0:00.00
hald-addon-acpi
 4433 haldaemo  15   0  2004  792  692 S  0.0  0.2   0:00.00
hald-addon-keyb
 4444 haldaemo  16   0  2004  816  716 S  0.0  0.2   0:00.34
hald-addon-stor
 4445 haldaemo  16   0  2008  816  716 S  0.0  0.2   0:00.27
hald-addon-stor
 4525 root      18   0  1968  704  616 S  0.0  0.2   0:00.00 hcid
 4531 root      19   0  1616  452  384 S  0.0  0.1   0:00.00 sdpd
 4543 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd
 4558 root      16   0  1628  296  232 S  0.0  0.1   0:00.00 mdadm
 4593 daemon    16   0  1800  396  296 S  0.0  0.1   0:00.00 atd
 4606 root      16   0  2120  844  684 S  0.0  0.2   0:00.01 cron
 4678 root      16   0  1564  496  424 S  0.0  0.1   0:00.00 getty
 4679 root      16   0  1564  496  424 S  0.0  0.1   0:00.00 getty
 4680 root      16   0  1564  496  424 S  0.0  0.1   0:00.00 getty
 4681 root      16   0  1560  492  424 S  0.0  0.1   0:00.00 getty
 4682 root      16   0  1560  492  424 S  0.0  0.1   0:00.00 getty
 4683 root      16   0  1564  496  424 S  0.0  0.1   0:00.00 getty
 4694 larry     16   0 19480 9.8m 7272 S  0.0  2.6   0:00.78
x-session-manag
 4736 larry     16   0  4328  688  444 S  0.0  0.2   0:00.01 ssh-agent
 4739 larry     16   0  2712  644  520 S  0.0  0.2   0:00.00 dbus-launch
 4740 larry     16   0  2188  920  768 S  0.0  0.2   0:00.03 dbus-daemon
 4742 larry     15   0  6060 3668 1808 S  0.0  0.9   0:00.90 gconfd-2
 4745 larry     18   0  2336  728  532 S  0.0  0.2   0:00.00
gnome-keyring-d
 4747 larry     17   0  6260 2952 2232 S  0.0  0.8   0:00.22
bonobo-activati
 4749 larry     15   0 27168 8972 6952 S  0.0  2.3   0:01.17
gnome-settings-
 4751 larry     16   0  5804 4328 1228 S  0.0  1.1   0:00.31 esd
 4761 larry     16   0 15268 9152 6436 S  0.0  2.4   0:06.37 metacity
 4766 larry     15   0 35912  14m  10m S  0.0  3.9   0:04.40 gnome-panel
 4768 larry     15   0 65872  13m  10m S  0.0  3.5   0:02.39 nautilus
 4773 larry     16   0 17116 5264 3948 S  0.0  1.4   0:00.14
gnome-volume-ma
 4779 larry     15   0 19052  10m 7628 S  0.0  2.7   0:01.11
update-notifier
 4782 larry     15   0  8484 3788 2984 S  0.0  1.0   0:00.36
gnome-vfs-daemo
 4786 larry     15   0 39676 8332 6520 S  0.0  2.2   0:00.57 trashapplet
 4789 larry     16   0 55220 7976 6368 S  0.0  2.1   2:44.97
gnome-cups-icon
 4808 larry     15   0 17712 5508 4008 S  0.0  1.4   0:00.66
gnome-power-man
 4810 larry     16   0  2284  800  700 S  0.0  0.2   0:00.02
mapping-daemon
 4812 larry     15   0 33856  10m 8064 S  0.0  2.9   0:01.28
mixer_applet2
 4814 larry     16   0 23172  10m 7680 S  0.0  2.7   0:01.32
clock-applet
 4837 larry     16   0 14820 5164 4004 S  0.0  1.3   0:01.19
gnome-screensav
 4847 larry     16   0 29036 9696 6336 S  0.0  2.5   0:01.22 gksu
 4848 root      15   0 83640  43m  17m S  0.0 11.7   0:11.38
update-manager
 4862 root      16   0  5920 3464 1784 S  0.0  0.9   0:00.57 gconfd-2
30543 cupsys    26  10  4344 2024 1436 S  0.0  0.5   1:11.52 cupsd
30628 syslog    26  10  1768  712  584 S  0.0  0.2   0:00.01 syslogd
 8784 larry     15   0  130m  28m  18m S  0.0  7.5   0:09.58 evolution
 8790 larry     16   0 65232 6700 5184 S  0.0  1.7   0:00.20
evolution-data-
 8793 larry     16   0 34232 9304 7512 S  0.0  2.4   0:00.45
evolution-excha
 8801 larry     16   0 57676 9864 7988 S  0.0  2.6   0:00.38
evolution-alarm
 9317 larry     15   0 39872  13m 9008 S  0.0  3.7   0:00.87
gnome-terminal
 9318 larry     20   0  2280  680  580 S  0.0  0.2   0:00.00
gnome-pty-helpe
 9319 larry     16   0  5564 3248 1360 S  0.0  0.8   0:00.32 bash

larry@Dads-Ubuntu:~$
------------------------------------------------------------------------------

---

### Post by funchords on 2006-08-31
The readouts don't show anything particularly sucking resources.  

Let's try this:

**sudo ifconfig eth0 mtu 1450**

Test again, without rebooting.

If that helps, it's because your DSL connection encapsulates the Ethernet packets, which are 1500 bytes by default.  So we reduce the size of the Ethernet packet to 1450, so it can be encapsulated without fragmenting.

This could explain why the larger sites have problems -- particularly sites that have a SSL-login like Yahoo or Google.

If that helps, you can add that command to execute whenever the card comes up (without the sudo prefix, but add a pre-up or up prefix) to /etc/network/interfaces ... so it will look like this:

.
.
.
auto eth0
iface eth0 inet dhcp
pre-up ifconfig eth0 mtu 1450
.
.
.

---

### Post by Viral on 2006-08-31
Hello! I had a similar problem, and suprisingly, I have almost the exact same setup as you, with Actiontech.

There is a simple solution:

On linux, type: about:config (in the address bar) on Firefox Web Browser.

Now, search for an entry name with DNS in it....

I'll edit this when I find the entry, but when I post the entry, you'll click it twice to have it set to "ENABLE".

Be right back...

EDIT, search DNS, and select one that looks like this:

network.dns.disableIPv6

Now, double click it to True, and then reboot and visit any webpage.


Post and see if it works!

---

### Post by Carbonfish on 2006-08-31
ldc_1

I have a question that probably won't be helpful, but I am curious and will ask it anyway. Have you tried any browser other than Firefox? I experienced a similar problem (with significantly different hardware), and tried quite a few fixes before, mostly out of frustration, I tried a different browser (Swiftfox) and was able to load pages. While I am sure that this wasn't the root of the problem, it was good to eliminate it from the troubleshooting loop.

Just curious,

KC

---

### Post by furiousV on 2006-08-31
The problem is that Firefox tries to make an IPv6 connection, but we all rely on IPv4 still.

As Viral said, fire up Firefox, go to **about:config**

Filter out **ipv6**

Double-click the **network.dns.disableIPv6** value to switch it to **true**

Enjoy browsing once more

I had this problem with my friends running Ubuntu on their laptop, and I had this problem when I first installed SUSE a while back.

Carbonfish, when I had the problem, it was only firefox. Konqueror worked fine.

---

### Post by Carbonfish on 2006-08-31
> **furiousV said:**
> 

Carbonfish, when I had the problem, it was only firefox. Konqueror worked fine.

furiousV,

Yes. This is the point that I was gently trying to make.

KC

---

### Post by ChuckNH on 2006-08-31
So glad to see this post! Same problem here (I'm viewing on XP) and with Firefox and Actiontec DSL gateway, ironically.  Before I tackle the cure, which will be later today, will there be an additional fix required for Thunderbird, or are we looking at the same filter necessary? My email is also timing out, so is it the same problem creating that? 

Thanks for the help, in advance.  I want to continue my happy Ubuntu ways.......

---

### Post by ldc_1 on 2006-08-31
Hello All

I have done the following tonight. Just to be sure my network had no problems I shutdown and rebooted DSL modem and the primary house switch yet again. For whatever reason I was able to get Firefox to reach a few pages, very slowly. I next tried the "sudo ifconfig eth0 mtu 1450"
That really did seem to help, I was able to run gaim, evolution, skype and firfox after the mtu change. I also added the code in so the command will be set on re-boot in the future. 

I have also tried the suggestion made concerning "network.dns.disableIPvt", it is now set to true, have not rebooted as I am doing a file download so I do not know if that helped or not.

I have only used Firefox for browsing, never tried another product on these two boxes. Truly we wanted to use Firfox as we have been using it on the Windows machines and like it.

What is the trick to drag and drop files from one folder to another when the folders are system folders? I downloaded a file to my desktop and needed it in a system folder, although I could do a copy, I was never allowed to paste it as I did not have privs. 

Thank you all for your help, it is really appreciated.

-ldc-

---

### Post by ldc_1 on 2006-08-31
Hello

Thank you, I believe that the solution below got me back on-line again. I have finally be able to get to pages and download things like Java.

Really appreciate the help.

-ldc-


> **funchords said:**
> The readouts don't show anything particularly sucking resources.  

Let's try this:

**sudo ifconfig eth0 mtu 1450**

Test again, without rebooting.

If that helps, it's because your DSL connection encapsulates the Ethernet packets, which are 1500 bytes by default.  So we reduce the size of the Ethernet packet to 1450, so it can be encapsulated without fragmenting.

This could explain why the larger sites have problems -- particularly sites that have a SSL-login like Yahoo or Google.

If that helps, you can add that command to execute whenever the card comes up (without the sudo prefix, but add a pre-up or up prefix) to /etc/network/interfaces ... so it will look like this:

.
.
.
auto eth0
iface eth0 inet dhcp
pre-up ifconfig eth0 mtu 1450
.
.
.

---

### Post by ldc_1 on 2006-08-31
Thank you, this to had a positive outcome, after I added your change and rebooted my trips to WEB sites seemed to improve. Between the MTU change and this one the spead to WEB pages has really improved.

Thanks again for your help,

-ldc-

---

### Post by funchords on 2006-09-01
Glad to have helped!

---

### Post by dhubbard on 2006-09-04
Two things:

1) For the person who asked about Thunderbird.
[INDENT]If you go into Edit, Preferences, click on Advanced, Config Editor. Follow the directions from before (type in network.dns.disableIPv6, and change it to False), then restart TB.[/INDENT]
2) I use an Action Tech DSL router, with wireless. Sometimes I don't have a problem with getting FF or TB to connect, but other times I do. The problems seem to start and stop if I restart the router. I have been dealing with this for a while, and haven't been able to figure out the solution. Does anyone know why sometimes it will work but other times it will not? :confused: 

Make that three things, thank you for the solution to this!! :D

---

### Post by ChuckNH on 2006-09-04
> **funchords said:**
> The readouts don't show anything particularly sucking resources.  

Let's try this:

**sudo ifconfig eth0 mtu 1450**

Test again, without rebooting.

If that helps, it's because your DSL connection encapsulates the Ethernet packets, which are 1500 bytes by default.  So we reduce the size of the Ethernet packet to 1450, so it can be encapsulated without fragmenting.

This could explain why the larger sites have problems -- particularly sites that have a SSL-login like Yahoo or Google.

If that helps, you can add that command to execute whenever the card comes up (without the sudo prefix, but add a pre-up or up prefix) to /etc/network/interfaces ... so it will look like this:

.
.
.
auto eth0
iface eth0 inet dhcp
pre-up ifconfig eth0 mtu 1450
.
.
.


Just checking - so do you mean to add the above lines at the head of the file, or replace it with the above?  Thanks.

---

### Post by Azure on 2007-11-29
Relatively new Ubuntu user.

I had the same problem on my daughter's laptop. Just built with version 7.10 and Firefox couldn't get to Hotmail.com unless you hit the "Retry" button many, many, times. I can certainly live without Hotmail, but she can't and it is a deal breaker in terms of her using an Ubuntu desktop.

Changed the "network.dns.disableIPv6" to True, via the "about:config" and it worked perfectly

---

