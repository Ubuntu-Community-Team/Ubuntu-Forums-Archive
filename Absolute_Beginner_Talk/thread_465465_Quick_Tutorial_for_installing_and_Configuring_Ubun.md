---
title: "Quick Tutorial for installing and Configuring Ubuntu"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by hkahwaji on 2007-06-05
Dual-boot Windows Vista and Ubuntu Linux 

This tutorial was put together with the help of a lot of users in this forum.

This tutorial is intended to be for users who are new to Ubuntu and would like to install it at home and configure their laptop for everyday use. Also,with the public release of Windows Vista, there are likely many users like me who would like to install Windows Vista along side some sort of Linux distribution. I chose Ubuntu Desktop Edition version 7.04. If you would like to add anything to this please feel free.
In my testing case, I used the Hard Drive Delete Utility that is included in a Recovery DVD that was given when I bought my laptop
1.	Insert the Recovery and Utility Disc
2.	Boot to the DVD
3.	Accept the license agreement
4.	Select the Utilities Tab
5.	Highlight Hard Drive Delete and click Start
After formatting the hard drive, you can now can use the other utility built in to the Recovery DVD and create 2 partitions. Essentially, one for Vista and the other for Ubuntu Linux
The problem arises with two small features of Windows Vista that does not play well with Linux. The first of which, and the main issue, is the new bootloader that Windows Vista uses. The second, which only causes minor issues, is the new NTFS format that is used by Vista. The main installation procedure that is recommended to avoid any troubles is to install Vista on the second partition that you created and then install Linux on the other partition. It is always safe to leave the best for last.
Note: When you install Ubuntu make sure that you select GRUB as your bootloader. GRUB will overwrite Vista bootloader in the MBR, but GRUB will be able to boot Vista after making some minor modifications to the /boot/grub/menu.lst file. 
Section A. Installing Vista and Linux
Obtain a copy of Vista Business and burn the iso-image to a DVD. Insert the DVD and boot to it. Go through the proper steps of installing Vista. In my testing, I installed Vista to the first partition and Ubuntu to the other one.

To obtain a copy of Ubuntu 7.04 Desktop Version, go to [www.ubuntu.com](www.ubuntu.com) and download the iso-image. Burn the ISO image to a DVD and then boot to the DVD. 
Go through the normal steps of installing Linux. Make sure that you install Linux on the other partition. Not the one that Vista is on.
DO NOT resize the Vista partition during the installation of the Linux distribution! Due to the change in NTFS versions, no Linux partitioning program, nor standard Windows partitioning programs, can properly alter the partition that Vista is installed to. Also, be sure to specify that GRUB is the bootloader to be installed if this is an option. After installation is completed, you will boot into the Linux operating system that you installed. 
This below section is what was recommended to do after the Linux installation. In my testing, I did not have to do that. I was able to boot to Linux and see Vista entry in the menu.lst file under /boot/grub
If you want to verify that in your menu.lst file, do the following. Open a terminal
To open a terminal, do the following: Applications -> Accessories -> Terminal
Run the following command as root:
	sudo gedit /boot/grub/menu.lst
Go to the end of the file and verify that you see a Vista entry that looks like that.
title         "Windows Vista" 
root         (hd0,0) 
chainloader      +1
Make sure that it is not commented out using the #.

Vista was installed on the first partition of IDE hard drive so that is why the location is (hd0,0) 

Now that you have this configured, you now have a system configured with Dual-Boot Windows and Ubuntu

Reboot the system -> Verify that GRUB lists the 2 OS (Vista and Ubuntu) -> Select the one that you want GRUB to load to memory

Section 2: Configuring your ATI X1400 card

My E8210 has ATI Radeon X1400 card, so the next step to do is install the xorg-driver-fglrx and change the resolution to 1280x800. Currently, your resolution is set to 800x600.

To install the driver do the following:

1.	Connect via the wire to the internet
2.	Open a terminal as specified above and run the following commands

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install xorg-driver-fglrx
sudo depmod –a
sudo aticonfig - - initial
sudo aticonfig - - overlay-type=Xv

