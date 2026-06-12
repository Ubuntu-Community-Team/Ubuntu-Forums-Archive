---
title: "Help with Linux Mint Version 11 network drivers"
date: 2012-03-30
forum: Any Other OS
---

### Post by 2048Megabytes on 2012-03-30
Well, I deleted the Ethernet driver because it was working poorly.  I could not get download speeds over 160 kilobytes per second and the connection would drop to zero many times for more than two minutes.  Now I cannot reinstall the Ethernet drivers that I have on my hard drive. So now I have no network interface card drivers and cannot obviously get on the Internet at all with Linux Mint Version 11. This is very frustrating. I am a newbie when it comes to reinstalling drivers for Linux.  I have been trying to fix this for hours.

Any help would be appreciated.

My motherboard is a GIGABYTE GA-970A-D3.  I downloaded the network interface card drivers from here:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)

I downloaded LINUX driver version 8.029.00

---

### Post by howefield on 2012-03-30
Thread moved to the "*Other OS/Distro Talk*" forum.

---

### Post by TransitMan on 2012-03-30
> **2048Megabytes said:**
> 
Any help would be appreciated.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)

I downloaded LINUX driver version 8.029.00

Here is the readme file from that download. It is pretty self explanitory.
Just follow the directions, and if you need to copy-paste the commands in terminal.

```

<Linux device driver for Realtek Ethernet controllers>

	This is the Linux device driver released for RealTek RTL8168B/8111B, RTL8168C/8111C, RTL8168CP/8111CP, RTL8168D/8111D, RTL8168DP/8111DP, and RTL8168E/8111E Gigabit Ethernet controllers with PCI-Express interface.

<Requirements>

	- Kernel source tree (supported Linux kernel 2.6.x and 2.4.x)
	- For linux kernel 2.4.x, this driver supports 2.4.20 and latter.
	- Compiler/binutils for kernel compilation

<Quick install with proper kernel settings>
	Unpack the tarball :
		# tar vjxf r8168-8.aaa.bb.tar.bz2

	Change to the directory:
		# cd r8168-8.aaa.bb

	If you are running the target kernel, then you should be able to do :

		# ./autorun.sh	(as root or with sudo)

	You can check whether the driver is loaded by using following commands.

		# lsmod | grep r8168
		# ifconfig -a

	If there is a device name, ethX, shown on the monitor, the linux 
	driver is loaded. Then, you can use the following command to activate 
	the ethX.

		# ifconfig ethX up

		,where X=0,1,2,...

<Set the network related information>
	1. Set manually
		a. Set the IP address of your machine.

			# ifconfig ethX "the IP address of your machine" 

		b. Set the IP address of DNS.

		   Insert the following configuration in /etc/resolv.conf.
		
			nameserver "the IP address of DNS"

		c. Set the IP address of gateway.

			# route add default gw "the IP address of gateway"

	2. Set by doing configurations in /etc/sysconfig/network-scripts
	   /ifcfg-ethX for Redhat and Fedora, or /etc/sysconfig/network
	   /ifcfg-ethX for SuSE. There are two examples to set network 
	   configurations.

		a. Fixed IP address:
			DEVICE=eth0
			BOOTPROTO=static
			ONBOOT=yes
			TYPE=ethernet
			NETMASK=255.255.255.0
			IPADDR=192.168.1.1
			GATEWAY=192.168.1.254
			BROADCAST=192.168.1.255

		b. DHCP:
			DEVICE=eth0
			BOOTPROTO=dhcp
			ONBOOT=yes	

<Modify the MAC address>
	There are two ways to modify the MAC address of the NIC.
	1. Use ifconfig:

		# ifconfig ethX hw ether YY:YY:YY:YY:YY:YY

	   ,where X is the device number assigned by Linux kernel, and
		  YY:YY:YY:YY:YY:YY is the MAC address assigned by the user.

	2. Use ip:

		# ip link set ethX address YY:YY:YY:YY:YY:YY

	   ,where X is the device number assigned by Linux kernel, and
		  YY:YY:YY:YY:YY:YY is the MAC address assigned by the user.

<Force Link Status>

	1. Force the link status when insert the driver.

	   If the user is in the path ~/r8168, the link status can be forced 
	   to one of the 5 modes as following command.

		# insmod ./src/r8168.ko speed=SPEED_MODE duplex=DUPLEX_MODE autoneg=NWAY_OPTION

		,where
			SPEED_MODE	= 1000	for 1000Mbps
					= 100	for 100Mbps
					= 10	for 10Mbps
			DUPLEX_MODE	= 0	for half-duplex
					= 1	for full-duplex
			NWAY_OPTION	= 0	for auto-negotiation off (true force)
					= 1	for auto-negotiation on (nway force)
		For example:

			# insmod ./src/r8168.ko speed=100 duplex=0 autoneg=1

		will force PHY to operate in 100Mpbs Half-duplex(nway force).

	2. Force the link status by using ethtool.
		a. Insert the driver first.
		b. Make sure that ethtool exists in /sbin.
		c. Force the link status as the following command.

			# ethtool -s ethX speed SPEED_MODE duplex DUPLEX_MODE autoneg NWAY_OPTION

			,where
				SPEED_MODE	= 1000	for 1000Mbps
						= 100	for 100Mbps
						= 10	for 10Mbps
				DUPLEX_MODE	= half	for half-duplex
						= full	for full-duplex
				NWAY_OPTION	= off	for auto-negotiation off (true force)
						= on	for auto-negotiation on (nway force)

		For example:
		
			# ethtool -s eth0 speed 100 duplex full autoneg on

		will force PHY to operate in 100Mpbs Full-duplex(nway force).

<Jumbo Frame>
	Transmitting Jumbo Frames, whose packet size is bigger than 1500 bytes, please change mtu by the following command.

	# ifconfig ethX mtu MTU

	, where X=0,1,2,..., and MTU is configured by user.

	RTL8168B/8111B supports Jumbo Frame size up to 4 kBytes.
	RTL8168C/8111C and RTL8168CP/8111CP support Jumbo Frame size up to 6 kBytes.
	RTL8168D/8111D supports Jumbo Frame size up to 9 kBytes.
```

