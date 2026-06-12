---
title: "Configuring Network Card with Command Line"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by Brendantb on 2007-03-20
Hi, 

I have just completed a command line installation of Xubuntu, and unfortunately didn't configure the card during the installation. (The card is pcmcia, and so is the cdrom drive.) 

Can I now use the command line to set up the card, or even set up an ethernet network, so that I can download the latest Xfce packages? The card is a D-link DWL-650, which worked flawlessly with my old Xubuntu installation. I just had to put in the network and WEP key. 

Thanks,

---

### Post by h0ax on 2007-03-21
You're going to look into the iwconfig command section
I would start with iwconfig --help
wlan0 will probably be the interface of your wireless card, but check to see.

therefore commands would be 
iwconfig wlan0 essid "My Network" key 0123-4567-89

If you ever want to know how to use a command - do man name_of_command
example:
```

man iwconfig

```

---

### Post by ac7ss on 2007-03-24
I have created a handy script to do all the wifi handling. (scans the airspace, you select a connection, it connects and gets dhcp)

```

#! /bin/sh
# New and improved WiFi scan and connect

ctf=/tmp/connect.$$

trap "exit 1"	HUP INT PIPE QUIT TERM
trap "rm -f $ctf" exit

echo '\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n'
	clear
	echo "Utility for connecting to wifi networks.\n"
if [ $1 ] ;then

#	Command line may accept an interface name, otherwise it will scan for an active interface.
	
	interf="$1"
else	

#	This will set it up with the installed IEEE 802.11 device. 

	interf=`iwconfig 2> /dev/null | grep "IEEE 802.11" | sed 's/ *IEEE.*//'`
	
fi	

#	Display interface.

printf "Active interface: -%s-\n\n" "$interf"

#	If there is an interface present:

if [ "$interf" ]; then

#	List available networks into file for a menu

	iwlist $interf scan | grep 'Cell\|Mode:\|ESSID\|key:off\|Signal'|tac |sed -n '/Encry/,+4 p' |tac | sed 's/ - Addr.*//;s/.*Cell/Cell/; s/.*ESSID/ID/; s/.*Sig/Sig/; s/.*Mode:/Mode:/; s/\/153.*level:/\//; s/\/153//' |grep 'Cell\|ID\|Mode:\|Signal' >$ctf

#	Re-Format menu for ease of reading.

	cat $ctf |sed   '/Cell/N; s/\n/\t/' |sed   '/Cell/N; s/\n/\t/' |sed  '/Cell/N; s/\n/\t/; s/ID://; s/Signal level/SNR/' >$ctf
	
#	Display menu:
	
	cat $ctf
	
	echo '\nCurrent:'

#	Show current configuration
#	First the wireless portion

	iwconfig $interf|sed -n 's/.*ESSID/ ID/; s/Nickname:.*//;s/.*Link/ Link/; s/Signal.*//; /ID\|Link/ p '|sed -n '/ID/ h;/92/ H ;x ;s/\n/\t/;/\/92/p'
	
#	Then the IP

	ifconfig $interf| sed -n 's/.*inet addr/ IP/;s/Bcast.*//;/IP/ p'
	
#	Query for selection

	echo '\nEnter Cell # (both digits) Return to exit'
	read selection
	echo ""

#	Branch to do nothing unless there is a selection.

	if [ "$selection" ] ; then
	
#	Check for valid selection

		if grep "Cell $selection" $ctf > /dev/null ; then 
		
#	Set ESSID

			iwconfig $interf essid "`grep "Cell $selection" $ctf |sed 's/.*\t\"//1; s/\"\t.*//'`"
			
#	Set Mode (Managed|Ad-Hoc)

			iwconfig $interf mode `grep "Cell $selection" $ctf |sed 's/.*Mode://; s/\tSNR.*//; s/Master/Managed/'`
			
#	Run dhclient

			dhclient $interf
			
#	Show off new settings
		
			echo '\nNew:'
			iwconfig $interf| grep 'ESSID\|Link' | sed 's/.*ESSID/ ID/;s/.*Link/ Link/'
			ifconfig $interf| sed -n 's/.*inet addr/ IP/;s/Bcast.*//;/IP/ p'	
		fi
	fi
	
#	cleanup
	rm $ctf
else
	echo ""
fi
```

---

### Post by ac7ss on 2007-03-24
Forgot, you must either do this sudo or:

create a wifi group,
chgrp wifi /sbin/dhclient* /sbin/iw*
chmod o-x /sbin/dhclient* /sbin/iw*
chmod u+s /sbin/dhclient* /sbin/iw*
add yourself to the wifi group
re-login

be very careful with the chmod u+s, you must do o-x otherwise you have a GAPING security hole.

Best not to merely add yourself to the root group, that would be BAD.

---

