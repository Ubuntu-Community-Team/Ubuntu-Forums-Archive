---
title: "Why 7.10 giving so many problems? :("
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by madu on 2007-10-30
Hey guys..

I recently upgraded to 7.10 from 7.04.. a big mistake when I was doing very well with Fiesty Fawn..
I have had nothing but trouble since I upgraded to Gusty...
Anyway, I have Lenovo T60 and I had a miserable video driver problem once I started 7.10... and somehow got it resloved to work.. and now its my network... seems the ethernet interface is going up and down very often.. although no problem with the wireless... I cant figure out why.. seems its a DNS unreachable problem since I can remote connect to desktop (direct connection from a switch)...
I almost wiped out this and went to install 7.04 but the 7.04 installer DIDNT SEE MY PARTITIONS.. I  have 2 more partions (recovery and XP) and I dont want to wipe them off... I'm starting to think its this Gusty thats making the installer not see my partitions (it only sees the entire hdd)... it is the same cd I used to install my 7.04 before so I know its working properly...

Please guys... any help here would be appreciated... why is 7.10 giving such problems.. why cant it get simple things right which was working fine with 7.04..??? and I'm yet to experience anything but trouble from this upgrade...also I started to experience apps getting stuck.. which I hardly experienced with 7.04 and also with any Linux...  any help to even go back to 7.04 would be greatly appreciated..

Thanks million guys...

Madu...

---

### Post by juantovarm on 2007-10-30
what you could do is eliminate your linux partition using the windows installer disk (i recommend you format it to fat32), you'll end up with 2 partitions, from here you could:
a: use an app like partition magic and resize your windows partition as to absorb the other one (this is only possible if both partitions have the same kind of format -fat32 or ntfs-), and then, once that is finished, install feisty normally,
b:install feisty in that fat32 partition you created

Personally i would go with option B, it has fewer steps


hope that helps :)

juan

---

### Post by madu on 2007-10-30
Thanks bro...
How about formatting the Linux partition from Windows and install Fiesty afterwards...? would it have any consequences like from Grub booting?

---

### Post by juantovarm on 2007-10-31
tried that a coupe of times with dapper and got the same result on different machines:

grub
grub

and that's all the pc's would say, total ruin... when i killed the linux partition from the windows install cd, did it maybe 6 or 7 times, no problems whatsoever :guitar:

---

### Post by mikewhatever on 2007-10-31
You don't seem to have any trouble reinstalling. So what, if Feisty does not see XP and its recovery partitions, you are not going to install there anyway. Write down your linux partitions (root, swap, home if there is a separate one) names, during the installation, choose manual partitioning, edit mount point for the linux ones (/,swap,/home) and format root. Then proceed with the installation.

Important: Do not format other partitions. All data on the partition formatted will be lost. Backup everything really important.

If you do not know the names of your partitions, post the output of > sudo fdisk -l

---

### Post by HermanAB on 2007-10-31
Well, if you are having more than about two serious problems, then it is better to look around for a different distribution.  Each distro tests with a zoo of computers in their lab, but nobody has every piece of kit ever made on the planet.  So shop around, try Mandriva 2008.  It is all the same underneath anyway.

---

### Post by madu on 2007-10-31
> **mikewhatever said:**
> You don't seem to have any trouble reinstalling. So what, if Feisty does not see XP and its recovery partitions, you are not going to install there anyway. Write down your linux partitions (root, swap, home if there is a separate one) names, during the installation, choose manual partitioning, edit mount point for the linux ones (/,swap,/home) and format root. Then proceed with the installation.

Important: Do not format other partitions. All data on the partition formatted will be lost. Backup everything really important.

If you do not know the names of your partitions, post the output of


Thanks for the replies guys..
heres the fdisk output:

>   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         668     5360640   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         669        2603    15535800    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            2603        6250    29295000   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4            6250       14593    67019400    f  W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/sda5   ?        6250      273599  2147483647+  ff  BBT
/dev/sda6            6493       10317    30716248+   7  HPFS/NTFS
/dev/sda7           10317       12229    15361888+   7  HPFS/NTFS
 

The problem is when I got to manual install all it gives me is** /dev/sda**.
And all I can do is to make new partitions.. I know I'm supposed to see the remaining partitions in the manual install but for some strange reason it sees the whole hdd as a single partition... and the only thing I can do is to partition the hdd which will eventually swipe off my XP and recovery partitions...

DO anybody know how to view a log file or something of the ether interface..?
My internet works fine and in the next minute its down.. cant resolve the addresses.. cant even ping my dns's...  but the wireless works fine...

thanks for the input guys...

---

