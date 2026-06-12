---
title: "Viewing Camera Pictures in Ubuntu"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by flubmasterq on 2007-05-20
I'm trying to figure out how I can view/save the pictures from my camera on Ubuntu.
When I plug in my camera, Ubuntu says "There are photos on this camera.  Would you like to them to your album?" and when I say yes it says "An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device."

---

### Post by Pragmatist on 2007-05-20
Please tell us what kind of camera (company and model number)

---

### Post by flubmasterq on 2007-05-21
Photosmart m425.

---

### Post by fenian on 2007-05-22
Try this-from the terminal run this command (will open gedit window)...
> 
sudo gedit /etc/udev/rules.d/45-libgphoto2.rules

add this line in the gedit file...> 

SYSFS{idVendor}=="07cf", SYSFS{idProduct}=="1043", MODE="0660", GROUP="plugdev"

save file and close gedit then run...
> 
sudo /etc/init.d/udev restart

---

### Post by jiminycricket on 2007-05-22
.

---

### Post by flubmasterq on 2007-05-23
> **fenian said:**
> Try this-from the terminal run this command (will open gedit window)...

add this line in the gedit file...

save file and close gedit then run...

I did that, and I'm still getting the same error.

---

### Post by fenian on 2007-05-23
what  output do you get if you run
> 
 lsusb

---

### Post by Pragmatist on 2007-05-24
Lets find out if your camera is treated like a hard drive or not.  First type this with the camera unplugged:
```
tail -f /var/log/messages
```Make a note of the last line that appears on the screen.  Now plug in your camera, and turn it on, and watch for the new lines to appear in the terminal.  Post those new lines here.

---

### Post by flubmasterq on 2007-05-24
May 24 17:30:54 flubmasterq kernel: [17181691.692000] usb 1-1: new full speed USB device using uhci_hcd and address 2
May 24 17:30:55 flubmasterq kernel: [17181691.876000] usb 1-1: configuration #1 chosen from 1 choice

---

### Post by FuturePilot on 2007-05-24
Would you happen to be using Edgy? I had this same problem with Edgy.:???:

---

### Post by flubmasterq on 2007-05-24
I'm either using Edgy or Feisty Fawn... I can't remember. >,<
What did you do to fix it in Edgy?

---

### Post by Pragmatist on 2007-05-24
I have a feeling that the problem is related to gnome-volume-manager or something else in gnome, hal, udev, etc...  Here is a simple experiment:

1.) Go into Synaptic and install **gphoto2**
2.) In a terminal type: ```
gphoto2 --get-all-files
```

What happened?

I took 5 pictures for this experiment (NOTE: Obviously you must have pictures in your camera to download!).  Here is my output:
> 
desktop:~$ **gphoto2 --get-all-files**
Downloading '100_9172.JPG' from folder '/store_00010001/DCIM/100K7300'...      
Saving file as 100_9172.JPG                                                    
Downloading 'HND_L1.XLS' from folder '/store_00010001/TRASH-~1'...
Saving file as HND_L1.XLS
Downloading 'MOOD0505.XLS' from folder '/store_00010001/TRASH-~1'...
Saving file as MOOD0505.XLS
Downloading 'ALBUM.DB' from folder '/store_00010001/TRASH-~1/DCIM'...
Saving file as ALBUM.DB
Downloading 'CARD.DB' from folder '/store_00010001/TRASH-~1/DCIM'...
Saving file as CARD.DB
Downloading 'ALBUM.DB' from folder '/store_00010001/TRASH-~1/DCIM/100HPM22'...
File ALBUM.DB exists. Overwrite? [y|n] n
[B]Specify new filename? [y|n] y
Enter new filename: myalbum[/B]
Saving file as myalbum
Downloading 'BANDPL~1.PDB' from folder '/store_00010001/TRASH-~1/RN_AUDIO/PLAYLIST'...
Saving file as BANDPL~1.PDB
[B]Downloading '000_0134.JPG' from folder '/store_00020001'...
Saving file as 000_0134.JPG                                                    
Downloading '000_0135.JPG' from folder '/store_00020001'...
Saving file as 000_0135.JPG                                                    
Downloading '000_0136.JPG' from folder '/store_00020001'...
Saving file as 000_0136.JPG                                                    
Downloading '000_0137.JPG' from folder '/store_00020001'...
Saving file as 000_0137.JPG                                                    
Downloading '000_0138.JPG' from folder '/store_00020001'...
Saving file as 000_0138.JPG                                                    [/B]
Downloading 'DCEMAIL.ABK' from folder '/store_00020001'...
Saving file as DCEMAIL.ABK


In bold you'll see:
1.) the command to run: gphoto2 --get-all-files
2.) A question that I answered. I just made up a filename that was memorable.  It seems that this file just contains some data that gphoto2 uses.
3.) The 5 downloaded JPEGs

---

### Post by FuturePilot on 2007-05-24
> **flubmasterq said:**
> I'm either using Edgy or Feisty Fawn... I can't remember. >,<
What did you do to fix it in Edgy?

I never got it fixed. I went back to Dapper. However, it did work for me in Feisty.

---

### Post by flubmasterq on 2007-05-25
This is what it said...

> *** Error ***              
An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.
*** Error (-53: 'Could not claim the USB device') ***       

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --get-all-files

Please make sure there is sufficient quoting around the arguments.


---

### Post by Pragmatist on 2007-05-25
What happens if you run gphoto2 with **sudo**
```
**sudo** gphoto2 --get-all-files
```

---

### Post by fenian on 2007-05-25
This is a [known bug]("https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146") in ]Feisty and Edgy involving the libgphoto2_rules list being out of date.Some people have had success following the instructions at the bottom of [this page.]("http://ubuntuforums.org/showthread.php?t=388576&highlight=camera&page=2")

---

