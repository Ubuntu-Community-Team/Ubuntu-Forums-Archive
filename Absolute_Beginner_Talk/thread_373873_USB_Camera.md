---
title: "USB Camera"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by tin2 on 2007-03-01
I have a camera out there which linux apparently recognized. I used lsusb command And it gave

 Bus 001 Device 006: ID 054c:00c0 Sony Corp. Handycam DCR-30

What should i do to mount it?

---

### Post by tin2 on 2007-03-02
Anyone?:(

---

### Post by steven8 on 2007-03-02
I'm not sure.  When I plug in my camera to the computer, it powers up, I select PC from the little menu on the back of the camera, and Ubuntu asks me if I want to import the pictures or just view them in a folder.

Power up your camera once it's connected and see if Ubuntu reacts.

---

### Post by tin2 on 2007-03-02
Sorry I should have made myself clearer: I have a problem with a Digital Camcoder not a digital camera. The camera works fine:)

---

### Post by steven8 on 2007-03-02
Shoot.  I don't have a camcorder, and you are the second person I've seen post with camcorder probelms in the last two days.  Di a search for camcorder in this forum.

I'll take a look too.

---

### Post by tin2 on 2007-03-02
I have searched in this fourm and in google too...nothing positive.:( 

The camcoder transmits data by usb streaming and every one is talking about firewire.

The manufacturer only supports windows and mac so i am stuck here.

I will wait until you lot get a solution:popcorn:

---

### Post by halitech on 2007-03-02
I found these threads on this

[http://www.ubuntuforums.org/showthread.php?t=337116&highlight=DCR-30]("http://www.ubuntuforums.org/showthread.php?t=337116&highlight=DCR-30")

[http://www.ubuntuforums.org/showthread.php?t=206847&highlight=DCR-30]("http://www.ubuntuforums.org/showthread.php?t=206847&highlight=DCR-30")

[http://www.linux1394.org/view_device.php?id=829]("http://www.linux1394.org/view_device.php?id=829")

---

### Post by tin2 on 2007-03-03
Well thank you for those links but..

 Link 1: sudo mount /dev/sda1 /media/camera  gave
  
mount: special device /dev/sda1 does not exist

Link 2,3: They deal with firewire not usb! I do not have a firewire port in my computer.

---

### Post by taurus on 2007-03-03
Did you plug in your camera and was it on?  If yes, then what's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by tin2 on 2007-03-03
I made sure that the camcoder and its usb streaming feature is on.

Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2   *        2321        4780    19759950   83  Linux
/dev/hda3            4781        4870      722925    5  Extended
/dev/hda5            4781        4870      722893+  82  Linux swap / Solaris

is the output for  sudo fdisk -l

but lsusb gave

Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 054c:00c0 Sony Corp. Handycam DCR-30
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

:(

---

### Post by taurus on 2007-03-03
And 

```
dmesg | tail
```

---

### Post by tin2 on 2007-03-03
[  445.654603] EXT3-fs: unable to read superblock
[ 1140.146659] usb 1-1: USB disconnect, address 2
[ 1722.408627] usb 1-1: new full speed USB device using uhci_hcd and address 3
[ 1722.560505] usb 1-1: configuration #1 chosen from 1 choice
[ 1727.237727] usb 1-1: USB disconnect, address 3
[ 1751.718647] usb 1-1: new full speed USB device using uhci_hcd and address 4
[ 1751.878498] usb 1-1: configuration #1 chosen from 1 choice
[ 1943.332203] usb 1-1: USB disconnect, address 4
[ 2431.397098] usb 1-1: new full speed USB device using uhci_hcd and address 5
[ 2431.548960] usb 1-1: configuration #1 chosen from 1 choice

---

### Post by steven8 on 2007-03-05
Go to System>Preferences>Removable Drives and Media, then click on the Cameras Tag.  My system does not have anything indicated as to what the system is to do with a Digital Video Camera once it's connected.  Check to see if yours is set up.

Heres a screen of what it looks like:

[http://h1.ripway.com/steven8/Screenshot.png]("http://h1.ripway.com/steven8/Screenshot.png")

---

### Post by tin2 on 2007-03-05
>>My system does not have anything indicated as to what the system is to do with a Digital Video Camera once it's connected

Exactly. Ubuntu does not know what to do when a camcoder is connected.
So I typed in a test command nautilus. Nothing happened. It means that Ubuntu does not auto-mount my camcoder ! Anyway, thanks!:)

---