### Post by mikewhatever on 2007-10-31
It looks like the errors such as 'Partition 1 does not end on cylinder boundary.' are responsible for the partitioning issues. Hope someone knows how to fix it.

---

### Post by madu on 2007-10-31
> **mikewhatever said:**
> It looks like the errors such as 'Partition 1 does not end on cylinder boundary.' are responsible for the partitioning issues. Hope someone knows how to fix it.

Oh... thats just great :confused:
I have no idea to fix that.. also I get "Logical I/O error in sda5..." before Ubuntu loads up.. I guess that explains the "?" in sda5... damn... I didnt get anything like this before the upgrade... :(

---

### Post by daengbo on 2007-10-31
As far as I know, there are no filesystems supported in Gutsy that aren't supported in Feisty, so all of your partitions should be seen either way. What filesystem is your Ubuntu system using? Have you checked the CD you used to upgrade to Gutsy for errors?

---

### Post by madu on 2007-10-31
> **daengbo said:**
> As far as I know, there are no filesystems supported in Gutsy that aren't supported in Feisty, so all of your partitions should be seen either way. What filesystem is your Ubuntu system using? Have you checked the CD you used to upgrade to Gutsy for errors?

I didnt use a cd to upgrade.. did it from Update manager...

---

### Post by madu on 2007-10-31
This is part of** ifconfig**:

> **br0**       Link encap:Ethernet  HWaddr 00:1A:6B:67:7D:30  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:6bff:fe67:7d30/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4890 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2781 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2421192 (2.3 MB)  TX bytes:607869 (593.6 KB)

**eth0**      Link encap:Ethernet  HWaddr 00:1A:6B:67:7D:30  
          inet6 addr: fe80::21a:6bff:fe67:7d30/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4920 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2785 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2512498 (2.3 MB)  TX bytes:620411 (605.8 KB)
          Base address:0x3000 Memory:ee000000-ee020000 
 

I'm not sure but would my link (probably dns resolving) going up and down has something to with using IPv6..? any ideas guys...?

---

### Post by Jaco Du Toit on 2007-10-31
Regarding the networking issues, I would just like to confirm that when you are in windows (on the same machine of course) the networking is working 100%? 

The reason I ask this is just to completely eliminate hardware related problems with your network connection. Also, when booted into ubuntu 7.10, do you experience packet loss? 
Test this by say flood pinging your router for 2-3 secs by issueing the command:
  ping -f 192.168.0.1
(Substitute 192.168.0.1 for your router address of course. Hit CTRL-C to abandon the ping, then it will print some statistics)

I am very much interested in this problem, as I am experiencing the same thing on my desktop machine at home running Ubuntu 7.10 AMD64 - but in my case I am almost certain that it is a semi-faulty network cable. 

What I found in my case to work (not a fix, but a work around) was to adjust the speed of my network connection to 10Mbps. This was done using the command 
  ethtool -s eth0 speed 10

Since in my case the connection works perfectly at 10Mbps I am inclined to think that I should fix my network cable - though I suppose it could still be related to software.

---

### Post by madu on 2007-10-31
> **Jaco Du Toit said:**
> Regarding the networking issues, I would just like to confirm that when you are in windows (on the same machine of course) the networking is working 100%? 

The reason I ask this is just to completely eliminate hardware related problems with your network connection. Also, when booted into ubuntu 7.10, do you experience packet loss? 
Test this by say flood pinging your router for 2-3 secs by issueing the command:
  ping -f 192.168.0.1
(Substitute 192.168.0.1 for your router address of course. Hit CTRL-C to abandon the ping, then it will print some statistics)

I am very much interested in this problem, as I am experiencing the same thing on my desktop machine at home running Ubuntu 7.10 AMD64 - but in my case I am almost certain that it is a semi-faulty network cable. 

What I found in my case to work (not a fix, but a work around) was to adjust the speed of my network connection to 10Mbps. This was done using the command 
  ethtool -s eth0 speed 10

Since in my case the connection works perfectly at 10Mbps I am inclined to think that I should fix my network cable - though I suppose it could still be related to software.

Yes.. Network works 100% in Windows...
The problem is, the ethernet works fine and a minute later it doesnt.. I cant ping even my gateway... then it automatically resolves... It cannot be a dns or dhcp server error because when I remote connect (tsclient) to my desktop (through a switch) it works fine and then freezes suddenly... and I cant even close the window.. I have to kill the processes... so it has to be the network cutting down.. really strange because the ethernet is the last thing I expected to have a problem...

I do not have the laptop with me now so I will try your suggestions tomorrow... thanks man... and I'm sure its not the cable becasue this happened to me with two cables... i'm starting to think gusty has serious problems.. gonna give up in a couple of days and go back to fiesty.. hopefully I can get the installer see my other partitions...

---

