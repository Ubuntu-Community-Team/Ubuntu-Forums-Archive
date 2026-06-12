---
title: "maya ple in linux?"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by waxfactor2nd on 2006-10-27
hi ive just downloaded maya personal learners edition for windows, (a exe) but i use ubuntu (dapper), so how can i install it, i know it aint gonna be too easy but ive tried wine, it shuts down when i start it, and my vmware is ****** up, dont know how to fix it, anyone knows  how i get it to run in ubuntu??

---

### Post by bulldog on 2006-10-27
Well you mentioned two methods already.

One of them should do,I should go for VMware though.

What's wrong with your vmware anyway?

---

### Post by waxfactor2nd on 2006-10-27
well as i said wine shuts down (that was what i wanted to use) and my vmware is a real pain in the ***, ive followed many tutorials on how to remove it and install it but it just got worse, so i guess ill go for wine, but when i install and it comes to where i usually press next it shuts down, how can i fix it and make it work??

---

### Post by bulldog on 2006-10-27
> **waxfactor2nd said:**
> well as i said wine shuts down (that was what i wanted to use) and my vmware is a real pain in the ***, ive followed many tutorials on how to remove it and install it but it just got worse, so i guess ill go for wine, but when i install and it comes to where i usually press next it shuts down, how can i fix it and make it work??

Sorry,have no knowledge about wine,never installed or used it.

---

### Post by waxfactor2nd on 2006-10-27
damn do you know any other way?? and does anyone els know how to fix it??

---

### Post by waxfactor2nd on 2006-10-27
anyone???

---

### Post by waxfactor2nd on 2006-10-27
plz someone help

---

### Post by bulldog on 2006-10-27
I use vmware to do windows stuff

I used this Howto to install and it works perfect.

