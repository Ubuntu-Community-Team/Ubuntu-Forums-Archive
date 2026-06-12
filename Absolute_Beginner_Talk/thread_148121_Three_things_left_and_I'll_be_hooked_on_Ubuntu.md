---
title: "Three things left and I'll be hooked on Ubuntu"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by txinga on 2006-03-21
Hello all. Well, I've successfully installed Ubuntu on a brand new system I just built. Screwed up twice tinkering where I shouldn't have and had to reinstall twice. The last time I made a full backup so if I mess up again it won't be too painful. But now the OS is working well. I am using Ubuntu exclusively on this system and moved my XP box to the living room for a media center. I've been lurking on the forums for a little while to find answers to almost all my questions. Thanks for all the good info here. 
I do have a couple of issues that I would love to get resolved though.

1. I'm a desktop support technician and I would like to be able to temporarily install additional hard drives for troubleshooting, data recovery and so forth. When I put another drive in the system and boot up, Ubuntu can "see" that there's a drive there but I cannot mount it to try and access the data. I get an inaccessible message in the gui. I can reformat them if I so choose. These are FAT32 and NTFS drives I'm working with here. I'm using the System | Administration | Disks way to try and access them.

2. wmv, mpeg and streaming media. 
I can successfully load beep media player via a link on the internet to listen to live streams but when I use streamtuner to load the stream the player just hangs trying to buffer the stream. Also, if I try to record the stream I get the same error, it just keeps trying to buffer the stream.

I have mapped (sorry, windows thinking) mounted a network folder from XP to Ubuntu. When I attempt to play an mpeg movie from the networked (XP) box I receive an error that the path is invalid. Also, I cannot get the media players to browse to the networked box (XP) to add titles to the queue. I can drag and drop mp3s to Rythmbox but it will crash when I click on browse if there is a networked file in the queue.

I cannot get wmv to play at all. I went through the Automatix install and selected everything available. It may be that the files are protected, not a big issue as I don't have a ton of wmv files. I can convert them to ogg or mp3 later.

3. Host name. I have given my Ubuntu install a name during the installation. When I go into the network properties, I see the name there. But my router sees me as unknown.

All in all, this is an excellent distro. There is still a little buginess in it, but it's not like it's my wife trying to learn it and deal with it. She has XP on her's and life is good. Synaptic is by far the most user friendly application installer I have worked with in the Linux world. Automatix is the bomb. I love having a fully functional OS, with all the applications I need, setup and running in a couple of hours. it's like using Norton Ghost at work to build a new PC, almost. :) Anyway, thanks in advance for your help!

txinga

---

### Post by TrendyDark on 2006-03-21
I can help with the first one. The GUI tool provided for mounting doesn't work well. Using the command line is much easier. I'm sorry to say, although, NTFS isn't really supported under Ubuntu. You can mount, but not write anything. 

