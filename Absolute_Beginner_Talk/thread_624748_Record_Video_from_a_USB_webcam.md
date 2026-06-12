---
title: "Record Video from a USB webcam"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by edwardcix@hotmail.com on 2007-11-27
Hi guys I just upgrated to Ubuntu 7.10
I got Camorama working 
I would like to record video from my webcam (USB)
I tryed some programs but no one seemed to work properly
I also did a lot of search about this topic but coudlnt find any good
I though of ask personally...

---

### Post by philinux on 2007-11-27
Have you tried mencoder or camstream both in synaptic.

I think mencode is command line only, dont know if there is a gui.

---

### Post by edwardcix@hotmail.com on 2007-11-28
I tryed Camstreamer
but Im not sure if it does record by it self
I mean I read this in the terminal
```
edoardo@edoardo-laptop:~/install/camstream-0.27$ camstream
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
CCamWindow::CCamWindow()
CWebCamViewer::CWebCamViewer(0x80d3df0, 0x0)
CVideoDevice::Init()
Using mmap(), VMBuf.size = 426240
Trying to find video options for Logitech QuickCam USB:/dev/video0
searching Logitech QuickCam USB
CSnapshotSettingsDlg::CSnapshotSettingsDlg(...)
CVideoSettingsDlg::SizeChanged(352x292)
CVideoSettingsDlg::FramerateChanged(10)
CCamPanel::SetSize(352x292)
CCamPanel::SetImageSize(352x292)
CCamPanel::SetVisibleSize(352x292)
CCamPanel::SetSize(352x292)
CCamPanel::SetImageSize(352x292)
CCamPanel::SetVisibleSize(352x292)
RecalcTotalViewSize: resize viewport(352x292)
EnableRGB: +
CVideoDevice::SetPalette picked palette 5 [rgb32]
CVideoDevice::CreateImagesRGB()
 using pre-allocated memory
CVideoDevice::StartCapture() go!
EnableRGB: -
CVideoDevice::ResetImagesRGB()
CVideoDevice::SetPalette picked palette 0 []
CVideoDevice::StopCapture() halt!

```
I tryed also to downlad it from it website but while configuring it
it says that Im missing the Qt lybraries..I pretty much installed all of it but still says the same
Im confused on this
thanks for the help

---

