---
title: "upgrade broke my netbook"
date: 2011-07-31
forum: Asus Ubuntu Support (CLOSED)
---

### Post by pdc124 on 2011-07-31
ASUS eee 901 , with NBR LTS. Just upgraded to the latest kernel
>  coop@littleCOOP:~$ uname -a 
Linux littleCOOP 2.6.32-33-generic #71-Ubuntu SMP Wed Jul 20 17:30:40 UTC 2011 i686 GNU/Linux

and the machine is broken. 
A number of problems : 
I get the login  screen and the mouseover popups but cant login. Starting a console shows that  ntos_wq is top of the list. 
Ive had to install ndiswrapper to get the wireless card working with WPA 
I disable (Fn-F2) wireless  and reboot and i get the login screen, after a pause it lets me login. But I cant connect to a cabled connection- it gets and address , and then drops the connection. 

Console -> dhclient3 -d eth0 seems to work though.

But the GUI still doesn't respond - very intermittent dropdown menus, GUI that responds unreliably. 

So i have an unusable netbook.

Where to start in sorting it out ?

---

### Post by pdc124 on 2011-08-01
ive removed ndiswrapper but that hasn't really fixed anything 
I still have an unusable GUI 
Top in a console doesn't show any particular process eating all the resources

---

### Post by pdc124 on 2011-08-03
this still isnt working. No GUI at all . How do i  *DOWN*grade a kernel version ?  my /boot/grub/grub.conf doesnt exist any more !

---

### Post by pdc124 on 2011-08-04
so ive downgraded the kernel to > 
 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011 i686 GNU/Linux

AND Ive got my GUI back.
But there are still network connection problems
[LIST]
[*]network manager applet  doesnt connect to the wired network automatically
[*]When i connect manually, it immediately disconnects
[*]but the command line - sudo dhclient eth0  - still works
[*]the wireless card doesn't show up with sudo ifconfig -a , but its there with lspci -RaLink RT2860
[/LIST]

---

### Post by garvinrick4 on 2011-08-04
Should always have the backup kernel to fall back on, have at least two:
[Index of /~kernel-ppa/mainline]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
this above gives you all the kernels in .deb package. Just download the all.deb the headers
and the image and install in that order, double click on each deb package and will install thru ubuntu software center. Or use the sudo dpkg -i (name of package) will also install.

On the wireless is your driver is not a kernel driver I take it:
lspci -k
if not is it in compat-wireless (easy it install) will go look.

---

### Post by garvinrick4 on 2011-08-04
Here is link with chili555 he is about the best with wireless and drivers:
This should do you hopefully. follow his instructions:

[http://ubuntuforums.org/showthread.php?t=1699987](http://ubuntuforums.org/showthread.php?t=1699987)

---

### Post by pdc124 on 2011-08-04
if its a bug ,  is there any value in reporting it ?

---

### Post by pdc124 on 2011-08-07
still struggling 
> relevant lspci -k
        *-network UNCLAIMED
       description: Network controller
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7ff0000-f7ffffff

I downloaded and compiled the latest driver. I put stuff like this in /usr/local/.
>  locate rt2860sta.ko
/lib/modules/2.6.32-25-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/lib/modules/2.6.32-26-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/lib/modules/2.6.32-27-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/lib/modules/2.6.32-28-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/lib/modules/2.6.32-29-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/lib/modules/2.6.32-30-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/lib/modules/2.6.32-31-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/lib/modules/2.6.32-32-generic/kernel/drivers/net/wireless/rt2860sta.ko
/lib/modules/2.6.32-32-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/usr/local/2010_07_16_RT2860_Linux_STA_v2.4.0.0/rt2860sta.ko
/usr/local/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/.rt2860sta.ko.cmd
/usr/local/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/rt2860sta.ko


ive got rt2860 in /etc/modules , so I assume its loading the kernel module.
How do i check which module the card is using  and tell it to use the one that isnt the kernel module ? I tried rmoving it from /etc/modules and then modprobe rt2860 , but it stall says its the kernel version module ( will i get a different message with the  self-compiled one ? )

---

