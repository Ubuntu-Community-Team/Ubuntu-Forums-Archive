---
title: "WindowsXP in vmplayer doesn't recognise usb HD"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2007-02-14
I installed vmplayer over Ubuntu yesterday and can now get to Windows XP without having to go through the dual boot restart rigmarole.
BTW, I used this howto which worked very well ([http://www.ubuntuforums.org/showthread.php?t=342631&highlight=vmware-player+howto](http://www.ubuntuforums.org/showthread.php?t=342631&highlight=vmware-player+howto))

However, when using Windows XP over Ubuntu, I can't get WinXP to recognise my usb HD.
I tried editing the .vmx file to include
```
scsi0.present = "TRUE"
```
from "FALSE".
However, this gave the following error message on starting up WinXP:
> Bad parameter scsi0:0.fileName: no file specified.
Cannot open configuration file "/home/paul/vmware/WindowsXPHome.vmx": Permission denied.
Configuration not saved.

Can anybody please advise me as to what I need to do to achieve this end?
Thanks
Paul

---

### Post by thenetduck on 2007-02-16
I hope this isn't a little bit off topic, but you could try using Virtual Box. Anyway, I don't have a solution for vmware sorry, 
 
The Net Duck

---

### Post by lemmy999 on 2007-02-16
I installed VMware server some days ago and noted that it didn't detect my USB key. Checking the VMware forums it became apparent that VM doesn't support USB 2 ( at least)

---

### Post by anaconda on 2007-02-16
You can get the USB-hd to work, but I think it will work as USB 1.1 not USB 2..

But. USB support isn't enabled after installation. So you must enable it. 
(might be a little different for you.. I am using VMWare server..)
Just povwr off your virtual machine, and then you can edit the settings. Select the "Edit virtual machine settings" (VM>Settings goes to the same place)  Then click the +Add and select USB controller. Then the next time you start your virtual machine it will have USB controller installed. 

Then just plug your USB-hd and Ubuntu will find your hd. Then go to VM>Removable devices and select your USB-hd and select connect. And there you have it.

It will be similar with the VMWare player

---

### Post by PaulFXH on 2007-02-17
Thanks for the replies and advice.
OK, I've got the usb hdd working but it's a little complicated.
First, there is no "Edit virtual machine settings"  or VM>Settings in vmware player.
There is, however, the .vmx file which contains this type of information. But I did already include in this "usb.present = "TRUE"" which I had thought would enable all usb devices to be recognised.
But apparently not.
Further down in the .vmx file are three usb related lines, the first of which is:
```
usb.autoConnect.device0 = "path:2/0 autoclean:1"
```
The other two lines refer to devices 1 and 2 but do not have any defined paths.
This seems to imply that ONLY three usb devices are catered for. But I had four (HDD, printer, scanner and bluetooth).
So, I took out the bluetooth and now the usb hdd is readily recognised every time I start my virtual Windows XP.
I'm going to try to add a fourth line (usb.autoConnect.device3) to see if I can bump up the number of recognisable usb devices.
Incidentally, I have both usb 2.0 and usb 1,1 ports on my computer. Both the printer and the usb hdd, both of which work fine on the virtual OS, are connected to usb 1.1 ports.
However, when I start up the usb hdd, I get a message saying that this device can work faster if it were connected to a usb 2.0 port. The Help accompanying this message then says that NO usb 2.0 ports are available on this computer which ties in with what lemmy999 said in his post.

---

