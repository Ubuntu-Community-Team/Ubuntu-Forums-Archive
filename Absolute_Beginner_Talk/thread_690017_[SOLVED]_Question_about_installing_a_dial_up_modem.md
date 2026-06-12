---
title: "[SOLVED] Question about installing a dial up modem"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by fritzgeraldyreyes on 2008-02-07
Is there a way to utilize a driver for a dial up modem (the driver is for windows, the modem connects to the computer via usb) to be used in ubuntu 7.10? I tried to boot the live CD..the screen resolution is good, the sound card is readily functioning..I think everything is ok except for the modem not being detected.

---

### Post by housam on 2008-02-07
You've to install a new driver that works under ubuntu. first scan your modem using this [[COLOR="black"][COLOR="Red"]scanModem tool [/COLOR][/COLOR]]("http://www.linmodems.org/")to inform you about your modem and the suitable driver for it. then download the driver and install it.

---

### Post by spiderbatdad on 2008-02-07
do you know the type of usb modem? chance are fairly good you will be able to use it. internal modems can be much trickier. Still...dial-up with ubuntu usually takes a little work. There are several configuration tools available: pppconfig, wvdial (with gnome-ppp as a graphical frontend). or, kppp. You will most likely need a day's worth (or more) of reading, and trial and error set-up attempts...unless you are really good, or extremely lucky.   scanModem is in synaptic.

---

### Post by fritzgeraldyreyes on 2008-02-07
I have explored the C:\Program Files directory and found a folder named 'conexant' and contains a 'hxfsetup'. I think the specification of this modem is conexant and hsf. I have searched from help.ubuntu.com and found that there is no 'hxf', instead there is 'hsf'..so I think its hsf.

---

### Post by spiderbatdad on 2008-02-07
mmm think ubuntu incorrectly identifies the modem...saw another thread on this earlier...will look for a linky for you.

---

### Post by housam on 2008-02-07
Read in [[COLOR="Red"]this site [/COLOR]]("http://www.conexant.com/products/")you may find what you need.

---

### Post by maniac_X on 2008-02-07
fritzgeraldyreyes,

you're probably going to find that trying to get dial-up to work might be rather frustrating. It's mainly due to lack of drivers that will work in linux in general because most modem drivers nowadays are for "Winmodems" or "Softmodems"(which utilize the Windoze OS for part of thier funtionality. There is also a serious lack of availabilty for linux compatible dial-up modems due to dial-up in general dieing out being that it's old tech.

You didn't mention what type of modem you had but most people who are stuck with dial-up(i just got cable recently myself so I know where you are coming from:() seem to have better luck with "external serial modems" that connect to the com port if your computer has one.

I myself have 2 'puters currently running Ubuntu. One had zero issues with the internal modem because it was an older modem and seems to be recognized easily in Ubuntu. The other 'puter's modem was a big source of frustration even though it was from the same company(Zoom) but was just a few years newer. The frustration almost turned me away from linux. Ended up it was a Conexant chipset modem that required purchase of a driver to get full use of it. The driver would have cost more than my final solution. I ended up getting a external Actiontec serial/usb modem(model EX560KLU) for about $15US and got my internet situation fixed. I just installed Gnome PPP and configured the modem properties with my ISP info and I was off and running.

Post back with more specific info on your modem if possible. The tool that housam linked to will help in that respect.

good luck

---

### Post by Jalke on 2008-02-07
Talking about dial-up modems: I've been using a Sierra Wireles 595 AirCard.  I got it working after a bit of reading up and tinkering.  Worked great for a number of months.  However, for some reason it stopped working a couple of days ago.  I just don't know how to get it going again.  

It won't detect the modem for some reason.  When I type "lsusb" I can see it connected to the usb port.  However, using the command "sudo wvdialconf /etc/wvdial.conf" the modem isn't detected.  
There's no /dev/modem or /dev/modem/tty0 anymore (which was the original location).  I think it has to do with this, but I'm not sure, let alone how to fix it.  How can I find out the location of the modem? Or how can I assign one, if that's the problem?  The output of "dmesg" shows no reference to the modem.

Any ideas?  Thanks a lot.

Edit: Ok, I guess my 595 card isn't dial-up.  But I've heard that setting one of these up is similar to setting up a dial-up modem.
Edit2: On second thoughts, this might not be the best place to post this question - I think I'll be kind of hijacking the thread then.  Sorry, I'll move it [http://ubuntuforums.org/showthread.php?p=4285292#post4285292]("http://ubuntuforums.org/showthread.php?p=4285292#post4285292")

---

### Post by spiderbatdad on 2008-02-07
grrr can't find it but take a look at this:[http://direct2dell.com/one2one/archive/2007/07/17/21325.aspx](http://direct2dell.com/one2one/archive/2007/07/17/21325.aspx)

---

### Post by maniac_X on 2008-02-07
> **fritzgeraldyreyes said:**
> I have explored the C:\Program Files directory and found a folder named 'conexant' and contains a 'hxfsetup'. I think the specification of this modem is conexant and hsf. I have searched from help.ubuntu.com and found that there is no 'hxf', instead there is 'hsf'..so I think its hsf.

Conexant made "HSF" and "HCF" modems as well as others. HSF is commonly referred to as "softmodem", HCF is "controllerless" but this can also be misleading because some Conexant chipped HCF modems do have controllers on the board. I think it just depends on the end manufacturer of the modem.

---

### Post by fritzgeraldyreyes on 2008-02-09
This is the info on my modem:

D-Link
DU-562M
v.92 56K Data/Fax USB Modem

Thanks for your replies..I'll post back when I got it fixed...

---

### Post by Bartender on 2008-02-09
maniac -
Did you mean the Actiontec EX560LKU, not KLU?
I don't mean to be anal about this, but I'm keeping a list of modems that work and want to make sure.  Googling only finds LKU model...

---

### Post by fritzgeraldyreyes on 2008-02-16
I've used this file:

[http://linux.dell.com/files/ubuntu/modem-drivers/hsf/hsfmodem_7.60.00.18oem_i386.deb](http://linux.dell.com/files/ubuntu/modem-drivers/hsf/hsfmodem_7.60.00.18oem_i386.deb)

opened it, and my dial-up modem worked..I even used that modem to connect to the internet and to reply this post..thanks for the help everyone..

---

