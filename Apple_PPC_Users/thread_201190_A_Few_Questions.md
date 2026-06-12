---
title: "A Few Questions"
date: 2006-06-21
forum: Apple PPC Users
---

### Post by ismhackett on 2006-06-21
I am brand new *(read: I have no idea what I am doing, but want to learn)* to Ubuntu (or any type of Linux, for that matter) and have two questions:

1. I am running Ubuntu 6.06 on a 15inch 1.33Ghz Al. Powerbook [v. PowerBook5,4]  with Airport Extreme [404.2 (3.90.34.0.p16)] and cannot get the Airport card to work using Networking. Any thoughts? I looked around the baords here for a while, but I'm simply lost. The Ethernet cable works as long as my Powerbook is plugged into it when I boot Linux.

2. Any time I open an "Administrative" application in Ubuntu, the app tries to launch, then doesn't. I don't know how to fix that.

Sorry, but again, I am in uncharted waters here....

stephen

---

### Post by jsonder on 2006-06-21
[QUOTE=ismhackett]I am brand new *(read: I have no idea what I am doing, but want to learn)* to Ubuntu (or any type of Linux, for that matter) and have two questions:

1. I am running Ubuntu 6.06 on a 15inch 1.33Ghz Al. Powerbook [v. PowerBook5,4]  with Airport Extreme [404.2 (3.90.34.0.p16)] and cannot get the Airport card to work using Networking. Any thoughts? I looked around the baords here for a while, but I'm simply lost. The Ethernet cable works as long as my Powerbook is plugged into it when I boot Linux.

2. Any time I open an "Administrative" application in Ubuntu, the app tries to launch, then doesn't. I don't know how to fix that.

Sorry, but again, I am in uncharted waters here....

stephen[/QUOTE]

I never managed to install 6.06.06 due to partitioning problems, had to go back to the dapper beta and upgrades.

You should get a request for permission (password for the first user, i.e., the user when installing the OS).   If you aren't getting that, you can "liberate" the root user as follows:

username@ubuntu:~$ sudo passwd root
Password:  {here you put in the first user password} 
Enter new UNIX password:  {enter the word you want as the root password}
Retype new UNIX password: {re-enter the password for root}
passwd: password updated sucessfully  {if you did the previous steps OK}
username@ubuntu:~$ su
Password: {enter the root password}
root@ubuntu:/home/username#


That leaves you set to issue the command you need.  If you figured out that you really wanted to do this with the gui, exit and go click on System and then click on Administration, and then click on Login Window.  Once there, click on the security tab and change the setup to let root log in (no need for any remote login). then log out as user and log in as root.

I can't help you with airport.

John

---

### Post by robino on 2006-06-21
[QUOTE=ismhackett]
1. I am running Ubuntu 6.06 on a 15inch 1.33Ghz Al. Powerbook [v. PowerBook5,4]  with Airport Extreme [404.2 (3.90.34.0.p16)] and cannot get the Airport card to work using Networking. Any thoughts? I looked around the baords here for a while, but I'm simply lost. [/QUOTE]


Hi, I have been looking around for a while too, and found the following solution to make your Airport Extreme work. Enabling your wireless should be fairly simple by now. Basically, the driver is *already* loaded in Ubuntu Dapper. You only need to load the Firmware.

You enable the driver by loading the right Firmware. The following code did the trick for me, according to the [HowTo]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#head-34d552a556ad5be07dbae4bafb73a6125139c9d8") on the Ubuntu Wiki.

```
 
sudo apt-get install bcm43xx-fwcutter
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
```

That's all to enable Airport Extreme in Dapper...

Then unload and reload the driver by ```
modprobe -r bcm43xx
modprobe bcm43xx
```

And a simple ```
sudo ifconfig eth1 up
```

makes your driver work, ie go up...

If not the  [HowTo bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#head-34d552a556ad5be07dbae4bafb73a6125139c9d8") on the Ubuntu Wiki should give you further guidelines.

Please let know if this worked for you.

---

### Post by ismhackett on 2006-06-21
Awesome. Thanks so much for the help. I know where to ask now!

stephen

---

### Post by Viserys on 2006-06-21
Hi there.
If you have problems with Airport later after installing the firmware, try the following steps:

"iwlist eth1 scan" - Makes sure it can see networks
"iwconfig eth1 essid (YOUR NETWORK NAME HERE)" - Forcibly connect yourself to the proper network
"dhclient eth1" - Grab an IP, etc, with DHCP from your router.

If you are sure you're connected wireless, but internet isn't working (this plagued a friend and I for a week), you need to disable the builtin firewall using the 'iptables' command, as well as remove firewall initialization from the boot scripts. I don't remember which two files it is. :(

---

