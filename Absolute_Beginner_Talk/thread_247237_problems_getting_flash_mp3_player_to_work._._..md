---
title: "problems getting flash mp3 player to work. . ."
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by nanamin on 2006-08-30
I recently picked up a Samsung YP-U2JXB mp3 player, and am having problems working with this in linux. When I plug it into a USB port, it disconnects the device shortly after. Here's the output of dmesg:

> [17222217.584000] usb 5-1: new high speed USB device using ehci_hcd and address 4
[17222217.716000] scsi2 : SCSI emulation for USB Mass Storage devices
[17222217.716000] usb-storage: device found at 4
[17222217.716000] usb-storage: waiting for device to settle before scanning
[17222222.940000] usb 5-1: USB disconnect, address 4
[17222222.940000] usb-storage: device scan complete

When I look at this in the gnome device manager, it shows up as "Samsung YP-U2" (or something like that), and then disappears shortly after.

I've tried googling for solutions, asked everyone I know, and even looked for firmware upgrades which might solve some of the problems I'm having with it, but to no avail. Does anyone know why it's disconnecting and how I can stop it? 

Thanks a lot!

---

### Post by taurus on 2006-08-30
I assume it's in fat32 format!!!  Can you try to see if you can mount it by hand from a terminal?

```

sudo mkdir /media/player
sudo mount -t vfat /dev/sda1 /media/player
df -h

```

---

### Post by nanamin on 2006-08-30
I've tried this before. The problem is that /dev/sda1 and so forth don't seem to exist at all. I think it's because it doesn't even see the device as connected. 

Watch:

> sacha@dcrypt:~$ sudo mkdir /media/player
Password:
sacha@dcrypt:~$ sudo mount -t vfat /dev/sda1 /media/player
mount: special device /dev/sda1 does not exist
sacha@dcrypt:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              72G   67G  1.5G  98% /
varrun                252M  132K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  112K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-26-386/volatile
/dev/hdb               76G   70G  1.4G  99% /home/sacha/Desktop/hdb


---

### Post by taurus on 2006-08-30
Replace /dev/sda1 with /dev/sda4!

---

### Post by nanamin on 2006-08-30
Here:

> sacha@dcrypt:~$ sudo mount -t vfat /dev/sda4 /media/player
mount: special device /dev/sda4 does not exist
sacha@dcrypt:~$ ls /dev/sda*
ls: /dev/sda*: No such file or directory


---

### Post by whizbaby on 2006-08-30
My try!
Are you in the group plugdev (by accident you may not)?
If not
sudo adduser YOURUSERNAME plugdev

if yes, here some other device guesses:

/dev/sda (w/o numbers)
/dev/sdb (w and w/o numbers)
/dev/sdd (may be stupid, only because of the '4' in your message, w and w/o numbers)

e.g. a cdrom is usually not /dev/hdc1 but /dev/hdc

---

### Post by nanamin on 2006-08-30
Yes, I'm in plugdev, and there's no sd-anything, even when I just freshly plugged the device in (which is before it disconnects and all that)

When I run ls on /dev, I get rtc, shm, snd. . .as far as that section of the device listing goes.

---

### Post by whizbaby on 2006-08-30
What does

lshal | grep -B6 -A5 amsung

give after having plugged the thing in for a reasonable time(ca. 10 secs)?
Is your stick in
less /proc/bus/usb/devices ?

---

### Post by nanamin on 2006-08-30
When plugged in for around 10 seconds, I get this output:

>   usb_device.speed_bcd = 294912  (0x48000)  (int)
  usb_device.serial = '4002FA7BF02B4E90'  (string)
  usb_device.linux.device_number = 6  (0x6)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.max_power = 500  (0x1f4)  (int)
  usb_device.device_revision_bcd = 256  (0x100)  (int)
  info.product = 'Samsung YP-U2J'  (string)
  usb_device.product = 'Samsung YP-U2J'  (string)
  info.vendor = 'Samsung Electronics Co., Ltd'  (string)
  usb_device.vendor = 'Samsung Electronics Co., Ltd'  (string)
  usb_device.product_id = 20564  (0x5054)  (int)
  usb_device.vendor_id = 1256  (0x4e8)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.device_class = 0  (0x0)  (int)
--
  usb.num_interfaces = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.vendor_id = 1256  (0x4e8)  (int)
  usb.product_id = 20564  (0x5054)  (int)
  usb.vendor = 'Samsung Electronics Co., Ltd'  (string)
  usb.product = 'USB Mass Storage Interface'  (string)
  usb.device_revision_bcd = 256  (0x100)  (int)
  usb.max_power = 500  (0x1f4)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.linux.device_number = 6  (0x6)  (int)


