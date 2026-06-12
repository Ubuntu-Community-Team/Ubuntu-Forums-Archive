---
title: "Help, I think I'm nearly wireless"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by gleble on 2007-12-15
neil@neil-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
driver : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
I presume this means my Broadcom wireless device is present and the driver is installed. However if I go to Network Tools it is not listed as a Network device.

I am new to Ubuntu and not too hot on wireless matters. Help

---

### Post by pHreaksYcle on 2007-12-15
Okay bro you called here I am. Your going to love this! from [here]("http://www.ubuntu1501.com/2007/11/wireless-in-gutsy-gibbon-with.html")

Step 4: Configure the Windows driver with ndiswrapper
Now install the Windows driver
In a terminal type:
sudo ndiswrapper -i bcmwl5.inf
Then:
sudo ndiswrapper -l (that is a lowercase L)

You should see a message that says driver present, hardware detected.

Now finish installing the driver
In a terminal type:
sudo ndiswrapper -m
Then:
sudo modprobe ndiswrapper

YOU MUST REBOOT NOW!
In a terminal type:
sudo reboot

STEP 5: TEST WIRELESS
Your WiFi light on your laptop should be illuminated. If not, you can always turn it on and off with the Fn+F2 (Function & F2 Key) and you're all set! Try running this to see if your wireless card is functioning properly.

In a terminal type:
sudo iwlist scanning

If once you get everything working and after a reboot and the wifi light does not come back on, simply repeat Step 4 and wireless will work again.


Step 6: Make it Stick
To autostart the ndiswrapper module
In a terminal type:
sudo gedit /etc/modules

and add this to the end of the file
ndiswrapper

---

### Post by gleble on 2007-12-15
OK this is where I got, still doesn't work, however Network tools now shows eth0 and eth1 and they're both ethernet

neil@neil-laptop:~$ sudo ndiswrapper -i bcmwl5.inf
[sudo] password for neil:
driver bcmwl5 is already installed
neil@neil-laptop:~$ sudo ndiswrapper -m
module configuration already contains alias directive

neil@neil-laptop:~$ sudo ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
driver : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
neil@neil-laptop:~$ sudo modprobe ndiswrapper
REBOOTED AT THIS POINT
neil@neil-laptop:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

neil@neil-laptop:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

neil@neil-laptop:~$

---

### Post by Cybergod on 2007-12-15
What are the results of 'sudo iwconfig'?  Does it show the MAC address of your router?

---

### Post by gleble on 2007-12-15
neil@neil-laptop:~$ sudo iwconfig
[sudo] password for neil:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Does that help?

---

### Post by Cybergod on 2007-12-15
Is your Wifi encrypted?  Right click the Network icon in the top right corner and see if your network is there.

---

### Post by gleble on 2007-12-15
It is encrypted but I don't know where to enter the WEP code
Connection info is
Interface:     Wired Ethernet (eth0)
Speed 100mb/s
Driver Sky2
IP Address      192.168.1.153
Broadcast       192.168.1.255
subnet mask    255.255.255.0
Default route   192.168.1.1
Primary DNS    192.168.1.1
Secondary DNS 0.0.0.0
Hardware address  00:16:36:C8:83;B9

Any clearer?

---

### Post by Cybergod on 2007-12-15
I could only get mine to work using DHCP and not a static IP address.  Click the network icon in the top right corner and create a new network connection, some where in there you'll be able to enter your encryption key.

---

### Post by gleble on 2007-12-15
Thanks sorted

---

### Post by pHreaksYcle on 2007-12-16
Glad it worked for you!

---

