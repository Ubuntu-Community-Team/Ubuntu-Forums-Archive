---
title: "FTP and HTTP"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by cranshinibon on 2007-07-05
So far so good with my noobness of linux lol i do however have a few questions

what are the different mount commands for cd-rom, dvd-rom, dvd r/rw, and USB devices

i have gFTP installed but I don't know what to plug in to configure it nor how to add users or have others have access to it. when i type the ftp command it says not connected, does anyone know how to set up the FTP over gFTP?

Also, how do you setup, start and test if a HTTP server is running correctly. I read through the tutorial but I'm still having a bit of trouble.

---

### Post by dwanders on 2007-07-05
>>> what are the different mount commands for cd-rom, dvd-rom, dvd r/rw, and USB devices
All mine in FIesty Auto mount when I plug them in. Then they are available in /media/...
If something does not mount, you need to know what the device is, and where its mount point is, so for a normal cd-rom it could be:

mount /dev/hdc /medit/cdrom
if /dev/hdc is your cdrom & the folder /media/cdrom exists

>>> i have gFTP installed but I don't know what to plug in to configure it nor how to add users or have others have access to it. when i type the ftp command it says not connected, does anyone know how to set up the FTP over gFTP?

gFtp is a client for accessing ftp servers. Point it to your ftp server and you should be albe to login to it with the correct information. If your trying to set up your computer as an FTP server, you need to install one of the ftp servers available in Add/Remove like GProFTPD

>>> Also, how do you setup, start and test if a HTTP server is running correctly. I read through the tutorial but I'm still having a bit of trouble.

If you have installed and set up Apache (the standard web server for Ubutnu) you should be able to open a web browser and goto [http://localhost](http://localhost).

---

### Post by cranshinibon on 2007-07-05
i can't install gProftpd bc of the following error and i cant figure out what to do to fix it.

Cannot install 'gproftpd'

This application conflicts with other installed software. To install 'gproftpd' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

---

### Post by dwanders on 2007-07-05
I would not know why you cannot install GProDFTPd (cause I cannot tell what its conflicting with =) But check out the remainder of this post:

[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

In section B - the writer goes on to show you how to configure the server without GProFTPd for a more secure server set up. It is a bit more intimidating, but should get you where you need to be.

---

### Post by Raineer on 2007-07-05
For an FTP server I recommend "vsftpd", that is the one I use and it works beautifully, very simple to setup too.

Just do
```
sudo apt-get install vsftpd
``` and go to town with that puppy

---

### Post by cranshinibon on 2007-07-05
how do you configre csftpd...i forgot that i did install it but i cant figure out how to configure it or log into it

---

### Post by Raineer on 2007-07-05
I used [this]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup") guide.  The guide is written for Redhat but easy enough to understand for Ubuntu. You just need to apt-get it, edit the configuration to your liking, then sudo /etc/init.d/vsftpd start

---

### Post by dwanders on 2007-07-05
That may be what causing your original problem. You should only have one ftpd server running at a time (unless your really going to get into it and set up the servers on different ports - way more than I am sure you want to get into to though). 

I also like vsftpd, very nice, pretty easy once you get the config file figured out. 

I would do one of the following:

To keep it really simple:
sudo apt-get remove csftpd  <-hopefully this is what's stopping the install of gproftpd
sudo apt-get install proftpd gproftpd
and use the GUI gproftpd to configure your server. 

OR

If you still cannot get that going, then 
sudo apt-get remove csftpd
sudo apt-get remove proftpd
Make sure these all get removed and there are no other FTPd's installed
sudo apt-get install vsftpd
to configure it modify the file /etc/vsftpd.conf - read through it, it is pretty self explanatory.

let us know how it goes.

---

