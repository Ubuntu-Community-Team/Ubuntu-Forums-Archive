---
title: "Wireless"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by amrclutch1 on 2007-09-11
I am trying to get my wireless to work. I have a Realtek 8185 Wireless Controller. They have a linux driver, and I followed the instructions listed below in the readme and i get an error (see bottom).[B]

README[/B]
```

RTL8185 Linux Driver v1010.0531.2006 for linux kernel 2.6

  - Support Client mode for either infrastructure or adhoc mode
  - Support WEP and WPAPSK connection

===============================================================================================
< Component >
The driver is composed of several parts:
    (1)source code
	r818x.tar.gz
	stack.tar.gz

    (2)Script ot build the modules
        makedrv

    (3)Script to load/unload modules
        wlan0up
        wlan0down

    (4)Script and configuration for DHCP
	wlan0dhcp
        ifcfg-wlan0

    (5)Supplicant source code
	wpa_supplicant-0.3.8.tar.gz
    	
    (6)Example of supplicant configuration file
	wpa1.conf




< Installation >
Running the scripts can finish all operations of building up modules from source code and start the nic:

	(1)Build up the driver from the source code
         	./makedrv

    	(2)Load the driver module to kernel and start up nic
    		./wlan0up
           (if "insmod: error inserting 'r8180.ko': -File exists." met,
	        ./wlan0rmv
		./wlan0down
		./wlan0up
	    should be OK.
	   )
	(3)Refer to < Set wireless lan MIBs > to set Wireless LAN specific parameters.





< Set wireless lan MIBs >
This driver uses Wireless Extension as an interface allowing you to set
Wireless LAN specific parameters.

Current driver supports "iwlist" to show the device status of nic

        iwlist wlan0 [parameters]
where

        parameter explaination      	[parameters]    
        -----------------------     	-------------   
        Show available chan and freq	freq / channel  
        Show and Scan BSS and IBSS 	scan[ning]          
        Show supported bit-rate         rate / bit[rate]        
        Show Power Management mode      power             

For example:

	iwlist wlan0 channel
	iwlist wlan0 scan
	iwlist wlan0 rate
	iwlist wlan0 power


Driver also supports "iwconfig", manipulate driver private ioctls, to set MIBs.

        iwconfig wlan0 [parameters] [val]
where

        parameter explaination      [parameters]        	[val] constraints
        -----------------------     -------------       	------------------
        Connect to AP by address    ap              		[essid]
        Set the essid, join (I)BSS  essid             		[mac_addr]
        Set operation mode          mode          		{Managed|Ad-hoc}
        Set keys and security mode  key / enc[ryption]          {N|open|restricted|off}


For example:

	iwconfig wlan0 ap XX:XX:XX:XX:XX:XX
	iwconfig wlan0 essid "ap_name"
	iwconfig wlan0 mode Ad-hoc
	iwconfig wlan0 mode essid "name" mode Ad-hoc
	iwconfig wlan0 key 0123456789 [2] open
	iwconfig wlan0 key off
	iwconfig wlan0 key restricted [3] 0123456789

< Getting IP address >
After start up the nic, the network needs to obtain an IP address before transmit/receive data.
This can be done by setting the static IP via "ifconfig wlan0 IP_ADDRESS" command, or using DHCP.

If using DHCP, setting steps is as below:
	
	(1)connect to an AP via "iwconfig" settings
		iwconfig wlan0 essid [name]	or
		iwconfig wlan0 ap XX:XX:XX:XX:XX:XX

	(2)run the script which run the dhclient
		./wlan0dhcp
           or 
		dhcpcd wlan0
              	(Some network admins require that you use the
              	hostname and domainname provided by the DHCP server.
              	In that case, use 
		dhcpcd -HD wlan0)



< WPAPSK >
WPA_SUPPLICANT help the network to communicate under the protection of WPAPSK mechanism
	
	(1)Unpack source code of WPA supplicant:
		tar -zxvf wpa_supplicant-0.4.9.tar.gz
		cd wpa_supplicant-0.4.9
	
	(2)Create .config file:
		cp defconfig .config
		
	(3)Edit .config file, uncomment the following line:
		#CONFIG_DRIVER_IPW=y.
		
	(4)Build WPA supplicant:
		make
        
	If make error for lack of <include/md5.h>, install the openssl lib:
	 1. Install the openssl lib from corresponding installation disc:
	    Fedora Core 2/3/4/5(openssl-0.9.71x-xx), Mandrake10.2/Mandriva10.2(openssl-0.9.7x-xmdk),
	    Debian 3.1(libssl-dev), Suse 9.3/10.0/10.1(openssl_devl), Gentoo(dev-libs/openssl), etc.
	 2. Download the openssl open source package from www.openssl.org, build and install it.
	 
	(5)Edit wpa_supplicant.conf to set up SSID and its passphrase.
	For example, the following setting in "wpa1.conf" means SSID to join is "BufAG54_Ch6" 
	and its passphrase is "87654321".

		network={
			ssid="BufAG54_Ch6"
			proto=WPA
			key_mgmt=WPA-PSK
			pairwise=CCMP TKIP
			group=CCMP TKIP WEP104 WEP40
			psk="87654321"
			priority=2
		}

	(6)Execute WPA supplicant (Assume 8185 and related modules had been loaded):
		./wpa_supplicant -D ipw -c wpa1.conf -i wlan0 &

```
[B]
ERROR[/B]
```

brandon@brandon-laptop:~/Desktop/rtl8185_linux_26.1010.0531.2006$ ./wlan0up
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8180.ko': No such file or directory
wlan0: ERROR while getting interface flags: No such device

```

---

### Post by bvmou on 2007-09-12
Do you get any error messages when you run the script ./makedrv?  The error indicates that the load/unload module is not finding the right compiled objects.  This may mean that they were not compiled properly, the simplest explanations are 1) that you may not have built them with sufficient permissions,  2) you may not have all the tools and libraries to build from source; in that case make sure to install the package "build-essential", which you can get with the command "sudo apt-get install build-essential".  This is a catch-all package for a number of tools to build from source.  All the problem "".ko's are related to cryptographic tools so maybe installing wpa_supplicant first makes sense, you can do that from repos too and shouldn't need the source package mentioned a couple of steps below.  There are some wireless tools, I think the deb is something like "wireless-tools", that can't hurt.

Let us know if any of that works and good luck.  When I have installed wireless devices on Debian I have generally found old instructions, for example the recommendations in the instructions to statically set your WAP are a bore and shouldn't be necessary with network manager or the later gnome tools.

---

