---
title: "imacG3 modem and xubuntu"
date: 2006-08-26
forum: Apple PPC Users
---

### Post by sersetto on 2006-08-26
Hi.
I have installed the latest release of xubuntu on my imac G3.
It is very fast (compare to OS9 and OSX) and I am very happy about it. 
However the internal modem is not detected. It is my undrstanding (reading other threads in this forum) that this is a kernel issue.
Xubuntu comes with kernel version 2.6.15.7. 
While the fixed (the one detecting the modem) kernel version should be 2.6.15.25.

Are new relesase (in the near future) of Xubuntu coming with the kernel 2.6.15.25 ?
If not how I do compile the kernel to have xubuntu recognize the modem?
1) I download the kernel 2.6.15.25? which file do I have to download?
 After download how I do manually compile the kernel?

2)Is there a way to not download anything and just recompile my kernel (2.6.15.7) "changing" some options (it seems that this was one the solution suggested in the links on [http://www.ubuntuforums.org/showthread.php?t=196327)](http://www.ubuntuforums.org/showthread.php?t=196327)).
But I am not so good to do it with some more detailed instructions :( .

Thank you very much.

---

### Post by beerstim on 2006-08-26
I have the same problem i installed xubuntu on my imac 400 dv and then no modem:( so now i can't use it on the internet at all:(

---

### Post by nkbj on 2006-08-27
You should try installing from the 6.06.1 cdrom. It has the updated kernel.

Regards,
Niels Kristian

---

### Post by beerstim on 2006-08-28
Thats the Cd that I installed with and the modem does not work:(

---

### Post by beerstim on 2006-09-02
U guess on one cares about dial up modems these days but i still need it on my imac  someone please help

---

### Post by Klatoo on 2006-09-04
Yes--I had same problem--googled for hours--no help.  My modem is inside an iMac G3 600 Mhz "graphite" slot loader.  This is my first iMac (somebody gave it to me)--apparently there is a "comm slot" in these iMacs that use an internal serial (rs-232, not USB) connection to modem (this is weird since the iMac has no external serial ports).  It appears to be a hardware modem from what I read elsewhere on the net.  The new Ubuntu 6.06.1 LTS alternate-install CD that I used installs a kernel which does include support for the serial interface used by this modem... but it is compiled as a module, so you need to type:

sudo modprobe pmac_zilog

...in order to load it.  After that, the serial modules show up if you type "lsmod".  Then, I was able to dial-out using this modem as /dev/ttyS0 using the System | Administration | Networking utility (although I am still having trouble connecting with this utility and may try to install Gnome-PPP).  Speaker is silent even though I have it set to loud.  Kppp query was successful--modem responded that it was manufactured by Apple, but am having trouble connecting via Kppp.  I think I'll get the rest figured out from the dial-up howto at:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
By the way, this iMac includes the ATI Rage 128 card which was also prone to the extremely slow Gnome problem which was fixed by commenting out the "load dri" line in /etc/X11/xorg.conf as described elsewhere in these forums.  Almost gave up on Dapper on this machine but think it is working great now.  Hope this helps.

---

### Post by Klatoo on 2006-09-06
Added the line "pmac_zilog" to the /etc/modules file so it loads on boot.  Deactivated ethernet connection under System | Administration | Networking and the modem started connecting fine under Kppp.

---

### Post by sersetto on 2006-09-12
thank you very much Klatoo.
i add the module and used wvdial to configure the modem
everything is fine.
:D

---

### Post by Ptero-4 on 2006-11-17
Does the modem dial out? I ask b/c someone got me an ibook G3 500MHz to install Dapper on it and this ibook uses the pmac_zilog modem, I already added the pmac_zilog module to /etc/modules but when using pon it gets stuck in "EXPECT (OK)" and won't get further than that, in breezy it shows lots of weird stuff and eventually it shows four IP's indicating that it's online.

---

