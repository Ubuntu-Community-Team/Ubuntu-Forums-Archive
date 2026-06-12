---
title: "Wireless trouble"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Shron on 2008-01-22
Hi everybody,

I am newbie for Ubuntu. I also have trouble with the wireless access. I tried to google my problem and search in our forum. But I can't find an answer. Could you please help me?

Related information:

Lenovo ThinkPad R60e.
Ubuntu 7.10
Router: Netgear MR814V2

In windows xp, I use Key Index 3. I didn't find anywhere to input this in Ubuntu. I am so confused!

In my Restricted Driver Manager, there appears the 'Intel(R) PRO/Wireless 3945 Network Connection driver for Linux'.

Here is my terminal 'ifconfig' output:
eth0      Link encap:Ethernet  HWaddr 00:16:D3:2F:0B:EF  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe2f:bef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1526 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1441 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1385957 (1.3 MB)  TX bytes:210841 (205.8 KB)
          Interrupt:20 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:4B:35:BF  
          inet6 addr: fe80::218:deff:fe4b:35bf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:40 dropped:31435 overruns:0 frame:0
          TX packets:0 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12504 (12.2 KB)  TX bytes:28212 (27.5 KB)
          Interrupt:21 Base address:0xa000 Memory:edf00000-edf00fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:319 errors:0 dropped:0 overruns:0 frame:0
          TX packets:319 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24460 (23.8 KB)  TX bytes:24460 (23.8 KB)

Please Help me! Thanks a lot!

---

### Post by PeterJS on 2008-01-22
> **Shron said:**
> Hi everybody,

I am newbie for Ubuntu. I also have trouble with the wireless access. I tried to google my problem and search in our forum. But I can't find an answer. Could you please help me?

Related information:

Lenovo ThinkPad R60e.
Ubuntu 7.10
Router: Netgear MR814V2

In windows xp, I use Key Index 3. I didn't find anywhere to input this in Ubuntu. I am so confused!

 Is this with WEP or WPA? does your network show up in the network manager applet? What exactly is the error? And for wireless iwconfig is more useful the ifconfig usually.

---

### Post by spiderbatdad on 2008-01-22
[http://ubuntuforums.org/showthread.php?t=307659](http://ubuntuforums.org/showthread.php?t=307659)

sorry, PeterJS didn't see you there.

---

### Post by PeterJS on 2008-01-22
> **spiderbatdad said:**
> [http://ubuntuforums.org/showthread.php?t=307659](http://ubuntuforums.org/showthread.php?t=307659)

sorry, PeterJS didn't see you there.

Eh it happens, you had a ready answer, I had 50 questions.

+1 spiderbatdad.

---

### Post by Shron on 2008-01-22
Sorry I didn't say it clearly. It is WEP. I can see the Wireless Networks list. But I couldn't connect.

Here is my iwconfig output:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"BBQ"  
          Mode:Managed  Frequency=2.422 GHz  Access Point: 00:09:5B:B0:9D:0E   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:32876   Missed beacon:0

Thank you for help!



> **PeterJS said:**
> Is this with WEP or WPA? does your network show up in the network manager applet? What exactly is the error? And for wireless iwconfig is more useful the ifconfig usually.

---

### Post by spiderbatdad on 2008-01-22
i think you will need the wpa supplicant. there is a trick to setting the esid as well...sorry i dont know it...I think i've read it needs to be in quotes in some cases. Good luck...a little patience and I'm sure you'll get it going. It may need to be assigned by the ip...not BBQ

---

### Post by Shron on 2008-01-22
Thank you for your help, spiderbatdad. I am trying to look for it everywhere. I am just a newbie...

Could you please tell me a little bit more information on WPA supplicant? Perhaps I can find a thread to start...

Thanks!


> **spiderbatdad said:**
> i think you will need the wpa supplicant. there is a trick to setting the esid as well...sorry i dont know it...I think i've read it needs to be in quotes in some cases. Good luck...a little patience and I'm sure you'll get it going. It may need to be assigned by the ip...not BBQ

---

### Post by spiderbatdad on 2008-01-22
it's in synaptic package manager

---

### Post by Helven Ink on 2008-01-22
I can't install anything from the synaptic package manager...

---

### Post by Bubba64 on 2008-01-22
Have you checked under system administration update manger check for updates to see if everything is installed. Click on check after it opens to check there may be missing packages if you cannot get synaptic to work. also make sure you have access to repositories from software resources in administrative under systems. This doesn't answer your question per say but you may be short of updates or downloads.

---

### Post by Helven Ink on 2008-01-22
I can't get online... I can't check for updates or repositories, because I can't get online. I thought that's what this whole thread was trying to remedy?

---

### Post by Helven Ink on 2008-01-22
wait... I have WPA supplicant... it's just not doing me a whole lot of good I guess...

---

### Post by Jeezus on 2008-01-22
Hey Shron, This may sound silly, but have you tried manually configuring your wifi settings from the network configuration?
That's what I just did to get my wifi going, I unchecked roaming, entered in the essid, selected WEP key from the drop down menu and stuck the password in quotes. Then I set the config to Automatic DHCP.
I tried doing that a couple of times before it worked... I don't think it worked untill I put the password in quotes though.

---

