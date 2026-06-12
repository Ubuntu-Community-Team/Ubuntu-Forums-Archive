---
title: "Bluetooth And SD"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2005-12-30
Hi,

I have a Dell Latitude X300 and it has built in bluetooth and an SD card slot.

This is all well and dandy apart from the fact that i can get neither of them to work. In XP all I had to do was put an SD card in and it would open up and  I had a bluetooth manager that would allow me to search for and swap files with bluetooth devices.

Is there anyway anyone can help me with this please?

Also, something else that is a little annoying is that if I want to attach a CD drive to my laptop i have to restart Ubuntu for it to recognise it. I have the CD drive logo in the Computer folder but it doesnt let me mount it.

Many thanks.

---

### Post by thekiller on 2005-12-30
check this link:

[https://wiki.ubuntu.com/BluetoothSetup?highlight=%28bluetooth%29](https://wiki.ubuntu.com/BluetoothSetup?highlight=%28bluetooth%29)

and for your cdrom, check the output of /etc/fstab, it should be the following to mount it using any user, if it is not then change it to this:

```

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by beercz on 2005-12-30
I think the SD card reader is a usb device - this thread may help:

[http://ubuntuforums.org/showthread.php?t=104875]("http://ubuntuforums.org/showthread.php?t=104875")

---

### Post by Dr Von Bon Bon on 2005-12-30
I can't get the /etc/fstab to work as it says that the command is invalid

---

### Post by thekiller on 2005-12-30
you have to open it in an editor (gedit or whatever u use)

[COLOR="red"]gedit /etc/fstab[/COLOR]

or just do

[COLOR="Red"]more /etc/fstab [/COLOR]

and it will output the result on the terminal itself. Sorry it wasnt clear enough.

---

### Post by Gimbo on 2005-12-30
[QUOTE=Dr Von Bon Bon]I can't get the /etc/fstab to work as it says that the command is invalid[/QUOTE]

You need to add sudo at the beginning of the command line to give you root privileges and you need to use the gedit command to open the file in gedit (Ubuntu's default text editor, the equivalent of Notepad)

```

sudo gedit /etc/fstab

```

---

### Post by Dr Von Bon Bon on 2005-12-30
Thanks, i probably should have known that so cheers for taking the time to say it.

Ive tried the SD card again but it still doesn't realise that it has been inserted.

---

### Post by thekiller on 2005-12-30
[QUOTE=Dr Von Bon Bon]
Ive tried the SD card again but it still doesn't realise that it has been inserted.[/QUOTE]

Its simply 'cos it hasn't been defined in /etc/fstab. If im right, it should be recognised as a USB device.

Try these :

```

sudo mkdir /mnt/sd_card
sudo mount -t vfat /dev/sda1 /mnt/sd_card

```

If it doesnt bomb after the second command, then its mounted correctly. Then you just need to open [COLOR="Red"]Nautilus[/COLOR] and browse to /mnt/sd_card


EDIT : One more thing, go to System -> Administration -> Device Manager and try to look out if your SD card is indeed recognised.

---

### Post by Dr Von Bon Bon on 2005-12-30
Okay, when I did the second command it came up with:

mount: special device /dev/sda1 does not exist


And i had a look in the device manager and couldn't see it but that doesn't really mean much because most of the stuff in there I didn't recognise but it defintely didn't say SD card anywhere.

---

### Post by thekiller on 2005-12-30
[QUOTE=Dr Von Bon Bon]Okay, when I did the second command it came up with:

mount: special device /dev/sda1 does not exist
[/QUOTE]

Its more of a hit and trial to find out which device SD card is identified as, i would try hdc1, sdb1, sdc1 too. Normally if you are not using any other USB devices on your computer, sda1 is the default it starts with.

[QUOTE=Dr Von Bon Bon]And i had a look in the device manager and couldn't see it but that doesn't really mean much because most of the stuff in there I didn't recognise but it defintely didn't say SD card anywhere.[/QUOTE]

When you look into device manager, on your left are displayed all the hardwares recognised by the machine, click on the places where USB is shown, and then on the right panel, details about that particular USB will be displayed (like the make and model of your SD card).

---

### Post by Dr Von Bon Bon on 2005-12-30
Okay, none of the other names worked and when I went into the device manager not a single one of them that had USB said anything about an SD card.

This sucks.

---

### Post by thekiller on 2005-12-30
ok, i like shooting in the blind, haha. Anyway, do u want to upload the pics from the SD card on ur computer ? If its from a camera, why dont u plug the camera through a USB to your computer and then ubuntu should definitely recognize it. Thats what my feeling is.

---

### Post by Dr Von Bon Bon on 2005-12-30
Yeah, 

I could do that but it's just the fact that I would like it work and I also use it for putting MP3's onto it to play on my phone.

Well, thanks for all your help.

---

### Post by thekiller on 2005-12-30
Ok, can u please post the output of

```

more /proc/bus/usb/devices

```

And see if you can see your SD card there ? If not, then your kernel doesnt recognize it and you have to recompile the kernel to make SD card recognizable directly.

---

### Post by Dr Von Bon Bon on 2005-12-30
This is what comes up.


```
T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-10-386 ehci_hcd
S:  Product=Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
S:  SerialNumber=0000:00:1d.7
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-10-386 uhci_hcd
S:  Product=Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
S:  SerialNumber=0000:00:1d.2
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms
--More--(0%)

```

Im using a panasonic 64mb SD card if that's any help and it is in the computer although I can't see it on that list.

---

### Post by thekiller on 2005-12-30
yeah its not there. Do you have any other USB device you can possibly connect to your computer ? And then again run that command and see if it is recognized ? I was searching on google about how to set up an SD card and they are normally recognized as USB. And are mounted the way I told you to mount them before.

Also post the output of 

```

lsmod |grep usb

```

---

### Post by Dr Von Bon Bon on 2005-12-30
Okay, I put in my USB key and here is the output:


```
T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-10-386 ehci_hcd
S:  Product=Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
S:  SerialNumber=0000:00:1d.7
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0457 ProdID=0151 Rev= 1.00
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr= 98mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=125us
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=  64 Ivl=16ms

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
--More--(0%)

```


And after running the other command:

```
usb_storage            64704  1
hci_usb                13192  2
bluetooth              43012  7 rfcomm,l2cap,hci_usb
scsi_mod              124872  3 sd_mod,usb_storage,sbp2
usbcore               104316  5 usb_storage,hci_usb,ehci_hcd,uhci_hcd
ide_core              125268  4 usb_storage,ide_disk,ide_generic,piix

```


(I did that last one with the USB stick still in)

---