Restart the system and go to System -> Preferences -> Screen Resolution and set the resolution to 1280x800.

Section 3: How to Configure your Wireless Card in Unbuntu 7.04

Wireless card: Intel PRO/Wireless 3945 a/b/g 
Kernel version: 2.6.20-15-generic Ubuntu 7.04 Desktop

The above distribution of Ubuntu already contains Intel PRO/Wireless 3945 Linux Driver. To verify that go to: System -> Administration -> Restricted Drivers Manager. To verify that Linux sees your wireless card and to gather information about the wireless card, open a terminal and run the following command as root:

sudo lshw -C network

The above command should display a result close to this:

*-network

       description: Ethernet interface

       product: 88E8055 PCI-E Gigabit Ethernet Controller

       vendor: Marvell Technology Group Ltd.

       physical id: 0

       bus info: pci@02:00.0

       logical name: eth0

       version: 12

       serial: 00:17:42:07:ae:52

       size: 100MB/s

       capacity: 1GB/s

       width: 64 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=sky2
driverversion=1.13 duplex=full firmware=N/A latency=0 link=no multicast=yes port=twisted pair speed=100MB/s

       resources: iomemory:f0100000-f0103fff ioport:3000-30ff irq:16

  *-network

       description: Wireless interface

       product: PRO/Wireless 3945ABG Network Connection

       vendor: Intel Corporation

       physical id: 0

       bus info: pci@05:00.0

       logical name: wlan0

       version: 02

       serial: 00:13:02:30:ba:f2

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical wireless

       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp
firmware=14.2 1:0 () ip=192.166.1.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11g

       resources: iomemory:58100000-58100fff irq:21


Now that you verified that your wireless card is seen. You can install Network Manager and use it to manage/configure your network devices. Open a terminal and run the following command as root:

sudo apt-get network-manager

Reboot the system

Open another terminal and run Network-Manager as root:

	sudo network-manager

This will launch the application for you. You should see the list of wireless networks that are detected. Use the wizard to connect to your choice of wireless network.

This is the easiest way to connect to a wireless network; however I recommend prior to installing Network-Manger to use command line terminal to configure your WLAN card so you get to see how that works.

Note: I do not recommend installing Network Manager and then modifying the interfaces file. That might mess things up.

Steps required configuring your wireless card via the command line terminal

Run the following the command as root from the terminal

	sudo cat /etc/iftab

You should see an output equivalent to the following:

eth0 mac 00:17:42:07:ae:52 arp 1

wlan0 mac 00:13:02:30:ba:f2 arp 1


Your eth0 entry is the MAC address of your Ethernet card, and your wlan0 entry is the MAC address of your Intel 3945 wireless card. I recommend that you write those down for later use.

Note: When I first installed Ububtu, for some reason I had eth1 instead of wlan0 in the above file. This does cause a problem. Primarily it will not allow you to scan for available wireless networks since scanning is usually done through wlan0. If you have the same problem, edit the file and replace the eth1 with wlan0

To edit the file, run the following command from a terminal

	sudo gedit /etc/iftab

This will open the iftab file using Gedit editor. Make the necessary changes, save, and close the file.

Now that you have set logical interface for the wireless card to wlan0, do the following. Open a terminal window and run the following command to see how the interfaces file is structured:

	sudo cat /etc/network/interfaces

Output should look like this:

auto lo

iface lo inet loopback



iface eth1 inet dhcp



auto eth2

iface eth2 inet dhcp



auto ath0

iface ath0 inet dhcp



auto wlan0

iface wlan0 inet dhcp


auto eth1

iface eth0 inet dhcp


auto eth0


Make sure that you see the wlan0 entry. If so, that means that your iftab file changes were applied successfully if there were any.

If you are wondering about the other different logical interfaces, here is a brief explanation:

eth0: interface to your wired Ethernet network
eth1: interface to your wired Ethernet network (in case you have two ethernet NIC cards)
lo: loopback address. That is usually your 127.0.0.1
ath0: I believe this can be for Atheros card (Not sure on this one)

