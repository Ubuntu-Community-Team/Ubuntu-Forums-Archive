---
title: "broadcom wireless card"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by conbrio on 2006-03-19
Hello all,

This is yet again another thread about a broadcom wirless card. I have a Compaq V5000Z laptop just over 2 weeks old. Anyways I have been reading and searching on how to get the wireless to work. So far very little has gone correctly. Last night I got the status light on the laptop for the wireless to come on, but the OS, Breezy 5.10 edubuntu, was saying that the hardware was not installed. I also got the OS to load the driver for the card 'bcmwl5', at least I believe it was installed. 

What I am needing is someone to help me get ubuntu to recoginize the built in wireless card and get this thing running. Thanks

ConBrio

---

### Post by Zelut on 2006-03-19
I suggest taking a look at my wireless howto (in my signature) and trying the steps.  If you get stuck at any point just reply here & we'll help give you the nudge you need.

If you've got broadcom you'll be fine.  Its a very well supported card.

---

### Post by conbrio on 2006-03-19
Kuyaedz,

Ok I went to the linux wireless link in your sig. 

First step was everything was updated
Second Step did nothing. when I typed the lspci line it just when straight to the next command line. Nothing was posted after typing in that line. 

On a side note, I am assuming that you are in Utah from the links in your sig. May I ask what part? I have two sisters in Utah with their families

---

### Post by Zelut on 2006-03-19
I'm a bit south of Salt Lake, in Orem.

Ok.  First command didn't return any results, we'll try a variation.
(this is listing all pci cards & searching for keywords)
lspci | grep Wireless
lspci | grep Wifi
lspci | grep Network

or
dmesg | 802.11
dmesg | Wireless

---

### Post by conbrio on 2006-03-19
ok here are the results

lspci | grep Wireless - nothing returned
lspci | grep Wifi - nothing returned
conbrio@edubuntu:~$ lspci | grep Network
0000:06:02.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)

or
conbrio@edubuntu:~$ dmesg | 802.11
bash: 802.11: command not found
conbrio@edubuntu:~$ dmesg | Wireless
bash: Wireless: command not found

Not sure how close everything is but both of my sisters live in Heber

---

