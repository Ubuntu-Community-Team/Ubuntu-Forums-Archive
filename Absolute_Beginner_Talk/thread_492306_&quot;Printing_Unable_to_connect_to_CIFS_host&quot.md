---
title: "&quot;Printing: Unable to connect to CIFS host&quot; error"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by bobmorris on 2007-07-04
No matter what I do, I get "Printing: Unable to connect to CIFS host, will retry in 60 seconds..." as an error when trying to do New Printer for a printer on an XP box. That printer had worked before on Ubuntu..

I can ping the Windows box

Samba is installed

Printer is shared from Windows, sharename BrotherH

[http://ubuntuforums.org/showthread.php?t=32190](http://ubuntuforums.org/showthread.php?t=32190) says to put in IP address of Windows box for Host, BrotherH for Name, and Ubuntu username/password. I've tried this and every other configuration I can think of yet still get this error.

Any ideas?

(The Ubuntu (7.04) computer has been weird since a power outage. Something got bonked. Upon restarting,. it loses the 1280x1024 video and only displays at 640x480 until I "sudo dpkg-reconfigure -phigh xserver-xorg"  plus it takes about 4 minutes to boot. It's dual boot with XP on another computer than the printer.)

---

### Post by asmcos on 2007-08-23
maybe you need insmod cifs.ko.

---

### Post by John Harrington on 2007-08-26
I have the same problem as Bobmorris.  Printing used to work under Edgy.  I can't remember whether it stopped working when I upgraded to Feisty, but it hasn't worked for a while.  When I enter "sudo insmod cifs.ko" I get the message:

insmod: can't read 'cifs.ko': No such file or directory

I can browse Windows fileshares using samba in Nautilus and mount them.  However, I have noticed that name resolution doesn't work as it used to under Edgy, and I now have to use IP addresses.  I reset the printer properties so it uses the IP address of the windows computer rather than the Windows name as previously  (i.e., in my case, smb://192.168.1.3/Printer), but I still get the message about being unable to connect to CIFS host.

I have samba, samba-common, smbclient and libsmbclient installed.

Here's the content of /var/log/cups/error_log when I try to print  (kitchen computer is the Ubuntu computer from which I'm trying to print..  Its IP address is 192.168.1.2, but I don't know where to set that.):

E [26/Aug/2007:07:39:11 -0400] Unable to find IP address for server name "kitchen computer"!
E [26/Aug/2007:15:25:08 -0400] Creating missing directory "/var/run/cups/certs"
E [26/Aug/2007:15:25:08 -0400] Unable to find IP address for server name "kitchen computer"!
E [26/Aug/2007:19:40:24 -0400] Unable to find IP address for server name "kitchen computer"!
E [26/Aug/2007:20:08:57 -0400] [Job 66] Unable to connect to CIFS host, will retry in 60 seconds...

I'd appreciate any help anybody could give me to fix this problem as well as any explanation about what's going on.  thanks.

---

### Post by John Harrington on 2007-08-27
Well, I solved my own problem by deleting the printer and adding it again in the CUPS browser interface, [http://localhost:631/](http://localhost:631/)   Apparently when I was trying to add the printer in gnome-cups-add, I was entering smb://192.168.1.3 for the host, when I should simply have entered 192.168.1.3

---