Open another terminal and run the following command

	ifconfig  -a

Your output should look something equivalent to this:

eth0      Link encap:Ethernet  HWaddr 00:17:42:07:AE:52

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:586 errors:0 dropped:0 overruns:0 frame:0

          TX packets:622 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000

          RX bytes:545123 (532.3 KiB)  TX bytes:67086 (65.5 KiB)

          Interrupt:16



eth0:avah Link encap:Ethernet  HWaddr 00:17:42:07:AE:52

          inet addr:169.254.5.3  Bcast:169.254.255.255  Mask:255.255.0.0

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          Interrupt:16



lo        Link encap:Local Loopback

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:6 errors:0 dropped:0 overruns:0 frame:0

          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0

          RX bytes:399 (399.0 b)  TX bytes:399 (399.0 b)



wlan0     Link encap:Ethernet  HWaddr 00:13:02:30:BA:F2

          inet addr:192.166.1.102  Bcast:192.166.1.255  Mask:255.255.255.0

          inet6 addr: fe80::213:2ff:fe30:baf2/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:464 errors:81 dropped:2475 overruns:0 frame:0

          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000

          RX bytes:343873 (335.8 KiB)  TX bytes:10841 (10.5 KiB)

          Interrupt:21 Base address:0xc000 Memory:58100000-58100fff


Verify that you see the wlan0 logical port listed in the output. At this point, you will not see an IP address assigned to the wlan0 port since you are not connected to an AP. You might have an IP address assigned to eth0 port if you are connect to a network via the wire

If the above went well, now you can modify the interfaces file to connect to a wireless network close to you. Login to your wireless router via the browser and verify that your wireless security setting is set to DISABLED. Write down your SSID.

Now we start can start modifying the interfaces file to add the wireless settings; however prior to any modification, I recommend that you backup the existing interfaces file, in case you want to revert back to it. To create a backup copy of the file, run the following command as root

	sudo cp /etc/network/interfaces /etc/network/interfaces.bak

While you are in that directory, run the following command to see if the backup file was created:
	
	ls -l

Now you can edit the file interfaces knowing that you have a backup

Open a terminal window and run the following command as root:

	sudo gedit /etc/network/interfaces

This will open the interfaces file with GEDIT. Add the following right after auto wlan0 in the file

iface wlan0 inet dhcp

wireless-essid <your-wireless-ssid>

To make the file look like

auto wlan0
iface wlan0 inet dhcp
wireless-essid <your-wireless-ssid>

Note: Keep the information about the other ports i.e (eth0 and eth1)

Save and close the file.

Note: In the above, we have set the inet to dhcp, you can specify static IP address if you want to. Add the following instead if you choose the static IP address route:

iface wlan0 inet static
IP address 192.166.1.102
Gateway 192.166.1.1
dns-nameservers x.x.x.x

I recommend that you set it to dhcp and let the wireless router lease you an IP address

Now that you have made the changes, it is time to test. Close all terminals and applications and reboot the system.

System -> Quit -> Restart

After rebooting, open a terminal console and run the following command: Make sure when you test this to remover your Ethernet cable if you have any plugged in to the Ethernet port:

	iwconfig

The ouptut should look like this:

lo        no wireless extensions.



eth0      no wireless extensions.



wlan0     IEEE 802.11g  ESSID:"linksys-n"

          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:18:F8:37:7F:36

          Bit Rate:18 Mb/s   Tx-Power:15 dBm

          Retry limit:15   RTS thr:off   Fragment thr:off

          Power Management:off

          Link Quality=43/100  Signal level=-83 dBm  Noise level=-84 dBm

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:4135   Missed beacon:0


To verify that your wlan0 acquired an IP address: run the following command

	ifconfig wlan0

Your output should look something like this:

wlan0     Link encap:Ethernet  HWaddr 00:13:02:30:BA:F2
          inet addr:192.166.1.102  Bcast:192.166.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe30:baf2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1304 errors:55 dropped:1321 overruns:0 frame:0
          TX packets:556 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1054210 (1.0 MiB)  TX bytes:57626 (56.2 KiB)
          Interrupt:21 Base address:0xc000 Memory:58100000-58100fff

