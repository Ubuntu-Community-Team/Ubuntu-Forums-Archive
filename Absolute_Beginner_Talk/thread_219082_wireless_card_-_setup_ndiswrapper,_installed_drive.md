---
title: "wireless card - setup ndiswrapper, installed driver,..."
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by next on 2006-07-19
Card: d-link dwl-g510

After several hours of trying to get ndiswrapper to work i finnaly got it, it think. Following  [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu")
i did everything except  7 - Edit the network interface file  because i dont understand. Any help with step 7? and how can i confirm i setup ndiswrapper right.
-Thanks

---

### Post by x64Jimbo on 2006-07-19
Can you be more specific about what you don't understand? 
sudo gedit /etc/network/interfaces
That should get you into editing the file, then you just go to the places in the file that it says to replace something with your own info, and fill them in.
To find out if ndiswrapper is working, run
ifconfig
if it shows your wireless interface, it's working. ;)

---

### Post by next on 2006-07-19
i ran ifconfig,  i got 
eth0      Link encap:Ethernet  HWaddr ********
          inet addr:******  Bcast:********
  Mask:*********
          inet6 addr: **********
Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16512802 (15.7 MiB)  TX bytes:2672236 (2.5 MiB)

lo        Link encap:Local Loopback
          inet addr:*******  Mask:********88
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:93 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6944 (6.7 KiB)  TX bytes:6944 (6.7 KiB)

I have a wire connectoin while trying to setup my card. Not sure if ndiswrapper is working.

For netowrk interface, 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

I know im supposed to put info like wep key and stuff but were? what does ath0 stand for?

Thanks for your help

---

### Post by x64Jimbo on 2006-07-19
ath0 is an Atheros Chipset wifi card (with native Linux drivers - no ndiswrapper needed. Very good WiFi card for Linux)
try 
sudo ifconfig ath0 up
sudo iwconfig ath0 essid <SSID> key <key>
sudo dhclient ath0

---

### Post by next on 2006-07-19
no im sorry i dont have an atheros chipset, i have marvell, i just didn't know what ath0 stood for.

After some searching(which i should have done before posting) im guessing, under wlan0 you put your setting for wireless?

---

### Post by next on 2006-07-19
Ok i put adress, netmask, and gateway. (netmask the same as subnetmask?) under wlan0. I left everything else blank. Then i copies the interface file to the correct directory using mv. Then i rean /etc/init.d/networking restart. At the end of that i got 
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

Any help?

---

### Post by next on 2006-07-19
im still lost but i ran iwconfig and got 
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

I have no idea what to do, please help.

---

### Post by x64Jimbo on 2006-07-19
Sounds like your ndiswrapper is not loaded. Did you configure it already? What commands did you use? Did you modprobe ndiswrapper after you set it up?

---

### Post by next on 2006-07-20
thanks alot for the help jimbo, i cant get to my pc right now but i will check first thing in the morning. thanks

---

### Post by next on 2006-07-20
by configure ndiswrapper do you mean install? i installed the package ubuntu then installed the driver with "ndiswrapper -i driver". I did modprobe ndiswrapper, but nothing happen, is anything supposed to?

Can anyone help me set up the network interfaces. AIM anyone?

thanks.

---

### Post by x64Jimbo on 2006-07-22
By configure ndiswrapper I meant doing ndiswrapper -i driver, which it appears you have done already. Did that command work? what was its output? If you modprobe ndiswrapper and it doesn't say anything at all, that means it worked.

---

