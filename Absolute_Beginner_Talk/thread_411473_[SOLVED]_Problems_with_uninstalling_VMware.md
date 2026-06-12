---
title: "[SOLVED] Problems with uninstalling VMware"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-04-16
Something is wrong when I'm try to uninstall VMware. It is also happening when I'm turning the computer off.  I'm getting a message about vmnet0, vmnet1 and vmnet8. 

Here is what I got from the console:

> Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.80.0/255.255.255.0 appears to be unused.

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

The subnet 172.16.144.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] y 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] y

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Setting up menu (2.1.29) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


How can I get rid of these messages?

---

### Post by zvacet on 2007-04-17
```
cd /usr/bin
```

And when you are there you will see vmware uninstall file.Still in usr/bin run this
```
./vmplayer uninstall.pl
```

I don´t remeber if it is correct file name,so chek it.Second option is to go to the etc and delete vmware folder.

---

### Post by the8thstar on 2007-04-17
I tried your solution and it brought up the splashscreen from VMware. Strangely enough, another screen came up reporting a launching error.

Out of desperation I tried and remove VMWare one last time with the Add/Remove tab from the menu panel... and it worked... finally!

So, no more VMWare, no more problems. Thanks for your help **zvacet**.

---