use the Mounting FAT32 partitions guide at [http://www.ubuntuguide.org](http://www.ubuntuguide.org) for your troubles mounting.

---

### Post by IYY on 2006-03-21
> 1. I'm a desktop support technician and I would like to be able to temporarily install additional hard drives for troubleshooting, data recovery and so forth. When I put another drive in the system and boot up, Ubuntu can "see" that there's a drive there but I cannot mount it to try and access the data. I get an inaccessible message in the gui. I can reformat them if I so choose. These are FAT32 and NTFS drives I'm working with here. I'm using the System | Administration | Disks way to try and access them.

You need to mount the disks on a mountpoint you created in the /media folder (I  assume you've already done that). You should be able to access it now, as root.     If you want to do it through the command line, just use "sudo bash" and look at your files in the terminal (assuming you know your way around the terminal, things like cp, ls, cd). If you want to do it through the GUI, you could run "sudo nautilus --no-desktop". There is also a way to mount the drives so that regular users can access them, but it involves editing /etc/fstab.

> I have mapped (sorry, windows thinking) mounted a network folder from XP to Ubuntu. When I attempt to play an mpeg movie from the networked (XP) box I receive an error that the path is invalid. Also, I cannot get the media players to browse to the networked box (XP) to add titles to the queue. I can drag and drop mp3s to Rythmbox but it will crash when I click on browse if there is a networked file in the queue.

Are you sure you mounted this filesystem, or are you just accessing it through SMB? Try copying an MP3 file to your desktop and playing it from there.

---

### Post by arnieboy on 2006-03-21
[QUOTE=TrendyDark]although, NTFS isn't really supported under Ubuntu. You can mount, but not write anything.[/QUOTE]
This feature is not Ubuntu specific. NTFS writing support is limited on Linux systems as such and is considered to be quite dangerous and hence avoided.

---

### Post by harisund on 2006-03-21
Regarding the host name thing, are you using DHCP? I mean, the router is providing an ip to your machine through the DHCP protocol right? 

In that case, yeah, the router wouldn't see your machine as your machine's host name, but rather something like "Unknown" or nothing at all. 

In order to change that, you will have to go to /etc/dhcp3/dhclient.conf and edit 
send host-name "WhatEverYouWant";

and then try to reacquire your IP address by executing
dhclient eth0 
or whatever your ethernet device is. 

(Remember, you need root previlidges, sudo or whatever)

And do post back if your router can see this host name of yours.

---

### Post by txinga on 2006-03-21
I guess I need to read up a little more on the mounting of additional drives. I tried unsuccessfully three times. 

Yes I'm using SMB to access the networked drive. But the media players cannot access the data from the networked PC. Copying over the file is ok but I want to keep the media files on one pc, the media center one.

The host name thing makes since but I'm actually using eth1 as the onboard nic won't work with Ubuntu (it's nvidia and I can't figure that one out yet.) I installed a PCI nic to handle my network requirements. When I look at my network settings it shows eth1 active and eth0 not configured so I'm a little stumped on the dhclient change. My /etc/dhcp3/dhclient.conf is as follows:

# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}.

---

### Post by txinga on 2006-03-21
ok did this:
Q: How to mount network folders on boot-up, and allow all users to read/write?

   1. Read General Notes
   2. Read How to install Samba Server for files/folders sharing service?
   3.

      e.g. Assumed that network connections have been configured properly
           Network computer's IP: 192.168.0.1
           Network computer's Username: myusername
           Network computer's Password: mypassword
           Shared folder's name: linux
           Local mount folder: /media/sharename

   4.

      sudo mkdir /media/sharename
      sudo gedit /root/.smbcredentials

   5. Insert the following lines into the new file

      username=myusername
      password=mypassword

   6. Save the edited file (sample)
   7.

      sudo chmod 700 /root/.smbcredentials
      sudo cp /etc/fstab /etc/fstab_backup
      sudo gedit /etc/fstab

   8. Append the following line at the end of file

      //192.168.0.1/linux        /media/sharename  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0

   9. Save the edited file 
Then did this:
Q: How to mount network folders on boot-up, and allow all users to read/write?

   1. Read General Notes
   2. Read How to install Samba Server for files/folders sharing service?
   3.

      e.g. Assumed that network connections have been configured properly
           Network computer's IP: 192.168.0.1
           Network computer's Username: myusername
           Network computer's Password: mypassword
           Shared folder's name: linux
           Local mount folder: /media/sharename

   4.

      sudo mkdir /media/sharename
      sudo gedit /root/.smbcredentials

   5. Insert the following lines into the new file

      username=myusername
      password=mypassword

   6. Save the edited file (sample)
   7.

      sudo chmod 700 /root/.smbcredentials
      sudo cp /etc/fstab /etc/fstab_backup
      sudo gedit /etc/fstab

   8. Append the following line at the end of file

      //192.168.0.1/linux        /media/sharename  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0

   9. Save the edited file 

Then did this:
 sudo mount -a

And got this result:
mount: wrong fs type, bad option, bad superblock on //192.168.2.4/MediaShare$,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by harisund on 2006-03-21
Again, on the dhclient thing, in the file that you have pasted you will find a line

#send host-name "andare.fugue.com";

Just remove the '#' from the beginning, and in place of andare.fugue.com type in whatever you want your host name to be !

And then do dhclient eth1

(All as root of course)

---

### Post by txinga on 2006-03-22
Ah... I see it now. I was looking at the file and didn't see eth1 anywhere and it threw me off. Host-name is not nic specific, DUH! Thanks for the help on that one.

---

### Post by Scunizi on 2006-03-22
The Wiki has a couple of good writeups on Mounting drives.  This one helped me get my NTFS partitions mounted and visable on the Desktop [https://wiki.ubuntu.com/AutomaticallyMountPartitions?highlight=%28mount%29](https://wiki.ubuntu.com/AutomaticallyMountPartitions?highlight=%28mount%29)

If you go to the Wiki and search on Mount you'll get a couple of other links for different situations.

---