[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

Remember if you get a new kernel or a kernel update you have to reconfigure vmware.
That's simply done to type vmware in your terminal.
You get a line which you have to use with sudo.

If you have vmware installed just type vmware in your terminal and see what it has to tell you.

---

### Post by waxfactor2nd on 2006-10-27
this is what i get then:

hackerdudepremium@computer:~$ sudo /usr/bin/vmware-config.pl Password:
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

You must read and accept the End User License Agreement to continue.
Press enter to display it.

/usr/share/doc/vmware-player/EULA: No such file or directory

Do you accept? (yes/no) y

Thank you.

Configuring fallback GTK+ 2.4 libraries.

Unable to open /usr/lib/vmware-player/libconf/etc/pango/pangorc
Execution aborted.

---

### Post by bulldog on 2006-10-27
In /usr/bin is a uninstall utility for vmware.

Find it and uninstall [if necessary]your vmware and install it again with my Howto.

[but I think it's not installed completely]

Oh and download the VMware server and not the player.

And another question,which Ubuntu do you use?

---

### Post by waxfactor2nd on 2006-10-27
In /usr/bin is a uninstall utility for vmware.

Find it and uninstall [if necessary]your vmware and install it again with my Howto.

[but I think it's not installed completely]

Oh and download the VMware server and not the player.

And another question,which Ubuntu do you use?.

i get this when i remove it: hackerdudepremium@computer:~$ sudo /usr/bin/vmware-uninstall.pl
Uninstalling the tar installation of VMware Server.

Stopping internet superserver: xinetd.
Starting internet superserver: xinetd.
The removal of VMware Server 1.0.1 build-29996 for Linux completed
successfully. Thank you for having tried this software.

hackerdudepremium@computer:~$


and then i installed it again and then it says this:

hackerdudepremium@computer:~$ sudo apt-get install linux-headers-`uname -r` build-essential xinetd
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.15-27-386 is already the newest version.
build-essential is already the newest version.
xinetd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.248.0/255.255.255.0 appears to be unused.

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.99.0/255.255.255.0 appears to be unused.

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
VMware Player is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
hackerdudepremium@computer:~$

---

### Post by waxfactor2nd on 2006-10-27
and when i run that config i get this:

hackerdudepremium@computer:~$ sudo /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done2
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

You must read and accept the End User License Agreement to continue.
Press enter to display it.

/usr/share/doc/vmware-player/EULA: No such file or directory

Do you accept? (yes/no) y

Thank you.

Configuring fallback GTK+ 2.4 libraries.

Unable to open /usr/lib/vmware-player/libconf/etc/pango/pangorc
Execution aborted.

hackerdudepremium@computer:~$

---

### Post by bulldog on 2006-10-27
What if you type in your terminal```
sudo aptitude dist-upgrade
```

---

### Post by waxfactor2nd on 2006-10-27
then this comes:

hackerdudepremium@computer:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.80.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install
already exists.  Overwrite? [yes] y

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.243.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes] y

yStarting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
VMware Player is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.152.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes]



and it just continues... i know my kernel is fu****

---

### Post by bulldog on 2006-10-27
Just reinstall another kernel,what kind of processor you have?

VMware should install perfectly with the kernel you have,but for some dumb reason it can't

---

### Post by waxfactor2nd on 2006-10-27
oehh i am a very linux noob so how do install a new kerneL??? ive got a amd athlon64 3700+ 2200mhz@3080mhz (without any fans)

---

### Post by bulldog on 2006-10-27
Look at this thread.

[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

This one should do

```
sudo aptitude install linux-k7
```

reboot after the install and choose the new k7 kernel to boot.[should be default]

Then start the Howto from the beginning,with build essentials and linux headers and so on.

---

### Post by waxfactor2nd on 2006-10-27
and again i get the looping error:
hackerdudepremium@computer:~$ sudo aptitude install linux-k7
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
hackerdudepremium@computer:~$
hackerdudepremium@computer:~$
hackerdudepremium@computer:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
hackerdudepremium@computer:~$ sudo dpkg --configure -a
Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.55.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install
already exists.  Overwrite? [yes]

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

---

### Post by bulldog on 2006-10-27
What is the outcome of ```
uname -r
```

---

### Post by waxfactor2nd on 2006-10-27
dunno copy pasted from the link of vmware

---

### Post by bulldog on 2006-10-27
I need to know which kernel you use,did you reboot after the kernel update?

Did you install build-essentials and linux-headers?

You're running to fast,I know your previous kernel will not let you install vmware.

To trouble shoot you have to install a new kernel and reboot and then install all the stuff which comes with it.

If that works proper then we go install vmware again.

---

### Post by waxfactor2nd on 2006-10-27
sry now i understood it is 2.6.15-27-386

---

### Post by waxfactor2nd on 2006-10-27
need to know which kernel you use,did you reboot after the kernel update?

Did you install build-essentials and linux-headers?

the kernel is 2.6.15-27-386 now i didnt reboot because it didnt work

dont know what the last to are

---

### Post by bulldog on 2006-10-27
> **waxfactor2nd said:**
> need to know which kernel you use,did you reboot after the kernel update?

Did you install build-essentials and linux-headers?

the kernel is 2.6.15-27-386 now i didnt reboot because it didnt work

dont know what the last to are

Just one thing in a time.

Just install the new kernel and nothing more.```
sudo aptitude install linux-k7
```

[You can quote with the little icon next to the cissor on the right bottom of the posting]

amd athlon64 3700+ 2200mhz@3080mhz (without any fans)

Do you have your processor a 900mghz overclock? 
And what means 'without any fans'

You ask for trouble if it means what I think!!

---

### Post by waxfactor2nd on 2006-10-27
i only wrote that and then i get this error

hackerdudepremium@computer:~$ sudo aptitude install linux-k7
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.


before i did the same thing but wrote the other line

---

### Post by bulldog on 2006-10-27
Then you run ```
sudo dpkg --configure -a
```

---

### Post by waxfactor2nd on 2006-10-27
then i get:

hackerdudepremium@computer:~$ sudo dpkg --configure -a
Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.46.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install
already exists.  Overwrite? [yes] y

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...


which wont stop

---

### Post by bulldog on 2006-10-27
Uninstall vmware again.
If done install the k7 kernel.
Maybe you have to do the reconfigure again but you'll see.


Think your not completely installed vmware causes this issues.
Just get rid of it and if I may suggest something,download vmware again to be sure it's not malfunctioning.

---

### Post by waxfactor2nd on 2006-10-27
kk thx for the help, ill go to sleep now, im to sleepy to think.

---

### Post by Newarz on 2008-05-30
I tried to install Maya PLE in Windows but I'm unable to find the Serial Key. Any idea? I'm wondering if it'll really work with Ubuntu which is what I'm using as my primary OS at present. By the way is Blender at par with Maya PLE? Thanks. 

Newarz

---

