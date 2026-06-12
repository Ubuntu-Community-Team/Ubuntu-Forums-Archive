---
title: "digital camera works! almost"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by vector on 2006-03-03
HI all
Normally i just plug any digi cam in and ubuntu usb say import photos. never had a problem.
Untill
A mate turned up with one of those pen like things. 
vivitar vivicam.30
hwinfo recognises it fine
but the import photos thing dont come up.
after reading some posts it was sugested to try digikam so i did and I suspect its a kde prog cause it loaded 100meg :( agghhh anyway i was in a rush.
sure enough digikam recognised it as a siPix style cam
and the images were there but the format was stange ppm and the image quality was strange it looked very dim even fiddlin with setting in gimp or digikam could do much to bring the picture up.
I then noticed that gthumb could now collect them too however it used the same siPix driver and had the same problem.

any thoughts?
I suspect its detecting the wrong driver or is there a way to change the format settings in SiPix ?

hwinfo52: USB 00.0: 0000 Unclassified device
  [Created at usb.120]
  Unique ID: hSuP.GTrxbk7ICk8
  Parent ID: pBe4.96IMLmgnt6B
  SysFS ID: /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.0
  SysFS BusID: 2-2:1.0
  Hardware Class: unknown
  Model: "DXG DIGITAL CAMERA"
  Hotplug: USB
  Vendor: usb 0x0d64 "DXG"
  Device: usb 0x1001 "DIGITAL CAMERA"
  Revision: "1.00"
  Speed: 1.5 Mbps
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #50 (Hub)

---

### Post by Pragmatist on 2006-03-04
What happens if you just mount the camera, copy some photos to your hard drive and then view the photos?  Type this in a terminal:
```
tail -f /var/log/messages
```
THEN plug your camera in and watch the terminal screen.  The device file of the camera should appear.  It will typically be something like sdXY where X is a letter and Y is a number, (examples: sda1 sdb5 sdc2)
Take a look in the /media directory to see if there is a mount point for your camera.  If not make one:
```
sudo mkdir /media/camera 
```
Then mount the camera
```
sudo mount /dev/sda1 /media/camera
```
Then just change into the mount directory (in this case /media/camera) and browse the photos.  Copy a few to your home directory:
```
sudo cp filenames /home/username
```

---

### Post by vector on 2006-03-05
"What happens if you just mount the camera, copy some photos to your hard drive and then view the photos?"
Ill go home and try this again. I did list messages but couldnt actually determine the device file type and so didnt know how to manually mount the camera
ill report back
thanks

---

### Post by vector on 2006-03-05
ok i just did it again
tail /var/log/messages give me 
""Mar  6 18:34:32 localhost kernel: [4398872.051000] usb 2-2: new full speed USB device using uhci_hcd and address 17
Mar  6 18:34:32 localhost usb.agent[18824]:      libgphoto2: loaded successfully
Mar  6 18:34:32 localhost usb.agent[18810]:      libgphoto2: loaded successfully
""
so i have no idea what the device type is still
thinking it might be "uhci_hcd"
i tried 
sudo mount /dev/uhci_hcd /media/camera
and got a you must specify file system type
so Im still a little lost

after reading some other posts i also tried mount /dev/sda1 but of course thats my hd, i tried going up the sda? numbers and they are all my hd so its not that.
usbview can also see the camera.
DIGITAL CAMERA
Manufacturer: DIGITAL CAMERA
Speed: 12Mb/s (full)
USB Version:  1.10
Device Class: 00(>ifc )
Device Subclass: 00
Device Protocol: 00
Maximum Default Endpoint Size: 64
Number of Configurations: 1
Vendor Id: 0d64
Product Id: 1001
Revision Number:  1.00

i suspect they are not using a normal usb-storage type interface

---

### Post by vector on 2006-03-06
another post said to add a camera to /etc/hotplug/usb/libgphoto2.usermap
i copied the vivtar 3350 and then modified the vendor and product id to match my vivitar 30
also note that on connection of the vivitar 30 it doesnt always get deteced as shown in usbview the first time i reconected gthumb said it was unable to find vendor 0x0d64 the second time
i reconnected and gthumb seemed to be happy allthough it choose siPix again but at least it didnt say cant find vendor
however it also said no photos

after doing some further googling vivitar 30 hardly ever comes up while 3350 and some others are rampant. Im suspecting this is some wierd weird device.

---

### Post by Pragmatist on 2006-03-06
Actually, I said to type ```
**tail -f /var/log/messages**
```

The key is to include the **-f**  Here is what the command means: ```
tail
``` outputs the last 10 lines of a file to the terminal (can be more or less lines, but 10 is the default).  The **-f** switch tells the **tail** command to "follow" which means it scrolls whatever the CURRENT 10 lines are. 

So, you run this command ```
tail -f /var/log/messages
``` While that is running you then plug in your camera.  Then, read the screen and look for /dev/sdxy where x is a letter and y is a number.

---

### Post by vector on 2006-03-06
erm ok I believe i did do a -f at some stage and saw no diff than what I posted. However I also realised late last night that linux does not see the device everytime i plug it in, not sure why. So maybe I just missed it.

I will try again, thanks for your endurance.

I also noted on some other posts that your supposed to connect then turn on the camera, download, turn off the camera and disconnect. Something about messing up the driver.
Cant do im afraid. The camera has no power button. It wakes up and goes into PC mode as you plug it in.

---

### Post by PhilJ on 2006-03-06
try adding HAL as a user to the groups you are listed as user in. that did it for me as my camera is not listed but shows up as removable drive. I can connect it and gthumb asks to  import photos. Come one someone I'm a newbie and I've forgotten where the users are stored and what the file is called. All I did was add HAL to every line where my username was and it worked. Dont ask me how or why. It worked when I first installed Breezy,then it stopped for some reason so I did the above and it started recognising the camera again

philj

found it  /etc/group 

edit this file and add HAL as a user

---

### Post by Pragmatist on 2006-03-06
just typing ```
groups
``` will tell you what groups you belong to.  Also, check out: ```
man group
```

---

### Post by vector on 2006-03-07
ok well 
tail -f /var/log/messages did what i expected
Mar  7 17:38:41 localhost kernel: [4295231.261000] usb 2-2: new full speed USB device using uhci_hcd and address 11
Mar  7 17:38:41 localhost kernel: [4295231.405000] usb 2-2: new full speed USB device using uhci_hcd and address 12
Mar  7 17:38:42 localhost kernel: [4295231.546000] usb 2-2: new full speed USB device using uhci_hcd and address 13
Mar  7 17:38:42 localhost kernel: [4295231.834000] usb 2-2: new full speed USB device using uhci_hcd and address 14
Mar  7 17:38:42 localhost kernel: [4295231.862000] usb 2-2: USB disconnect, address 14
Mar  7 17:38:42 localhost kernel: [4295231.926000] usb 2-2: new full speed USB device using uhci_hcd and address 15
Mar  7 17:38:42 localhost kernel: [4295232.069000] usb 2-2: new full speed USB device using uhci_hcd and address 16
Mar  7 17:38:42 localhost kernel: [4295232.211000] usb 2-2: new full speed USB device using uhci_hcd and address 17
Mar  7 17:38:43 localhost kernel: [4295232.500000] usb 2-2: new full speed USB device using uhci_hcd and address 18

no different than before.
note that usbview did not show the camera .
I tried a reboot with camera attached and sure enough usb view listed it. I searched the var/log/messages but found no mention of any sdx etc.
on opening gthumb it had sipix as the camera but no images and then as if by magic I noticed it disappear of the usbview list as well :(

also FYI /etc/init.d/hotplug restart
makes no diff, i e it dosent popup in usbview.

mark@miranda:~$ groups
mark adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin mytunes

not sure if that helps?

erm what or who is HAL?
groups

---

### Post by vector on 2006-03-07
im not sure but I just rebooted and then scrolled back thru /var/log/messages and found this section
Mar  7 17:53:21 localhost kernel: [4294675.394000] **usb 2-1: new low speed USB device using uhci_hcd and address 3**
Mar  7 17:53:21 localhost kernel: [4294675.682000] usb 2-2: new full speed USB device using uhci_hcd and address 4
Mar  7 17:53:21 localhost kernel: [4294675.826000] usb 2-2: new full speed USB device using uhci_hcd and address 5
Mar  7 17:53:21 localhost kernel: [4294676.905000] usbcore: registered new driver hiddev
Mar  7 17:53:21 localhost kernel: [4294676.905000] **usbhid: probe of 2-1:1.0 failed with error -5**
Mar  7 17:53:21 localhost kernel: [4294676.905000] usbcore: registered new driver usbhid

I have highlighted what might be the error point ?
however I then tail -f /var/log/messages and disconnected the camera
Mar  7 18:01:01 localhost kernel: [4295165.689000] usb 2-2: USB disconnect, address 5

is disapeared of usbview list
I reconnected camera

Mar  7 18:01:01 localhost kernel: [4295165.689000] usb 2-2: USB disconnect, address 5
Mar  7 18:03:05 localhost kernel: [4295289.073000] usb 2-2: new full speed USB device using uhci_hcd and address 6
Mar  7 18:03:05 localhost kernel: [4295289.217000] usb 2-2: new full speed USB device using uhci_hcd and address 7
Mar  7 18:03:05 localhost kernel: [4295289.410000] usb 2-2: new full speed USB device using uhci_hcd and address 8
Mar  7 18:03:05 localhost kernel: [4295289.539000] usb 2-2: new full speed USB device using uhci_hcd and address 9

---

### Post by vector on 2006-03-07
hhahh this time i tokk a picture and while the camera was "awake" I plugged it in

 Mar  7 18:05:39 localhost kernel: [4295443.808000] usb 2-2: USB disconnect, address 15
Mar  7 18:05:39 localhost kernel: [4295443.872000] usb 2-2: new full speed USB device using uhci_hcd and address 16
Mar  7 18:05:40 localhost kernel: [4295444.011000] usb 2-2: new full speed USB device using uhci_hcd and address 17
Mar  7 18:05:42 localhost usb.agent[8730]:      libgphoto2: loaded successfully
Mar  7 18:05:42 localhost usb.agent[8710]:      libgphoto2: loaded successfully
Mar  7 18:05:42 localhost usb.agent[8823]:      libgphoto2: loaded successfully
Mar  7 18:05:42 localhost usb.agent[8836]:      libgphoto2: loaded successfully

usbview indicated it was there too
i tried gthumb and :( the same old story. SiPix detected but no images, then it disapeared off the usbview

---

### Post by Pragmatist on 2006-03-07
groups is a command to determine the groups you belong to.  The idea of a group is similar to that of a user.  Seperate users allow the ability for each user to control who can do what with their files.  Seperate groups allows all the members of each group to control who can do what with their files.  If you list a file with **ls -l** you will get a long listing which has something like this:
**brw-rw----  1 root disk 3, 0 Mar  7 07:37 /dev/hda**
This means that the user called root is the owner of the file and that the group called disk is the file's group.  brw-rw---- means that it is a block device (it transfers information in blocks as opposed to a character device which transfers information character by charcter such as your terminal device or console device or modems and so on).  The important par are the 9 spaces that follow this letter b or c.  they can contain:
rwxrwxrwx  r stands for read, w stands for write and x stands for execute.  The first three are the owner's permission the second three the group permissions and the last three are permissions for everybody else (called "other").  So in the case of /dev/hda which is my hard drive, the owner, root, can read or write to this device, and any user who is a member of the group disks can read or write to it.  Everybody else can not read or write to it.  There is much more to understanding and manipulating permissions so go to [www.google.com/linux](www.google.com/linux) and type in "file permissions howto"  and you'll find lots of good documentation.

HAL stands for Hardware Abstraction Layer and you can read its man page if you like: ```
man hald
```  Its purpose is to make detecting devices easier. Also check out ```
man lshal
``` this lets you list all the devices HAL has detected.  It is a bit messy looking however, so try ```
hal-device-manager
``` which is much more user-friendly.

Question: What is the EXACT make and model of your camera read from the camera itself, not the computer.

Question: What is **usbview**

Question: What is the output of typing ```
mount
```
Question: What is the output of typing ```
ls -l /media
```
Question: What is the output of typing ```
ls -l /mnt
```

---

### Post by vector on 2006-03-07
**"""Question: What is the EXACT make and model of your camera read from the camera itself, not the computer."""**

vivitar vivicam 30

some info Im collecting on the beast [http://mec-symonds.eng.monash.edu.au/cgi-bin/twiki/view/Saqqara/VivitarVivicam30](http://mec-symonds.eng.monash.edu.au/cgi-bin/twiki/view/Saqqara/VivitarVivicam30)
[B]
"""Question: What is usbview"""[/B]

apt-get install usbview
"""USBView is a GTK program that displays the topography of the devices that are plugged into the USB bus on a Linux machine. It also displays information on each of the devices. This can be useful to determine if a device is working properly or not.""" [http://www.kroah.com/linux-usb/](http://www.kroah.com/linux-usb/)

your other questions regarding mount and /media I will do when Im in front of my home box (im currently at work).  however I think I know what your trying to find out and I can tell you that the camera does not show up in any of these places.
I also bring to your attention the fact that the /var/log/messages indicates it detects/loads the device multiple times onto sequential address. This to me is very strange and hints to me at anyrate that its glitching as I plug the device in.

---

### Post by Pragmatist on 2006-03-07
> I also noted on some other posts that your supposed to connect then turn on the camera, download, turn off the camera and disconnect. Something about messing up the driver.
Cant do im afraid. The camera has no power button. It wakes up and goes into PC mode as you plug it in.

My guess is that this is the problem.  I just tested things out with my camera which I know works.  I did **tail -f  /var/log/messages** plugged the camera in.  Nothing shows up in messages.  Turn the camera on, it shows up. Turn the camera off, it shows that it disconnected.  Turn the camera on again, I get a new address and it shows the camera is connected etc...etc...etc...
> Mar  7 16:00:55 localhost kernel: [4324907.695000] usb 2-3: new full speed USB device using ohci_hcd and address 3
Mar  7 16:00:57 localhost usb.agent[9166]:      libgphoto2: loaded successfully
Mar  7 16:00:57 localhost kernel: [4324909.768000] usb 2-3: USB disconnect, address 3
Mar  7 16:01:09 localhost kernel: [4324920.945000] usb 2-3: new full speed USB device using ohci_hcd and address 4
Mar  7 16:01:09 localhost usb.agent[9255]:      libgphoto2: loaded successfully
Mar  7 16:01:17 localhost kernel: [4324929.768000] usb 2-3: USB disconnect, address 4


In that monash.edu website there is a pdf file for the user manual.  It says you can turn the camera on by holding down the **MODE** button until the camera beeps.  I would try this:
1. ```
tail -f /var/log/messages
```
2. plug camera in
3. press MODE button until camera beeps and watch the terminal for new messages as you do this.

---

### Post by vector on 2006-03-08
yeah the mode button only works in camera mode. 
as soon as you plug the camera into the usb it turns itself on and goes into PC mode.
I did try tuning it on first then plugging in but it doesnt make much diff

hal-device-manager
I got the camera recognised (viewable in usbview) and ran hal-device-manager.
its listed under usb digital camera usb vendor specific interface(note its listed twice :(
there is alot of guf in the advanced tab which I cant seem to select to repaste here :(
not sure what else to do with hal.

Im wondering if when i loaded digikam its upset it or loaded other drivers that maybe confusing it im not sure how to unload digikam.


sumary: I dont think the vivitar 30 uses a normal storage type driver
and i think its power up when conected is causing problems

ok gthumb is picking sipix because according to the libgphoto2.usermap
sixpix has the same id and vendor as my beast
# SiPix Stylecam
libgphoto2           0x0003      0x0d64   0x1001    0x0000       0x0000      0x00         0x00            0x00            0x00            0x00               0x00               0x00000000
not sure what that means of course or what libgphoto does with this info.
maybe vivicam were naughty and pinched someone elses number, thats why you cant seem to buy them 
anymore?

this is all a real shame cause I know a few other guys who have them and would like to use them under linux

---

### Post by Pragmatist on 2006-03-08
> I dont think the vivitar 30 uses a normal....driver
I agree.  However, if your not able to turn the camera on the driver doesn't even come into play.  If you want to send information on HAL you can use the ```
lshal
``` command.  You'll get a long listing, so it is better to filter out just what you need by using **grep** so try this:
```
lshal | grep usb
```

Maybe some of this can help:
[http://www.linuxquestions.org/questions/showthread.php?threadid=338852](http://www.linuxquestions.org/questions/showthread.php?threadid=338852)
[http://www.linux-usb.org/USB-guide/c122.html](http://www.linux-usb.org/USB-guide/c122.html)

Now, my opinion is that this camera just doesn't work with Linux.  You can use hardware compatibility lists such as:
[http://www.linuxquestions.org/hcl/showcat.php?cat=271&page=](http://www.linuxquestions.org/hcl/showcat.php?cat=271&page=)
In general, if possible, it is always better to know in advance whether or not hardware is compatible with Linux.  This is especially important with somewhat newer technologies (like firewire), and with newer models of hardware devices.

At the end of the day, however, there will always be some hardware devices that won't work with Linux.  In order to write a driver, sometimes the cooperation of the manufacturer is necessary and sometimes they don't want to reveal their proprietary information.  In this case we are stuck.

---

### Post by vector on 2006-03-08
Ok thanks for all you help, we tried our best. I read thru some of those links and dont understand much of any of it,, its way beyond this little black duck.

fully understand about drivers and manufacturers not giving out info and all that stuff.
We give in! and will have to opt for downloading it using a windows box.

As for looking at compatible lists I generally do however I might add I got caught out here too. I recently replaced an old scanner. and Sane indicated that it supported Cannon Lite 60 but when I got it home, no go. After some soul seraching it seems the copy of sane in ubuntu is old compared to the one listing my scanner. Yes I can it seems fix this by manually doing stuff but im not an IT guy..It is currently plugged into the windows box too :( until ubuntu catches up with sane and one day ill upadate and itll just work :) I hope

---

### Post by dvarsam on 2006-03-08
I think that your last resort is to use the "jump" command.

It is very powerfull though, so be carefull how you use it...

---

### Post by Pragmatist on 2006-03-08
> "jump" command.  What is the jump command?

---

### Post by jsteve54302 on 2007-01-14
> **vector said:**
> HI all
sure enough digikam recognised it as a siPix style cam
and the images were there but the format was stange ppm and the image quality was strange it looked very dim even fiddlin with setting in gimp or digikam could do much to bring the picture up.



Sorry to break it to you, but unless there's an image quality setting on that cam that cam that can be changed in windows, that format is there to stay.  Fixing the drivers won't change  what format the cam is using.  If I'm not mistaken, ppm is one of the high-quality raw-image format similar (but not identical) to JPEG...  my Canon Eos Rebel XT can use a similar format, and it's docs warn that if you use it without the software provided by Canon, the images will appear dark or washed out because image programs like GIMP don't get all the information from the file (I guess some of it is in file areas normally reserved for metadata).  You may try seeing if you can change the quality setting of the cam from windows (I can't imagine one of those pencams could possibly take a photo of high enough resolution to need that kind of image quality anyway, and it takes up more space), or find a GIMP plugin for that file format (try googling "gimp plugin .ppm" without the quotes of course.)

---