After running that command for a count beyond 10, however, there is no output at all.

What exactly am I looking for in the second command you gave me? Here's the output:

> T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-26-386 ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:09.2
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  7 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=04e8 ProdID=5054 Rev= 1.00
S:  Manufacturer=Samsung 
S:  Product=Samsung YP-U2J  
S:  SerialNumber=4002FA7BF02B4E90
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=  64 Ivl=4096ms

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-26-386 uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:09.1
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-26-386 uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:09.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 3
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-26-386 ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:02.3
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 3
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-26-386 ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:02.2
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms


---

### Post by whizbaby on 2006-08-30
You are looking for your Samsung of course!
/proc/ is updated all the time, so you can see if after lshal lost the connection the system still sees the stick. (if I unplug my stick /proc gets rid of it).
Does it?
(by the way, it's a bad thing that hald looses the connection)

---

### Post by nanamin on 2006-08-30
no, it doesn't :-\

the odd thing is, this does not happen for my 1 gig flash drive (non-mp3 player). that just mounts, even creates a folder on the desktop and so forth.

---

### Post by whizbaby on 2006-08-30
Really weird (my stick is a mp3-player, too)!
In what kind of USB-prt did you plug it? Hub? Front panel?
Does it show any other behaviour when you plug it in one of the ports at the back side directly on the main board?

---

### Post by nanamin on 2006-08-30
Well, I have two USB (1.0) ports in my motherboard, which recognize the device when plugged in, but don't seem to work for any other device. Recently, I got a PCI card which has two more USB (2.0) ports, which work for everything -- except this so far. The mp3 player is for USB 2.0, so I've mostly been using the PCI card, although I believe it's also backwards compatible. I get the same behaviour in all of the ports, nonetheless.

Basically, what happens is the mp3 player will light up, start charging, and say "disconnected" on the screen, though it says "connected" for the brief time before my computer reports it as disconnected. This doesn't happen when Windows XP (on a different machine) is used. I'm pretty sure it's still usable on ubuntu.

I found a similar topic [here]("http://http://www.linuxquestions.org/questions/showthread.php?t=323912"), which went unanswered. Someone suggested a that there wasn't information about the inquirer's device in a database. Could this be the same issue? 

Also, the proper devices don't show up in my /dev directory, even when the device is connected, I believe. Don't know if that information helps any.

---

### Post by whizbaby on 2006-08-30
Let's try another approach.
Shurely your problem is originated in the missing sd* in /dev, but we have to find out where it fails. Plug the stick in wherever you like and wait the ten secs. Then type

dmesg|grep sda      (or sdb or, when not too tired, usb)

this should show us where the system tries to register the device (even after disconnecting it).
Next

lsmod|grep usb

to verify that usbcore, usb-storage and scsi-mod are loaded.

---

### Post by nanamin on 2006-08-31
```
sacha@dcrypt:~$ dmesg | grep sda 
sacha@dcrypt:~$ dmesg | grep sdb
sacha@dcrypt:~$ dmesg | grep usb
[17302611.680000] usb 5-1: new high speed USB device using ehci_hcd and address 19
[17302611.812000] usb-storage: device found at 19
[17302611.812000] usb-storage: waiting for device to settle before scanning
[17302617.040000] usb 5-1: USB disconnect, address 19
[17302617.040000] usb-storage: device scan complete

```

```
sacha@dcrypt:~$ lsmod | grep usb
usb_storage            74176  0 
scsi_mod              139496  2 sd_mod,usb_storage
usbcore               130692  5 usb_storage,ehci_hcd,uhci_hcd,ohci_hcd

```

---

### Post by nanamin on 2006-09-01
bump

---

### Post by whizbaby on 2006-09-01
Sorry, had to codalot today...
Back to your problem: let's try to generate this /dev entry by ourselves!
In **/etc/udev/rules.d/20-names.rules** append with your favorite editor (run with **sudo**):

# Samsung YP-U2J mp3 player
BUS=="usb", SYSFS{manufacturer}=="Samsung", SYSFS{product}=="YP-U2J", NAME="ypu2"

Because I don't know if restarting udevd would be enough, restart the whole system (:( very bad style :( , sorry)

now, is there a device(or directory?) in /dev starting with ypu2 (sudo grep -r ypu2 /dev)...? (this would be score!)
(if you can't see or mount it, can amaroK? (connect with media or so))
Oh, and put it only in USB 2.0, please.

---

### Post by veruca on 2006-10-02
Was this ever resolved? I'm still not able to get my yp-u2j player working.

---

