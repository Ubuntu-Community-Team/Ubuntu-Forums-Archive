---
title: "Help:  MacBook Pro - Ubuntu Dual Boot Wiki Confusing"
date: 2008-04-27
forum: Apple Hardware Users
---

### Post by linuxmonkey on 2008-04-27
I followed the wiki below for my MacBook Pro.

[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

I followed the steps under "Preparing to Install Ubuntu alongside OS X (Dual Boot)"

At step #9, it says "9. Follow Ubuntu installation instructions from here."

The next section is titled "Ubuntu Installation (Dual Boot)" but it goes thru the process of repartitioning and installing AGAIN.  I found this odd, so I tried to restart and boot under Ubuntu to see what happens.  When I chose Ubuntu in the rEFIt menu, it went to the terminal screen.  It then said something along the lines of "cannot find boot device".  I then went back to the Wiki and followed the "Ubuntu Installation (Dual Boot)".

I am in the process of doing this now, but I am very confused on why the first set of steps had you partition the drive a certain way then the second set of steps had to partition again and Install again.

Is this an error?  Which should I be doing?  

Thanks in advanced.

---

### Post by cyberdork33 on 2008-04-27
> **linuxmonkey said:**
> I followed the wiki below for my MacBook Pro.

[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

I followed the steps under "Preparing to Install Ubuntu alongside OS X (Dual Boot)"

At step #9, it says "9. Follow Ubuntu installation instructions from here."

The next section is titled "Ubuntu Installation (Dual Boot)" but it goes thru the process of repartitioning and installing AGAIN.  I found this odd, so I tried to restart and boot under Ubuntu to see what happens.  When I chose Ubuntu in the rEFIt menu, it went to the terminal screen.  It then said something along the lines of "cannot find boot device".  I then went back to the Wiki and followed the "Ubuntu Installation (Dual Boot)".

I am in the process of doing this now, but I am very confused on why the first set of steps had you partition the drive a certain way then the second set of steps had to partition again and Install again.

Is this an error?  Which should I be doing?  

Thanks in advanced.
i think you were supposed to pick up on the part after partitioning... idk

anyway your error message is related to your partition table being out of sync. reboot into the refit menu and choose the partition tool. It will ask if you want to sync the partitions.

---

### Post by linuxmonkey on 2008-04-27
> **cyberdork33 said:**
> i think you were supposed to pick up on the part after partitioning... idk

anyway your error message is realted to your partition table being out of sync. reboot into the refit menu and choose the partition tool. It will ask if you want to sync the partitions.

Thanks.  I found a thread regarding the resync issue about an hour or so after I posted this thread.  I was still curious about the confusing steps.

Can you explain why in the first set of steps there is 2 partitions and the second set of steps they have 3 partitions?

Which one is correct?

---

### Post by cyberdork33 on 2008-04-27
> **linuxmonkey said:**
> Thanks.  I found a thread regarding the resync issue about an hour or so after I posted this thread.  I was still curious about the confusing steps.

Can you explain why in the first set of steps there is 2 partitions and the second set of steps they have 3 partitions?

Which one is correct?
both. you are creating a swap partition in the second part.

The esaiest way to do this is to just start the Ubuntu Live CD, run 'gparted' (called partition editor in the menus), and use it to delete the partition(s) after OSX. After that, start the ubuntu installer and choose to install to the largest free space when prompted. It will handle the rest of the partitioning itself.

---

### Post by linuxmonkey on 2008-04-27
> **cyberdork33 said:**
> both. you are creating a swap partition in the second part.

The esaiest way to do this is to just start the Ubuntu Live CD, run 'gparted' (called partition editor in the menus), and use it to delete the partition(s) after OSX. After that, start the ubuntu installer and choose to install to the largest free space when prompted. It will handle the rest of the partitioning itself.

I understand about the swap partition.  What I am referring to is the 1st set of steps says to create a ext3 partition minus 1GB and mount point "/".  Then use the free space to make a 1GB swap partition.

The 2nd set of instructions says to edit the main partition and cut it in 1/2, then set a mount point to "/media/Windows/", then create a partition with the remaining space MINUS 1GB and set the mount point "/".  Then the remaining 1GB is the swap partition.

So one says to create 2 partitions while the other says to create 3 partitions.  Whats the /media/Windows for anyway?

---

### Post by cyberdork33 on 2008-04-27
> **linuxmonkey said:**
> The 2nd set of instructions says to edit the main partition and cut it in 1/2, then set a mount point to "/media/Windows/", then create a partition with the remaining space MINUS 1GB and set the mount point "/".  Then the remaining 1GB is the swap partition.
I would say it is a cut and paste error. if you do not plan on using windows, then you don't need that partition.

---

### Post by linuxmonkey on 2008-04-27
> **cyberdork33 said:**
> I would say it is a cut and paste error. if you do not plan on using windows, then you don't need that partition.

Cool. 
Thanks, thats what I figured.

One last question since you have been very helpful.  Everything pretty much works after install except my WiFi.  The wiki shows a bunch of commands to do in Terminal to get this working, and I did it.  So far the WiFi is working just fine.  Is there an easy way to copy/paste a list of terminal commands and run it, or do I have to copy/paste each line as its needed?  Also, I have NO idea what the commands mean, like sudo, sed, and svn.  Is there a "Dummies Guide" to terminal commands like this that explains whats going on?

Here is the commands for getting the WiFi to work:

[I]

sudo apt-get install build-essential subversion automake autoconf
svn co [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk) madwifi -r3403
cd madwifi
make
sudo make install
sudo sed -i~ 's/^exit 0/modprobe ath_pci\nexit 0/' /etc/rc.local
sudo sed -i~ 's/^exit 0/modprobe wlan_scan_sta\nexit 0/' /etc/rc.local
sudo sed -i~ 's/^exit 0/iwpriv ath0 bgscan 0\nexit 0/' /etc/rc.local
[/I]

---

### Post by cyberdork33 on 2008-04-28
> **linuxmonkey said:**
> Is there an easy way to copy/paste a list of terminal commands and run it, or do I have to copy/paste each line as its needed? 
You can make a script script out of them, but you have to know bash to do that.

> **linuxmonkey said:**
> Also, I have NO idea what the commands mean, like sudo, sed, and svn.  Is there a "Dummies Guide" to terminal commands like this that explains whats going on?
[http://linuxcommand.org/](http://linuxcommand.org/)
but for a lot of commands, you can check the man page on your system... just type 'man *command*'


> **linuxmonkey said:**
>  Here is the commands for getting the WiFi to work:[I]

sudo apt-get install build-essential subversion automake autoconf
svn co [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk) madwifi -r3403
cd madwifi
make
sudo make install
sudo sed -i~ 's/^exit 0/modprobe ath_pci\nexit 0/' /etc/rc.local
sudo sed -i~ 's/^exit 0/modprobe wlan_scan_sta\nexit 0/' /etc/rc.local
sudo sed -i~ 's/^exit 0/iwpriv ath0 bgscan 0\nexit 0/' /etc/rc.local
[/I]
I'll run through these real quick.

apt-get is one of the various tools for accessing the Ubuntu repositories and managing software on your system. The first command says to install several packages that are required for compiling, and installs subversion, which is a source code management app.

svn is the subversion commandline utility. the command says to checkout revision 3403 of the madwifi source in the 'trunk'. This is probably all you will ever use it for. it is mainly a tool for developers.

make executes a script in the source directory which calls the various commands needed to properly compile the source. Often, you might precede this with './configure' which is another script that generates the proper makefile for compiling.

sudo is a command that gives you temporary 'root' privileges for the command following. root is the ultimate administrator of a system, and has no security restrictions. It literally means, 'super user do' a related command, su allows you to become a different user on a system. 

the last three commands use the utility 'sed' to add some items to a file (actually a script) /etc/rc.local. I am not familiar with sed myself, but you can checkout some info on it with 'man sed'

---

### Post by linuxmonkey on 2008-04-28
Thanks for the info and link :)

The only issue I have now is seeing my Windows Shares with the File Browser (Nautilus).  I see my windows computer, but none of the shares come up.

I will post another thread for help with this.

Thanks again.

---

### Post by cyberdork33 on 2008-04-28
> **linuxmonkey said:**
> Thanks for the info and link :)

The only issue I have now is seeing my Windows Shares with the File Browser (Nautilus).  I see my windows computer, but none of the shares come up.

I will post another thread for help with this.

Thanks again.nautilus hasn't played nice with samba for awhile. I gave up on it myself. I just mount the shared partition in fstab.

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by linuxmonkey on 2008-04-28
> **cyberdork33 said:**
> nautilus hasn't played nice with samba for awhile. I gave up on it myself. I just mount the shared partition in fstab.

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

Thanks.  I read about that yesterday, but I was hoping for a way to connect to shares via a GUI.  Im new with the terminal stuff, and its sort of over my head.

---

### Post by cyberdork33 on 2008-04-28
> **linuxmonkey said:**
> Thanks.  I read about that yesterday, but I was hoping for a way to connect to shares via a GUI.  Im new with the terminal stuff, and its sort of over my head.
might as well jump in. You will be using the terminal quite a bit in linux. /etc/fstab is the file that contains the locations that you want to "mount" as part of your filesystem automatically on startup. it is one of the most basic config files on your system. (Actually, you can create an fstab file in OSX and it will work there too ;) )

---

