---
title: "Using wireless in Ubuntu 6.10"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by ubantunovice on 2006-11-12
A little over a year ago I tried Ubuntu Linux and gave up because I could not get it to connect to the internet. I just downloaded Ubuntu 6.10 to try again.   ](*,) 

I am using a Toshiba Satellite laptop M105-S3084 and am writing from Windows because I cannot yet connect in Linux. In Windows I connect through my home wireless network which uses a router with WPA encryption.  But, to keep things simple, I would like to first simply connect in Ubuntu without using any encryption which should be easy because when (in windows) I click on "View available Networks" I find I am surrounded by several neighbors unsecured wireless networks to which I can connect easily as a test.

How do I "View available Networks" when in Ubuntu to connect to these unsecured networks? When I click on the wireless connection on the top right panel it only says (from memory) etho:lo, even though I have enabled the wireless connection in the screen that showed a choice of wireless, wired and modem connections.

I've searched this forum and understand that it would be helpful to include in my message the results of Linux's ipconfig and ifconfig, but that is another problem: I can open a terminal and execute these commands when in Ubuntu, but - Catch-22 - how do I copy and paste the contents to a file that I can then access from within Windows so I can include them in a message sent from Windows? Windows cannot see the Linux text files and Linux cannot see the Windows files!

The built in wireless adapter on this laptop is an "Intel PRO/Wireless 3945ABG" network connection which I found out on the web is supposed to be supported within Ubuntu. So that should not be the problem.

Any help would be greatly appreciated.  Inability to reach the internet wirelessly is a killer for me in any OS. I absolutely need it.

Thank you.

---

### Post by Mrpelletier on 2006-11-12
You can connect by going to system admin networking and chose the network by clicking prefrences. or if it doesnt work go to apps and click add/remove and add Kwif manager witch sould work if not im not sure what will:confused:

---

### Post by nickpaton on 2006-11-12
> **ubantunovice said:**
> 
I've searched this forum and understand that it would be helpful to include in my message the results of Linux's ipconfig and ifconfig, but that is another problem: I can open a terminal and execute these commands when in Ubuntu, but - Catch-22 - how do I copy and paste the contents to a file that I can then access from within Windows so I can include them in a message sent from Windows? Windows cannot see the Linux text files and Linux cannot see the Windows files!

Way to do it would be to generate the file and copy into Open Office as a .doc.  Then copy onto a CD or a memory stick.
Boot up into windows, copy into Word, and then from there you should be able to post it.

Sorry I cannot answer the rest since I use Broadcome Wireless but good luck anyway.

---

### Post by ubantunovice on 2006-11-12
Thank you both for your advice and help.  I really appreciate it.  There is nothing likegetting caught in a catch-22 while being unfamiliar with the area in the first place.

I will boot back into Ubuntu and add kwif manager.  I will also paste the ifconfig and iwconfig data to a USB port (I hope Ubuntu will recognize it without my needing to do anything too complicated) and then post the results.

Once I can get onto the internet when in Linux, I will be better able to solve problems I am having in it.  Also when I finally get my Ubuntu book.

Thanks again.  :D

---

### Post by ubantunovice on 2006-11-12
OK  Here is what I got. 
....................

iwconfig output

eth1      unassociated  ESSID:"kHart"  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:85   Missed beacon:0
........................

ifconfig output

eth0      Link encap:Ethernet  HWaddr 00:16:D4:22:C2:CE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x2000 Memory:d0000000-d0020000 

eth1      Link encap:Ethernet  HWaddr 00:13:02:AB:32:8E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1247 errors:0 dropped:83 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 Memory:d0100000-d0100fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:230 errors:0 dropped:0 overruns:0 frame:0
          TX packets:230 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18092 (17.6 KiB)  TX bytes:18092 (17.6 KiB)

---

### Post by nickpaton on 2006-11-13
Thanks for that, but we are missing are the actual network hardware components, so please post the result of:

sudo lshw -C network

---

