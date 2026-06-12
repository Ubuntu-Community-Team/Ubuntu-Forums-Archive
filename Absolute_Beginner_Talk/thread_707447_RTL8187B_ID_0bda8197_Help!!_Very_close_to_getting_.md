---
title: "RTL8187B ID: 0bda:8197 Help!! Very close to getting wireless"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-02-25
Please go here for RTL8187B (ID:8197) issues!

[http://ubuntuforums.org/showthread.php?t=792092]("http://ubuntuforums.org/showthread.php?t=792092")

---

### Post by jeffus_il on 2008-02-25
Here is someone who claims to have the native driver working with WEP:


[http://briancantin.blogspot.com/2007/11/hacking-rtl8187b-on-linux.html](http://briancantin.blogspot.com/2007/11/hacking-rtl8187b-on-linux.html)

---

### Post by Tom--d on 2008-02-25
Ok, read the last post on that link.

I done that.
This is what it said
```
Easiest way is to use ndiswrapper, if you're not going to use this for security monitoring (Airocrack, etc).

Download the RTL8187B_driver_only from realtek or search google for it. Open up the INF, and look for 
;;****************************************************************************
;; IDs for 98SE/ME/2K/XP
;;****************************************************************************
[Realtek]
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8187&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8189&REV_0200


CHANGE IT TO

;;****************************************************************************
;; IDs for 98SE/ME/2K/XP
;;****************************************************************************
[Realtek]
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8187&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8189&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200

insert the new inf/sys file into ndiswrapper (ndiswrapper -i /location/of/driver)

finish installing the driver with ndiswrapper, and you should be good
```

Now it says:

```
ndiswrapper -l
net8187b : driver installed
              device  (0BDA:8179) present
```

I thoguht I did it then!But sadly not :(

```
If ndiswrapper correctly associates the driver to the wireless adapter, you are now ready to load the driver into memory, and try to establish a network connection. 

Open a Terminal and run the following commands: 

  sudo depmod -a
  sudo modprobe ndiswrapper
  Then, also in a Terminal, check for error messages: 

  tail /var/log/messages
```


when I done this 
```
tail /var/log/messages
```
It comes up with this:

```

tom@Laptop:~$ tail /var/log/messages
Feb 25 17:37:13 Laptop kernel: [ 4020.956000] lo: Disabled Privacy Extensions
Feb 25 17:37:48 Laptop kernel: [ 4050.236000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 25 17:38:13 Laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Feb 25 17:38:30 Laptop kernel: [ 4092.296000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Feb 25 17:38:33 Laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Feb 25 17:38:33 Laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Feb 25 17:38:33 Laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Feb 25 17:46:45 Laptop kernel: [ 4587.608000] usb 2-2: USB disconnect, address 4
Feb 25 17:46:46 Laptop kernel: [ 4588.348000] ndiswrapper: device wlan0 removed
Feb 25 17:52:11 Laptop kernel: [ 4913.148000] usb 2-1: USB disconnect, address 3


```

And when I do
```
 iwconfig
```

it comes up with...
```
lo          no wireless extensions
```

Help..

---

### Post by jordanmthomas on 2008-02-25
I am in NO WAY in the know about ndiswrapper, but I think it's a kernel module you need to load up.
```
sudo modprobe ndiswrapper
```
Does iwconfig show your device after this?


Forgive me if you've already done this.


EDIT
Sorry, reread your last post, and you did it already.

---

### Post by Tom--d on 2008-02-25
yeah I did. 
Says there is no wireless but now it detects the card which is a good thing :)

Just now need to enable the wireless.
Maybe change the .inf file so it sees the wireless.. I don't know how to do that! Need someone to help me :)

---

### Post by Tom--d on 2008-02-25
Anyone?

Please help. Once this is fixed and working through ndiswrapper.. then everyone else can use it!!!

---

### Post by pcweber on 2008-03-06
Hi,
I have tried several measures to get this card up and without any luck whatsoever. My current system uses wep and ad-hoc, and these poorly programmed drivers do not meet any standards whatsoever, there is likewise no support from realtek. Send an e-mail to them and you will probably never receive an answer. After several tries and distributions, I had to go out and buy a USB dongle, with the ralink chip. Ubuntu has a patch that makes the driver work with a couple of minor glitches, the dongle will not automagically come up and modifying the interfaces file doesn't help. It seems that the changes to ad-hoc have to be made prior to ifconfig brings up the dongle, I wrote a small script which gets me over the problem, for now. What the heck it cost me 16€ but has saved me some time.
Good luck.

Phil

---

### Post by kachline on 2008-03-25
Hi All,

I have had success with using this WiFi adapter on my Toshiba laptop. Following are some details and hopefully steps to recreate.....

-- What --
Toshiba A215-S7414
Ubuntu 8.04 x86_64
2.6.24-12-generic kernel
(Pretty much a "fresh install" of 8.04 )


Steps:

```

$ lsusb

```
You should see "0bda:8197 Realtek Semiconductor Corp."


[http://www.datanorth.net/~cuervo/rtl8187b/]("http://www.datanorth.net/~cuervo/rtl8187b/")
Download the "jadams" modified kernel sources.



```

$ sudo apt-get install build-essential

```
Get tools needed to build a kernel module.

```

$ cd Desktop
$ tar -xzvf rtl8187b-modified-jadams-2-1-2008.tar.gz
$ cd rtl8187b-modified-jadams
$ chmod +x ./makedrv
$ sudo ./makedrv

```
Untar and build.
Though there will be warnings, the last message printed should indicate that a ".ko" was built.


```

$ chmod +x wlan0*
$ sudo ./wlan0up

```
This fires up the wireless device. Shortly after this step, you should see the gnome network manager icon start looking for wireless networks. If you click the network manager link in your gnome panel, you should see options about wireless.


-- Using the driver --
Someone else will have to post better instructions for auto-startup, but, if you do the steps above, then, each time you boot your box (or login), in order to startup wireless, you need to...

```

$ cd Desktop
$ cd rtl8187b-modified
$ sudo ./wlan0up

```


Cheers,
   - Mike

---

### Post by mistered39 on 2008-05-16
Sir, trying your instructions but am stuck at:

edv@edv-laptop:~/Desktop$ **cd rtl8187b-modified-jadams**
bash: cd: rtl8187b-modified-jadams: No such file or directory

Am I in the wrong directory? All the steps before this added themselves, but not this one...

---