As you can see, I have an IP address assigned, MAC address of my Intel 3945 ab/g card is listed and some other information such as Mask and Broadcast address

If your wlan0 is assigned an IP address, try to ping the gateway or AP

	ping <IP_ADDRESS_of_Gateway>

If that is successful, try to ping [www.yahoo.com](www.yahoo.com)

	ping <www.yahoo.com>

Now you are connected to your wireless AP:

Considering that we all use laptops, you might end up in a place that offers free wireless. To scan the wireless Access Points that are within your range, open a terminal console and run the following command:

	iwlist scan

This will list the AP's that are within range along with their properties such as if they secured or not.


How to enable WEP

 In Windows, you can always enter the WEP key when you try to connect to a 
secured wireless network. Here is how to set it up in Ubuntu.

Lets go back to the interfaces file and add the following line under 
wireless-essid

wireless-essid <your-wireless-ssid.
wireless-key <xxxxxxxxxx>

Note: The xxxxxxxxxx represents the 10 hexadecimals that you used when 
creating your key within your wireless router. This 10 hexadecimal key is 
equivalent to 64 bit encryption key.

Save the file and Quit.

Open a terminal console and run the following commands

	sudo /etc/init.d/networking restart

This command will flush all the IP addresses that you have assigned on all 
the terminals and obtains new IP addressed through the DHCP server.

You can also use the following set of commands:

	sudo ifdown wlan0
	sudo dhclient wlan0

Verify that you have associated to your AP with new setting:

	ifconfig
	iwconfig

You should have an IP address now

	ping <www.yahoo.com>

How to configure WPA-PSK

Make the necessary changes in your AP to set the wireless security settings to WPA-PSK / TKIP or AES. Open a terminal and download the wpa_supplicant support. To install wpa_supplicant, run the following command from the terminal

	sudo apt-get install wpasupplicant 

On your computer, edit the interfaces file in the /etc/network directory to add the following:

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid <your_wireless_network_ssid>
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <your-hex-key>

Note: Here is the description of the values that are passed:
Wlan0: is the logical interface for your wireless card
Dhcp: setting the DHCP protocol
wpa-driver: that is Linux wireless extensions (generic)
wpa-ssid: Your wireless network SSID
wpa-ap-scan: Values can be either 1 or 2. Set to 1 if you are broadcasting the SSID or 2 if you are not broadcasting the SSID
wpa-proto: WPA if you have WPA(1) set up at your AP or RSN if you have WPA(2) set up at AP
wpa-pairwise: TKIP if wpa-proto is WPA and CCMP if you have wpa-proto set to RSN
wpa-group: TKIP if wpa-proto is WPA and CCMP if you have wpa-proto set to RSN
wpa-key-mgmt: WPA-PSK  (Authentication via pre-shared key)
or 
"WPA-EAP" = Authentication via enterprise authentication server.

Note: You will need to pass the a hex key for wpa-psk, to obtain the hex equivalent to the passphrase that you set up at the AP. Open a terminal and run the following command:

	wpa_passphrase <your-wireless-essid> <your-passphrase>

You should get an output equivalent to this:

network={
        ssid="linksys-n"
        #psk="test1234"
        psk=7270ebe2783ca7af537cc1a618e6306169a8aa1f142c1877f766d1a4a6da6cbd

The psk value is your hex key. Copy and paste that to the wpa-psk key value.

Save the file and restart your networking services using the following command:

	sudo /etc/init.d/networking restart

You now should be able to obtain an IP address

---

### Post by gimmy_bond on 2007-06-06
It is very nice tutorial.
My problem is that I have Feisty installed on a partitioned disk. (only ubuntu) 15GB for the OS and 130GB for personal files. Now I have diffulties during the boot up, where some drives and setup got corrupted. 

 How do I re-install the Feisty just to refresh and update the drives, and bring it back to its original working state?. 

thanks

---

