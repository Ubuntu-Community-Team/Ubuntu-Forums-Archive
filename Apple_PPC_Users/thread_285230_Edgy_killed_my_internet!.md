---
title: "Edgy killed my internet!"
date: 2006-10-26
forum: Apple PPC Users
---

### Post by goldenratiophi on 2006-10-26
I've been using Dapper for the past few days on my iMac G4 and today I decided to upgrade to Edgy.  So I used the upgrader to upgrade to Edgy, and then I rebooted and.... suddenly I don't have internet!  What do I do? :(

---

### Post by vixinu on 2006-10-26
How did you have wireless on Dapper:confused:?

---

### Post by agrionia on 2006-10-26
I've got the same problem with the 6.10 upgrade.   Machine is a G4 dual proc 1.42ghz "wind tunnel"  and my 6.06 upgrade to 6.10 caused my ethernet interface to not come up after the reboot.

I'm going to start looking into this soon, but for now, I'd recommend that others be cautious!...


> **goldenratiophi said:**
> I've been using Dapper for the past few days on my iMac G4 and today I decided to upgrade to Edgy.  So I used the upgrader to upgrade to Edgy, and then I rebooted and.... suddenly I don't have internet!  What do I do? :(

---

### Post by goldenratiophi on 2006-10-27
I tried to (re)start DHCP and it worked: "sudo dhclient".

I just need to make it do that on startup...

---

### Post by wcadrin on 2006-10-29
I had the same problem with my upgrade from Dapper to Edgy.  The wireless that I had working before no longer would get an IP address.  After doing some digging I discovered that the symlinks to the new kernel images weren't updated, they were still pointing to the old images.  After updating the links and rerunning ybin I rebooted and it was working again.

---

### Post by ricanelite on 2006-10-30
Well as for me, I have a Mac Mini which is a G4 processor, Running Edgy 6.10 and when the upgrade was done and I restarted my machine my internet connection was down as well, What i did was unplug the power to my router and cable modem, waited about a minutes and plugged in my router and cable modem, and then went to Settings>>>Networking and made sure I setup a Location as "Home" and then Made sure where it said Wired Connection I had it selected to "DHCP" or and made sure the port was eth0. Now if that was already selected from the beginning, I also made sure my Firefox Connection was set it "Direct connection to the internet" and now if that was already setup. I will go back to your Networking Configure under Settings again and just for fun click on Static IP and then click back on DHCP and unplug your router and cable modem wait about a minute and see what happens.

I know that might sound crazy but I did that with my Mac Mini and for some reason it worked.

So give that a shot and see what happens. Because honestly I don't remember entering no information or numbers to get my internet going. Because if I would have it would have been written down on a paper. So give that a shot. Wish you all good luck.

---

### Post by Mazmot on 2006-10-31
I had the same problem; upgraded from 6.06 to 6.10 and lost LAN connection after reboot. Actually it was much worse than reported above because while I humbled Network Manager, it crashed and I lost my tool to adjust my connections. The Network Manager was revived after I throw away configure settings (in the user folder as hidden files), and the connection came back after I set IP address manually. The real problem is that this situation happens again and again whenever I reboot the system. Every time I lost connection,somehow Network Manager crashes, and I must clean up settings. 

Oh, I forgot to mention that I have an old iBook: G3 500MHz.It worked pretty well when I used 6.06. I need help, at least some hint from someone who knows.

---

### Post by wcadrin on 2006-10-31
You could check to see if you had the same problem I did.

I first ran 'dpkg -l | grep linux-image'

This should give you a list of the kernel packages that are installed.  Find the one with the largest version number.  I'm not home so I can't remember exactly what version it was but I had two kernels installed; 2.6.15 and 2.6.17.

Next I checked the kernel image symlinks: 'ls -l / | grep vmlinuz'

This was where I found that vmlinuz was still symlinked to the 2.6.15 kernel image instead of the 2.6.17 image.  So I removed the symlinks that pointed to the old image

rm /vmlinuz /initrd.img

And relinked them to the new ones:

ln -s /boot/vmlinuz-2.6.17-10-ppc /vmlinuz
ln -s /boot/initrd.img-2.6.17-10-ppc /initrd.img
(I think.  Doing this from memory so I don't recall the exact file name)

I also went ahead and created the links for the old image just in case
ln -s /boot/vmlinuz-2.6.15-ppc /vmlinuz.old
ln -s /boot/initrd.img-2.6.15-ppc /initrd.img.old
(Again approximating the filenames)

And then ran yaboot to write the boot loader
ybin

You have to run this as root.  So include sudo or just run 'sudo su -' to change to the root user.

---

### Post by Mazmot on 2006-11-01
> **wcadrin said:**
> You could check to see if you had the same problem I did.


It seems that it is not the same problem. The link was alright, and after I tried as you showed me, the problem happened again. But somehow, the network manager didn't crash this time on.

---

### Post by maxvonseibold on 2006-11-07
Im having similar problems. Can anyone please help me. I (foolishly) upgraded my g4 powerbook from dapper to edgy the other night. 

After the upgrade the network seemed fine but when I rebooted I cannot connect to a single thing, even my router 
on 192.168.0.1 ... 

I have to say that I find networking extremely hard but I know I am runing DHCP and the network wizard thing says that this is operating.  

I ran the following commands below and I am pretty certain that 'route' should show something but I have no idea how to reset it. 

Could anyone please offer me some advice. 


Thanks. 


Output begins: 



max@orchard:~$ netstat -r
Kernel IP routeing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
max@orchard:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:93:AE:33:DA
          inet6 addr: fe80::20d:93ff:feae:33da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2376 (2.3 KiB)  TX bytes:1836 (1.7 KiB)
          Interrupt:41 Base address:0x6c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

max@orchard:~$ route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
max@orchard:~$
max@orchard:~$ cat /etc/resolv.conf
nameserver 192.168.0.1
max@orchard:~$

---

### Post by Mazmot on 2006-11-08
> **maxvonseibold said:**
> Im having similar problems. Can anyone please help me. I (foolishly) upgraded my g4 powerbook from dapper to edgy the other night. 

After the upgrade the network seemed fine but when I rebooted I cannot connect to a single thing, even my router 

As posted previously, my connection was cut off every time I reboot after my upgrade. Now, the problem was solved after I re-installed 6.10 from live CD. I'm sure the online upgrading process made some error to cause these kind of problems. I recommend you to start all over using live CD. If you have enough space on your hard drive or partition, it can create a new system without losing your existing data (although you have to make a backup). It was much easier for me than poking around the bushes.

---

### Post by maxvonseibold on 2006-11-20
Hey, someone suggested I try the command 'dhclient' 


It worked. Although I have no clue why or how. 



Thanks anyhow though!

---

### Post by magnolia fan on 2006-12-08
I also lost my ethernet after the upgrade. I'm on a G4 Power Mac 800 Mhz Quicksilver Tower (2002). After the upgrade to Edgy, Ethernet was not a configurable option in the Network Tools until I tried this in Terminal:

sudo ifdown eth0
sudo ifup eth0

My ethernet came back on the ifup eth0 command and has not gone down since then.

-cheers

---

### Post by johnrobert on 2006-12-28
Thanks magnolia fan! I had the same AWOL internet after upgrading to Edgy, and your instructions took care of it. Now, on to loading Gnash...

---

