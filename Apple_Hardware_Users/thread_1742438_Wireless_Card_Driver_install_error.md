---
title: "Wireless Card Driver install error"
date: 2011-04-28
forum: Apple Hardware Users
---

### Post by chico1986 on 2011-04-28
I have MacBook 3,1. I just installed 11.04. When I go to activate the "Broadcom STA wireless driver" I get the message "Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log" When I check the log the message is "2011-04-28 18:38:59,896 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted"

I have had 10.04 on this computer in the past and it worked fine, but this is a fresh install of 11.04. Any suggestions on where to go from here?

If anymore info would be helpful let me know! 

Thank You!

---

### Post by chico1986 on 2011-04-29
Hey Again, So a closer look at the jockey.log and I notice something a few lines up 

"2011-04-28 20:58:05,606 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-04-28 20:58:05,677 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-04-28 20:58:08,985 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-04-28 20:58:08,999 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-04-28 20:58:09,021 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-04-28 20:58:11,431 DEBUG: Shutting down"

It looks like the directory where the drivers should be does not exists  /sys/module/wl/drivers I went looking for it myself and could not find it, where can I get the drivers? Any help would be great.... Thanks!

---

### Post by chico1986 on 2011-04-29
Run
#sudo apt-get update 
#sudo apt-get --reinstall install bcmwl-kernel-source

restart, should be up and running, if not go back and try to activate the driver. ;-)

---

### Post by collisionystm on 2011-04-29
> **chico1986 said:**
> I have MacBook 3,1. I just installed 11.04. When I go to activate the "Broadcom STA wireless driver" I get the message "Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log" When I check the log the message is "2011-04-28 18:38:59,896 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted"

I have had 10.04 on this computer in the past and it worked fine, but this is a fresh install of 11.04. Any suggestions on where to go from here?

If anymore info would be helpful let me know! 

Thank You!


[http://ubuntuforums.org/showthread.php?p=10736018](http://ubuntuforums.org/showthread.php?p=10736018)

I followed the instructions, ran the Additional Drivers app and after a reboot... happy happy.

---

