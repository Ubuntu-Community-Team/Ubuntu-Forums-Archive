---
title: "Installing iSeriesAccess-5.4.0-1.6.i386.rpm on Lubuntu 11.10 on ASUS EB1007"
date: 2012-01-31
forum: Asus Ubuntu Support (CLOSED)
---

### Post by gypsumwolf on 2012-01-31
Instructions on how to make a lightweight Linux terminal for the AS400.

-
Specific Software: iSeriesAccess-5.4.0-1.6.i386.rpm on Lubuntu 11.10 32-bit

Specific hardware: ASUS EB1007

Note: If the web-filter blocks internet access, open a Web browser and sign in.
	-> Open a terminal and run: chromium-browser

-
Index

1...........ASUS EB1007 Booting from USB

2...........Installing iSeriesAccess-5.4.0-1.6.i386.rpm on Lubuntu 11.10 32-bit

3...........Extras you will want to Install/Configure/Hostname/Script

4...........HOW TO RE-IMAGE THE ASUS EB1007

5...........Wifi and LAN connections

6...........Join Windows Domain

7...........A few BASH commands you may want to reference

8...........Fixing APT GPG errors

9...........STATIC Information

10...........Numlock On at Startup

====================================================================
====================================================================
1. ASUS EB1007 Booting from USB
====================================================================
====================================================================

1. On boot, hit the F2 key.

2. Once you are in BIOS, go to the BOOT section.

3. Select 'Hard Disk Drives'.

4. In the hard drives list, move the USB device to the top of the list.

5. Save and exit BIOS (F10).

====================================================================
====================================================================
2. Installing iSeriesAccess-5.4.0-1.6.i386.rpm on Lubuntu 11.10 32-bit.
====================================================================
====================================================================

sudo -i

apt-get install alien libmotif4 libxaw7 libstdc++5

alien -i iSeriesAccess-*****.rpm -cv

ln -sf /usr/lib/libXm.so.4 /usr/lib/libXm.so.3
ln -s /opt/ibm/iSeriesAccess/lib/libcwbcore.so /usr/lib/libcwbcore.so
ln -s /opt/ibm/iSeriesAccess/lib/libcwbodbc.so /usr/lib/libcwbodbc.so
ln -s /opt/ibm/iSeriesAccess/lib/libcwbodbcs.so /usr/lib/libcwbodbcs.so
ln -s /opt/ibm/iSeriesAccess/lib/libcwbrc.so /usr/lib/libcwbrc.so

local-gen en_US

------------------------------------------------
Run the program: (include full path)

/opt/ibm/iSeriesAccess/bin/ibm5250 -LANGID en_us (Enter Host name here.)
-------------------------------------------------

====================================================================
====================================================================
3. Extras you will want to Install/Configure/Hostname/Script.
====================================================================
====================================================================

#Change the hostname in both:
sudo nano /etc/hostname
sudo nano /etc/hosts

--
sudo apt-get install docker

sudo nano /etc/xdg/openbox/autostart

	Add: sleep 5 && /opt/ibm/iSeriesAccess/bin/ibm5250 -LANGID en_US (HOST) &
	Add: docker &

sudo nano /etc/xdg/openbox/menu.xml (Look it up on google).

nano ~/scripts/(custom scripts)

	Create: /home/administrator/scripts/rmprofile.sh (Run this from /etc/xdg/openbox/autostart):

		Add: rm /home/(admin_user)/.iSeriesAccess/cwb*

	Create: /home/administrator/scripts/5250.sh (Run this from /etc/xdg/openbox/menu.xml):

		Add: /opt/ibm/iSeriesAccess/bin/ibm5250 -LANGID en_US (HOST)

	Note: Do 'chmod a+x (filename)' for both of these scripts.

====================================================================
====================================================================
4. HOW TO RE-IMAGE THE ASUS EB1007
====================================================================
====================================================================

NOTE: Most of the time, when you use "sudo", you will be prompted
to enter the password. (*** for specific company).

1. Use the Acronis image in \\***\***\(image_name.tib).

2. Boot into a Ubuntu-based Live USB.

3. Open a terminal and use the following 2 commands and follow promps if needed.

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update

sudo apt-get install -y boot-repair && boot-repair

4. Reboot Asus EB1007.

5. Next, hide the grub2 menu:

	A. Open a terminal and do this command below: (It will open a editor with the grub file.)

		sudo nano /etc/default/grub

	B. Remove the "#" comment out symbol from this line:

		#GRUB_HIDDEN_TIMEOUT=0

	C. Save your work by pressing "CTRL + O". Exit the editor by pressing "CTRL + X".

	D. Type this command:

		sudo update-grub

	E. Reboot. (Reboot command: sudo shutdown -r now)

====================================================================
====================================================================
5. Wifi and LAN connections:
====================================================================
====================================================================

1. Open terminal.

2. use these commands to load nm-applet.

	sudo -i
	nm-applet &

	exit

3. There will be an network manager in the upper left corner of the screen.

====================================================================
====================================================================
6. Join Windows Domain:
====================================================================
====================================================================

1. Use the terminal to install likewise-open

	sudo apt-get install likewise-open

2. Connect to domain:

	sudo domainjoin-cli join (domainname) (username)

3. If you want to disconnect the domain

	sudo domainjoin-cli leave

====================================================================
====================================================================
7. A few BASH commands you may want to reference:
====================================================================
====================================================================

sudo -i (for root prompt)

sudo shutdown -h now (shutdown computer now)

sudo shutdown -r now (restart computer now)

nano (text editor, more simple than vi)

pkill (kill process)

chromium-browser (if you need to enter mobile + mobile for watchguard)

ifconfig (like MS Widnows ipconfig)

---> Need more? Use Google or ask me.

====================================================================
====================================================================
8. Fixing APT GPG errors:
====================================================================
====================================================================

1. Open a terminal and try ALL of these commands.

	sudo -i
	apt-get clean
	cd /var/lib/apt
	mv lists lists.old
	mkdir -p lists/partial
	apt-get clean
	apt-get update

2. If it does not work, Google it.

====================================================================
====================================================================
9. STATIC information
====================================================================
====================================================================

This was origionally for a specific comapny, fill out accordingly.

IP= x.x.x.x

Subnet= x.x.x.x

Gateway= x.x.x.x

DNS= x.x.x.x, x.x.x.x

====================================================================
====================================================================
10. Numlock On at Startup
====================================================================
====================================================================

sudo apt-get install numlockx

#May not be necessary.
sudo sed -i 's|^exit 0.*$|# Numlock enable\n[ -x /usr/bin/numlockx ] \&\& numlockx on\n\nexit 0|' /etc/rc.local

#Add the line below to /etc/xdg/openbox/autostart
numlockx &

---

