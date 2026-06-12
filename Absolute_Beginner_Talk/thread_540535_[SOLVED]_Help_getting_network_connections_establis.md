---
title: "[SOLVED] Help getting network connections established"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by vasocreta on 2007-09-01
Hi, I had no idea that this would be so difficult! But I am so tired of that other, more popular operating system, that I am determined. But it looks like I need some help.

Ok, so I installed Ubuntu 7.04 today and everything seemed to go off without a hitch. However, there are 2 things that I am not feeling good about:

1) I cannot access the Internet
2) I cannot login as 'root'. In fact I was never given the opportunity to set a password for root during install

As for the first problem, I am accessing through my onboard ethernet port and am not using wireless or a router.

Here is the output from iwconfig, ifconfig and lspci:

vasocreta@vasocreta:~$ iwconfig

lo        no wireless extensions.
eth0      no wireless extensions.

vasocreta@vasocreta:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:04:61:45:E5:4F
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:8747 errors:0 dropped:0 overruns:0 frame:0
         TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
         RX bytes:665160 (649.5 KiB)  TX bytes:7830 (7.6 KiB)
         Interrupt:16 Base address:0xc000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7880 (7.6 KiB)  TX bytes:7880 (7.6 KiB)

vasocreta@vasocreta:~$ lspci

00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation MCP2A ISA bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP2A SMBus (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation MCP2A USB Controller (rev a2)
00:04.0 Bridge: nVidia Corporation MCP2A Ethernet Controller (rev a3)
00:06.0 Multimedia audio controller: nVidia Corporation MCP2S AC'97 Audio Controller (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP2A PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation MCP2A IDE (rev a3)
00:0b.0 IDE interface: nVidia Corporation nForce2 Serial ATA Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:06.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
01:0d.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]
02:00.1 Display controller: ATI Technologies Inc RV515 [Radeon X1300] (Secondary)


I am not sure where to go from here. The other threads that I have searched did not help at all with this issue.

With regards to my second issue of not being able to log in as root, I am clueless. Remember I am a NOOB of the highest degree.

Thanks in advance for any help that you can give.

Matt

---

### Post by wormser on 2007-09-01
Ubuntu does not set up a root account during the install.  It uses **sudo** instead.  Put sudo infront of a command to get root privileges.  Here is a short [guide]("http://www.psychocats.net/ubuntu/graphicalsudo") on sudo and gksudo.  It is recommend to use sudo but you can log into root with **sudo -i**.

This looks like it is your ethernet card.

> Bridge: nVidia Corporation MCP2A Ethernet Controller (rev a3)

I took a quick google and a forum search but did not see anything promising.  Try to get more information on the card because this might be a hardware issue.

You can try envoking the DHCP client.

```
sudo dhclient
```

Also completely shut down and boot back up.  It is rare but some cards have trouble when you reboot from windows.  Sorry, I cannot help you more.

---

### Post by vasocreta on 2007-09-01
Thanks. I will look into each of your suggestions regarding my network card.  Also, thank you for clarifying how root works in ubuntu. I appreciate the help.

Edit: I have tried everything that I am capable of doing right now and I cannot get online. I find nothing that says that my adapter is incompatible, either. I am flustered!

Windows is looking like a happy place at this moment. Gosh...I can't believe I am saying that!!

---

### Post by vasocreta on 2007-09-03
Sweet Jesus in Heaven!!!

Ok, why didn't anyone tell that simply adding a router would get me connected!!!!

I can't quite remember my rationale because after all of the reading I have been doing over the last few days about the possible reasons for my not getting on the net; I am still a bit fuzzy in the head!

But the gist of it is this:
The computer was not obtaining an IP via my modem, so I figured that I would try to put a device in place that would simply assign an IP onto my machine. Hence the thought of trying a router.

Of course, I had spent the last few days figuring that there was something wrong with my network adapter. So, I disabled my onboard adapter via the BIOS configuration and installed a Network Card via a free PCI slot. I have no idea if this was necessary now, but I am not going back, as I am just so happy to have gotten this damn computer on the Internet.

So, here I am...alive and kicking. Windows just got a little further behind in the rearview mirror. Now let's see if I can burn some CDs, play DVDs, and get software installed.

Does anyone want to join in a verse of The Little Mermaid's, "A Whole New World"?

---

