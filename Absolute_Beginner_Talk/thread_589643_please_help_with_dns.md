---
title: "please help with dns"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by stfury on 2007-10-24
Hi There,

i had a problem with my dns - but with help i have sorted it out - im using the dns from OpenDNS and the internet  works perfectly.

the only thing is the dns resets to the old one (10.0.0.2) which doesnt work, on the web page it says u do this in terminal and it should stop the problem ----------------------

    208.67.222.222
    208.67.220.220

To avoid having your settings get revoked after reboots, or after periods of inactivity, do this:

    $ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
    $ sudo gedit /etc/dhcp3/dhclient.conf
    # append the following line to the document
    prepend domain-name-servers 208.67.222.222,208.67.220.220;
    # save and exit
    $ sudo ifdown eth0 && sudo ifup eth0 

You may be required to change eth0 to your own network device's name if it uses a non-standard name.

------------------------------------------------------------------
ok so my device IS DEFINATELY eth0 this i am sure of cos it says eth0 active in my network monitor and its the one sending and receiving many mb's.

ok so when i type in that konsole stuff i get these to errors for the last command --

ifdown: interface eth0 not configured
Ignoring unknown interface eth0=eth0.

----------------------------------------------------------------
pls help!! thanks stfury

as a last thing and this is a real nuub question - if i download a program as a tar.gz2 how the hell do i install it? i go inside that tar.gz2 and i have got no idea how to install when its downloaded like this?? pls help guys

---

### Post by conjur3r on 2007-10-24
Let me guess, you have a DLink modem?  Anyways, as an alternative to configuring your ubuntu computer, you can edit your modem/router and tell it to assign your ISP's DNS servers rather than run a local one.  That way, all computers connected to your modem/router will have your ISP's DNS servers rather than 10.0.0.x

If you do not wish to do the above, copy and paste the contents of the following command:
# ifconfig

Finally, with tar.gz2 files, they are usually the source code to the program.  You will most likely need to follow the installation instructions which should come in the file as INSTALL or README or on the website you downloaded it from.  Try searching Ubuntu's packages at [http://packages.ubuntu.com](http://packages.ubuntu.com) to see if there is a version already available to you.  If there is, it's much easier to install that then to have to compile from source.

---

### Post by stfury on 2007-10-24
thanks i would do the above - but i already tried and it pretty much screwed up my router i had to reset it so i wil rather paste this thanks for all the help.

--------------------------------------------------------------------------------------
eth0      Link encap:Ethernet  HWaddr 00:11:95:65:D1:38  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fe65:d138/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7741 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7706 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4368027 (4.1 MB)  TX bytes:896248 (875.2 KB)
          Interrupt:16 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:15:58:78:62:9A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:44641 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41808 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23232680 (22.1 MB)  TX bytes:4089512 (3.9 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:386 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:29780 (29.0 KB)  TX bytes:29780 (29.0 KB)

eth0 is my gigabit lan port - im using that one.
eth1 is the spare megabit lan port on my mobo i dont use anymore

cheers

---

### Post by conjur3r on 2007-10-24
Well it looks like eth0 is functional again.  Try running both commands separately.

# sudo ifdown eth0

then

# sudo ifup eth0

Failing that, just reboot and see if you have different DNS ips in your /etc/resolv.conf (this would be taking the easy way out).

---

### Post by stfury on 2007-10-24
i did all that and it still doesnt work

---

### Post by stfury on 2007-10-24
pls wil someone help me with this i have tried everything and it is still giving me trouble

---

