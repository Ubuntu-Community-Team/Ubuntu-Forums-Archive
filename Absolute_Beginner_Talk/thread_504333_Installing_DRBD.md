---
title: "Installing DRBD"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by januka on 2007-07-19
HI

I'm using Ubuntu 7.04 Desktop version. I tried to install DRBD. and following errors occurred during the installation..

fist i did     apt-get install drbd0.7-module-source     worked fine 
then          m-a a-i drbd0.7-module-source

"/usr/share/modass/overrides/drbd0.7-module-source" build KVERS=2.6.20-15-server KSRC=/lib/modules/2.6.20-15-server/build KDREV=2.6.20-15.27 kdist_image
find: /usr/src/modules/drbd0.7*: No such file or directory   

Can anybody Please tell the required steps to install it properly.....
Thank you.

---

### Post by straps on 2007-07-19
I've experienced errors too installing it as a module...try installing it from sources...I have used this script with success (execute *sudo -s* before); execute it at your own risk :)

```

	apt-get -y install flex build-essential linux-headers-`uname -r`
	wget http://oss.linbit.com/drbd/8.0/drbd-8.0.3.tar.gz
	tar xzvf drbd-8.0.3.tar.gz
	cd drbd-8.0.3
	make all && make install

	cd ..
	update-rc.d drbd defaults 70
	modprobe drbd
	cp /etc/drbd.conf /etc/drbd.conf.orig

        echo "Insert the correct Name-IP associations in /etc/hosts" && read
	pico /etc/hosts

        echo "Configure drbd.conf properly" && read
	pico /etc/drbd.conf

        echo "Create drbd mount directories and update /etc/fstab" && read
        echo "From 8.0 versione meta-data have to be manually created"
        echo "ex: drbdadm create-md drbd-device-name" && read

        echo "Press Enter to start drbd" && read
	/etc/init.d/drbd start
	cat /proc/drbd
	drbdadm -- --overwrite-data-of-peer primary all

```

---

