---
title: "Need help in Speedtouch usb modem setup"
date: 2005-06-13
forum: Absolute Beginner Talk
---

### Post by silent-red on 2005-06-13
Hi,

Can anybody help me do this. I'm barely a week old using Ubuntu Linux and I want to set up my Speedtouch modem. I have followed the setup guide in linux-usb.org[http://www.linux-usb.org](http://www.linux-usb.org) , the speedtouch modem is a revision 4.0 or silver modem but its not working. I also want to ask what is VCI/VPI and where could I get this numbers. Actually I was guessing the numbers, I've tried 0.35 and 8.35 the default in the guide is 0.00.

---

### Post by silent-red on 2005-06-14
Here's the output when I entered the command
root@localhost /home/usr/Desktop **pppd call speedtch**
-----------------------------

Plugin pppoatm.so loaded
PPPoATM plugin_init
PPPoATM setdevname - remove unwanted options
PPPoATM setdevname _pppoatm - SUCCESS:0.35
connect(0.35) : Address already in use

-------------------------------------------------------------------------

Heres the second time I entered the commmand

-------------------------------------------------------------------------
Plugin pppoatm.so loaded
PPPoATM plugin_init
PPPoATM setdevname - remove unwanted options
PPPoATM setdevname _pppoatm - SUCCESS:0.35
Using interface ppp0
connect: ppp0 <--> 0.35
LCP terminated by peer
Connection terminated



I was really hoping that after I follow the setup and after a reboot the internet will work. 

Thanks.

---

### Post by N'Jal on 2005-06-14
ok just had a look at the linux-usb project to remember how i set up my speed touch, i have the revision 0

I live in brittan so i belive i typed my numbers in like this
0.38

But you will have to consult the table on the linux-usb project website for your numbers

---

### Post by silent-red on 2005-06-14
In my speedtouch usb windows installer, I installed the driver PPPoA 0-35 VCMUX
other driver I tried installing won't work. Thats where I get VPI/VPI id

Are there any other settings that needs to tweaked in the firefox browser, like connection settings.

Thanks

---

### Post by desdinova on 2005-06-14
I set mine up using the software and instructions at [http://speedtouchconf.sourceforge.net](http://speedtouchconf.sourceforge.net)

---

### Post by silent-red on 2005-06-14
What can anyone about this error?

root@localhost:/home/jered/speedtouchconf-06-03-2005 # ./speedtouchconf.sh


************************************************
*                                              *
*       speedtouchconf.sh by Steve Parker      *
*                                              *
*    [http://speedtouchconf.sourceforge.net/](http://speedtouchconf.sourceforge.net/)    *
* based on speedtouch.sourceforge.net project  *
*                                              *
************************************************

If you have any problems with this script, mail me
(steve at steve-parker dot org) with the files
/tmp/speedtouch.txt and /var/log/messages for diagnosis.
Using speedtouch-1.3-sgp
Error: Cannot find gcc.
The kernel speedtch module is loaded. This is not
compatible with the speedtouch usermode driver.
Removing the speedtch module
microcode is rev4fw.zip
  PPP version 2.4.2 okay.
  Linux kernel version 2.6.10 okay.
No USB Bus found!
ERROR:
Some required files are not installed:
gcc
Please install these (from your Linux install media,
or the internet) before you can configure and install
the speedtouch software.
Please check the PATH environment variable, and that you are running
as root. Your PATH variable is currently:
/bin:/sbin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
root@localhost:/home/jered/speedtouchconf-06-03-2005 #

---

### Post by silent-red on 2005-06-15
Thanks for all your help guys!  :smile: 

I'm now using my Ubuntu in posting this message.  :smile: 

The link below is just what I needed to make my internet going, Hope this will help others
[speedtouchconf.sourceforge.net](http://speedtouchconf.sourceforge.net)

---