### Post by Zelut on 2006-03-19
Ok.  Lets try the following:
> 
sudo apt-get install ndiswrapper-utils
wget [http://christer.homeip.net/bcmwl5.inf](http://christer.homeip.net/bcmwl5.inf)
wget [http://christer.homeip.net/bcmwl5.sys](http://christer.homeip.net/bcmwl5.sys)
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l (thats L)

Does this return 'driver present, hardware present'?

---

### Post by conbrio on 2006-03-19
conbrio@edubuntu:~$ sudo ndiswrapper -i bcmwl5.inf
bcmwl5 is already installed. Use -e to remove it
conbrio@edubuntu:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5  invalid driver!

---

### Post by Zelut on 2006-03-19
can you try to remove the existing driver & try with the newly downloaded?
sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -i bcmwl5.inf

...if that doesn't work I'll look for an alternate driver.  Can you give me the output of:
lspci -n | grep 0000:06:02.0

---

### Post by conbrio on 2006-03-19
conbrio@edubuntu:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present

ok. a step in the right direction. whoo hoo

---

### Post by conbrio on 2006-03-19
conbrio@edubuntu:~$ lspci -n | grep 0000:06:02.0
0000:06:02.0 0280: 14e4:4318 (rev 02)

---

### Post by Zelut on 2006-03-19
Good to see! :)

Now we'll do:
sudo modprobe ndiswrapper
(this inserts the ndiswrapper module into the kernel)

Now you can open your Networking (System > Admin > Networking) and setup your wireless card (ie; broadcast name, DHCP/static).  You may need to reboot, I do sometimes on first setup of ndiswrapper.  Let me know how it goes.

---

### Post by conbrio on 2006-03-19
ok, I finally saw the wireless in network, decided to reboot and then go from there. now that I have rebooted the wireless option in networking is gone.

ran modprobe ndiswrapper and it is back. anyway do have this automatically have this set upon bootup

---

### Post by Zelut on 2006-03-19
After I posted I realized I forgot to give you the command to automagically load the driver at boot time.

At this point you can do:
sudo modprobe ndiswrapper
sudo ndiswrapper -m
(the -m option sets it to load automagically)

---

### Post by conbrio on 2006-03-20
ok.  Card is activated. Thank you. Made it very straight forward.next question. Card says it is connected and has 100% signal strength, but I am not getting anything to load. Tried to log into router and connection refused. Any tips or suggestions?

---

### Post by Zelut on 2006-03-20
Well try a few checks..

'ifconfig'.  Does that give you an IP address for your wireless card?  (I'm guessing it'll list eth0, wlan0 & lo.  Does wlan0 have an IP assigned?)

You can try 'sudo dhclient' and try to recieve a new IP.. maybe it is detecting your card but isn't actually connected to anything.

Another thing to verify is whether you have any kind of encryption or mac filtering set on your router.  If so you'll have to update for those settings as well.

This is all that comes to mind right now.. I hate to leave you hangin' but I do need to get to bed.  If you are still stuck I'll see what I can look into in the morning.  Looks like we made some good progres though.

---

### Post by conbrio on 2006-03-20
ok. still not connecting but here is what I have tried so far to get it to work. I ran ifconfig and no ip addy was assigned. I then did 'sudo dhclient' came back with 'No DHCPOFFERS recieved' 'No working leases in persistent database - sleeping'. Searched around and decided to try Disabling IPv6 according to [https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4]("https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4") and then ran 'ifconfig' again after a reboot. Got an ipaddy. Now I did make sure that the WPA on the router was turned off and the ssid was braodcasting, but still no connection. All this was with a static address. Changed static to DHCP and now no more ipaddy. I am going to bed now. I have early classes then work tomorrow so it will be after 9p est before I can check back. Thanks for the help.

ConBrio

---

### Post by conbrio on 2006-03-20
Evening all, 

time more more questions on getting connected to the net via wireless. I have tried several thing to see if I can get connected. Some of the things I have tried are what is listed above, [http://ubuntuforums.org/showpost.php?p=581811&postcount=18](http://ubuntuforums.org/showpost.php?p=581811&postcount=18), [https://wiki.ubuntu.com/WifiDocs/Driver/Broadcom43xx?highlight=%28WifiDocs%2FDriver%29](https://wiki.ubuntu.com/WifiDocs/Driver/Broadcom43xx?highlight=%28WifiDocs%2FDriver%29),
and one or two other things. Now I am getting when I do 'iwconfig' is essid:off/any Mode:Managed Freq:2.412 GHz Access point: 00:00:00:00:00:00
Bit Rate:54 Mb/s Tx-Power:25dBm
Power Management: off
Link Quality: 100/100 Signal Level:-10dBm Nosie Level:-256 dBm
Rx invalad nwid:0 Rx invalad crpt:0  invalad frag:0
Tx excessive rtries:0 Invalid misc:0 Missd beacon:0

I have also tried to scan but no scan results. any help?

---

### Post by Zelut on 2006-03-20
I guess I should ask..  are you using Breezy or Dapper?  Unfortunately I've continued to have problems with Dapper + wireless, although Breezy has been pretty simple.

If you're using Dapper I'm going to have to bow out.  I'm working my own issues with that one.

---

### Post by conbrio on 2006-03-20
breezy. Gess I should put that in a sig or somewhere, huh.

---

### Post by conbrio on 2006-03-21
HOT DOG!! Wireless works now. I followed MetalMusicAddict's advice in this thread [http://www.ubuntuforums.org/showthread.php?t=25683&page=13&highlight=status+light]("http://www.ubuntuforums.org/showthread.php?t=25683&page=13&highlight=status+light"). 
after the driver and hardware for my broadcom wirelesscard was recognized in ubuntu 
> I found out that my "/etc/network/interfaces" wasnt being saved properly.

I had to do this:
Code:

# This file describes the network interfaces available on your system # and how to activate them. For more information, see interfaces(5). # The loopback network interface auto lo iface lo inet loopback # This is a list of hotpluggable network interfaces. # They will be activated automatically by the hotplug subsystem. mapping hotplug script grep map eth0 <-change to wlan0 # The primary network interface<- Move this down iface eth0 inet static address *.*.*.* netmask *.*.*.* gateway *.*.*.* TO HERE!! iface wlan0 inet static address *.*.*.* netmask *.*.*.* gateway *.*.*.* wireless-essid ****** wireless-key **************** auto wlan0

The network works great now. Just like it was plugged in.

night all. Stayed up too late tonight with a midterm in the morning

ConBrio

---

