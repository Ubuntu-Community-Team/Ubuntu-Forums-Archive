---
title: "How do I install a driver"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Johnny K on 2007-06-14
I need to install a driver for a device I have. I have the .tar.gz, but what do I do with it?

---

### Post by Crafty Kisses on 2007-06-14
> **Johnny K said:**
> I need to install a driver for a device I have. I have the .tar.gz, but what do I do with it?

What drivers are you exactly trying to install?

Usually you can just do this:
```
sudo apt-get install *package name*
```

That installs the package for you.

---

### Post by Johnny K on 2007-06-14
It's not available via apt-get. The driver is [USBVision]("http://sourceforge.net/project/showfiles.php?group_id=27255&package_id=169940&release_id=372069").

---

### Post by Crafty Kisses on 2007-06-14
> **Johnny K said:**
> It's not available via apt-get. The driver is [USBVision]("http://sourceforge.net/project/showfiles.php?group_id=27255&package_id=169940&release_id=372069").

Did you download the source version or the binary of that file?

---

### Post by w4ett on 2007-06-14
Here's a great how-to for app/driver installation.

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by encompass on 2007-06-14
What is it for.
It is better to understand your real goal, the look for a general solution.  Is this for some webcam or other device?  It could be your driver is already working in linux.  It jsut needs to be turned on.

---

### Post by Crafty Kisses on 2007-06-14
> **Johnny K said:**
> It's not available via apt-get. The driver is [USBVision]("http://sourceforge.net/project/showfiles.php?group_id=27255&package_id=169940&release_id=372069").

It depends on what you downloaded.

If you downloaded the source that means you have to compile the file.

If you downloaded the Binary version it should be a package you can just install, I'm not sure. :(

---

### Post by Johnny K on 2007-06-14
> Did you download the source version or the binary of that file?
Looks like I downloaded the source...shucks.


> What is it for.
It is better to understand your real goal, the look for a general solution. Is this for some webcam or other device? It could be your driver is already working in linux. It jsut needs to be turned on.
It's for something called "[Belkin USB VideoBus II]("http://catalog.belkin.com/IWCatProductPage.process?Product_Id=105106")" It's a USB device for capturing A/V. When I plugged in, nothing happened.

---

### Post by w4ett on 2007-06-15
There's an ap in Synaptic.....Camstream......which will do just that...if your  USB Bus sees your device.
 type lsusb in the terminal and see if it's in the output.

---

### Post by Johnny K on 2007-06-15
> **w4ett said:**
> There's an ap in Synaptic.....Camstream......which will do just that...if your  USB Bus sees your device.
 type lsusb in the terminal and see if it's in the output.
Great! Linux detects the device, and I installed camstream. But, now what do I do? Do I need special software to capture video? I have Kino, but it doesn't say it detects the device or anything like that.

Thanks in advance, and sorry for all the questions, I've been using Linux for a little over 24 hours :)

---

### Post by w4ett on 2007-06-15
In the terminal type    camstream and press <enter>,   when the GUI opens click on file and select your device from the dropdown menu

---

### Post by Johnny K on 2007-06-15
Terminal gives this message, then opens the camstream GUI:
```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
CVideoDevice::CVideoDevice() could not query capabilities; is this really a video device?
CVideoDevice::ResetImagesRGB()
CVideoDevice::ResetImagesYUV()
CCamWindow::CCamWindow()
CWebCamViewer::CWebCamViewer(0x5ae960, 0x0)
Error opening video device: -16.
```

Once camstream is open, it detects the device /dev/video1, but when I click OK, I get a blank sub-window.

---

### Post by w4ett on 2007-06-15
> **Johnny K said:**
> Terminal gives this message, then opens the camstream GUI:
```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
CVideoDevice::CVideoDevice() could not query capabilities; is this really a video device?
CVideoDevice::ResetImagesRGB()
CVideoDevice::ResetImagesYUV()
CCamWindow::CCamWindow()
CWebCamViewer::CWebCamViewer(0x5ae960, 0x0)
Error opening video device: -16.
```

Once camstream is open, it detects the device /dev/video1, but when I click OK, I get a blank sub-window.
In that blank window...does it have a FILE and WINDOW tab at the top....If so click on file and select "open viewer"  then you should see a device tab to select your device.

---

### Post by Johnny K on 2007-06-15
> **w4ett said:**
> In that blank window...does it have a FILE and WINDOW tab at the top....If so click on file and select "open viewer"  then you should see a device tab to select your device.
Yeah. My bad, I should have been more specific.

Camstream opened, I clicked File > Open viewer... > ["Open video device" pops up, /dev/video1 (only option) and "Use current size" are selected by default] > I clicked OK > [now I get just a small blue window bar with only _ [ ] X, but nothing else happens].

---

### Post by w4ett on 2007-06-15
To "see" anything u need a video feed or camera to your capture device.

---

### Post by Johnny K on 2007-06-15
I have something connected to the device, but camstream isn't showing anything. The device itself isn't the greatest piece of hardware, maybe it just isn't working anymore.

---

### Post by w4ett on 2007-06-15
well, you could try it on a M$ machine to verify, but camstream is a down and dirty method to get vid capture device to work in Ubuntu....it even worked with my 8 year old intel cam (which has vid capture too).

---

### Post by Johnny K on 2007-06-15
Yeah, I'll try that.

Thanks for all the amazing help! I learned alot about Linux by trying all this, so it certainly wasn't a waste of time.

---