---

### Post by 2048Megabytes on 2012-03-31
The instructions in that help file aren't clear to me.  I did the following:


I right click the file **r8168-8.028.00.tar.bz2** and the left click **Open with archive manager**
I left click the **Location:** window and extract the files to: **tar vjxf r8168-8.aaa.bb.tar.bz2**

I then open Terminal by doing the following:
Menu => Terminal
I type the following command into Terminal: **cd r8168-8.aaa.bb**
When I type in the above I get the following error in Terminal:

“bash: cd: r8168-8.aaa.bb: No such file or directory”

---

### Post by TransitMan on 2012-03-31
Where did you unpack the folder to? Specifically.

---

### Post by 2048Megabytes on 2012-03-31
I extracted the files to: tar vjxf r8168-8.aaa.bb.tar.bz2

I have also tried extracting the files to the Desktop also with no success.

---

### Post by TransitMan on 2012-03-31
The files should extract to a folder named r8168-8.029.00
After extracting the folder, to your Desktop, then open a terminal and type in cd /Desktop/r8168-8.029.00
Then follow the directions doing sudo sh autorun.sh
This should install the drivers you need.
You may have to log out and log in to and then check to see if they are installed and loaded by following the directions from above.

---

### Post by 2048Megabytes on 2012-03-31
I extracted the files to my desktop.  I then opened terminal and typed the following:

cd /home/ubuntu-user/desktop/r8168-8.028.00 

I got the following error code:

bash: cd: /home/ubuntu-user/desktop/r8168-8.028.00: No such file or directory 


I also typed other variations to try and get into the directory without success.  I know that what I typed is the right folder path though because I looked it up.  Any ideas?

---

### Post by TransitMan on 2012-03-31
> **2048Megabytes said:**
> I extracted the files to my desktop.  I then opened terminal and typed the following:

cd /home/ubuntu-user/desktop/r8168-8.028.00 

I got the following error code:

bash: cd: /home/ubuntu-user/desktop/r8168-8.028.00: No such file or directory 

If the file is on your desktop, open terminal and type this -
```

cd /Desktop/r8168-8.028.00
Hit enter
Then sudo sh autorun.sh
Hit enter, 
Enter your password and it should install.

```

By typing what you did, it was not needed. Also, when you type cd /Desktop, Desktop must be with a capital D.

---

### Post by 2048Megabytes on 2012-03-31
Thanks for all your help I appreciate it.  I have tried Ubuntu Versions 9.10, 10.04, and 10.10 on this motherboard.  I've also tried Linux Mint Version 11 and they all have problems with it.

I've been using Ubuntu since about 2006.  I've just come to the conclusion that Linux software support for this hardware just isn't there yet.  I will maybe try Linux Mint on it in the year 2013.

Right now I've cloned my Windows 7 64-bit to this drive and that is what I've decided to use for now.  It runs now without any issues.

Thanks agin for your help.

---

