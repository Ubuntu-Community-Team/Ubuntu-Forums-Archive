---
title: "QCad printing and Dolphin question"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by notbitmonk on 2008-04-03
QCad is able to see my printer without problem.  I have an Epson Stylus CX7400 with two entries using different drivers.  One entry uses Avasys pipslite driver and the other uses the gutenprint driver.  I can print from QCad using the gutenprint driver but the resultant printout is wrong.  With the gutenprint driver, the drawing gets shifted (about a quarter of the drawing) towards one of the corners.  The pipslite driver offered better picture printouts on other programs but couldn't print from QCad because it complained that /usr/lib/cups/filter/rastertopips didn't exist.  I reinstalled  the Avasys driver but now I can't use it (even after reinstalling cups).  With the Avasys driver QCad is now complaining the it can´t find libcups.so and now other programs are not printing because of the following error (from the IPP report): job-printer-state-message - /usr/lib/cups/filter/rastertopips failed.  Any help on how to fix it?

Also with Dolphin I would like to change its one click behavior to two-click.  I wasn´t able to find where to change the behavior in the settings page.  Thanks

---

### Post by notbitmonk on 2008-04-04
bump

---

### Post by notbitmonk on 2008-04-04
I went into Adept and selected to purge the pipslite package.  Following the instructions from [http://forum.ubuntu-it.org/index.php?topic=142737.msg941930]("http://forum.ubuntu-it.org/index.php?topic=142737.msg941930")  as directed by [http://ubuntuforums.org/showthread.php?t=631781]("http://ubuntuforums.org/showthread.php?t=631781") I did the following:
[LIST=1]
[*]Created a .deb file by using dpkg
[*]Since I'm using Kubuntu, I clicked on the .deb file and installed it
[*]Afterwards in Adept I installed libgtk1.2 and libgtk1.2-common
[*]Opening a shell, I typed ```
sudo sh /usr/share/pipslite/rc.d/inst-rc_d.sh install
``` (for some reason, the filename was different from the one in the Italian post
[*]Still on the shell, ```
sudo /etc/init.d/ekpd start
```
[*]Install pipslite so that a ppd file can be created.  If you use 8.5x11 (letter) paper, is better to get the custom ppd as it will have the correct metrics.  If you don't, you can do it by hand.  The way I did it was to get the cups-pdf.ppd and look at the entries that describe the Letter page.  There are at least three different lines that you need to copy.  I will include the ppd file info at the bottom of the post in case you do not want to install libgtk1.2 ```
sudo pipslite-install
```
[*]Install the printer by using the GUI tools and select the created ppd (located at /usr/share/cups/model/ekscx7400.ppd).  You can also install using your browser and navigating to [http://localhost:631](http://localhost:631)
[/LIST]
The pipslite driver was better than the gutenprint driver.  Text appeared equal with both drivers however, images were sharper and color was truer with the pipslite driver.  Still, I can not print from QCad.  I was able to print from OpenOffice and Gwenview as well as the Test page from CUPS.  The problem appears to be QCad however I'm able to print to the CUPS-pdf printer so I don't really know.  QCad complains that libcups.so doesn't exist.  I used Dolphin's file search and the file can't be found.  I'm still trying to change the one-click behavior in Dolphin.  
Here is the ppd file (mine is ekscx7400 because my model is an Stylus CX7400):
```
*PPD-Adobe: "4.3"

*%
*% Photo Image Print System
*%   Copyright (C) SEIKO EPSON CORPORATION 2008.
*%

*FormatVersion:         "4.3"
*FileVersion:           "1.0"
*LanguageVersion:       English
*LanguageEncoding:      ISOLatin1
*PCFileName:            "EKSCX7400.PPD"
*Manufacturer:          "EPSON"
*Product:               "(Photo Image Print System Lite)"
*cupsVersion:           1.1
*cupsManualCopies:      True
*cupsModelNumber:       1
*cupsFilter:            "application/vnd.cups-raster 0 rastertopips"
*ModelName:             "SCX7400"
*ShortNickName:         "Stylus CX7400"
*NickName:              "EPSON  Stylus CX7400, Photo Image Print System Lite"
*PSVersion:             "(3010.000) 550"
*LanguageLevel:         "3"
*ColorDevice:           True
*DefaultColorSpace:     RGB
*FileSystem:            True
*Throughput:            "1"
*LandscapeOrientation:  Plus90
*VariablePaperSize:     False
*TTRasterizer:          Type42


*OpenUI *PageSize/Media Size: PickOne
*OrderDependency: 10 AnySetup *PageSize
*DefaultPageSize: LT
*PageSize LT/Letter  8 1/2x11 in:                           "<</PageSize[612.0 792.0]/ImagingBBox null>>setpagedevice"
*PageSize TLT/Letter  8 1/2x11 in (no margin):                     "<</PageSize[612.0 792.0]/ImagingBBox null>>setpagedevice"
*PageSize 4X6FULL/Photo Paper 4x6 in  No Perforations:                           "<</PageSize[288.0 432.0]/ImagingBBox null>>setpagedevice"
*PageSize T4X6FULL/Photo Paper 4x6 in  No Perforations (no margin):                     "<</PageSize[288.0 432.0]/ImagingBBox null>>setpagedevice"
*CloseUI: *PageSize

*OpenUI *PageRegion: PickOne
*OrderDependency: 10 AnySetup *PageRegion
*DefaultPageRegion: LT
*PageRegion LT/Letter  8 1/2x11 in:                           "<</PageRegion[612.0 792.0]/ImagingBBox null>>setpagedevice"
*PageRegion TLT/Letter  8 1/2x11 in (no margin):                     "<</PageRegion[612.0 792.0]/ImagingBBox null>>setpagedevice"
*PageRegion 4X6FULL/Photo Paper 4x6 in  No Perforations:                           "<</PageRegion[288.0 432.0]/ImagingBBox null>>setpagedevice"
*PageRegion T4X6FULL/Photo Paper 4x6 in  No Perforations (no margin):                     "<</PageRegion[288.0 432.0]/ImagingBBox null>>setpagedevice"
*CloseUI: *PageRegion

*DefaultImageableArea: LT
*ImageableArea LT:          "8.4 8.4 603.6 783.6"
*ImageableArea TLT:       "0.0 0.0 612.0 792.0"
*ImageableArea 4X6FULL:          "8.4 8.4 279.6 423.6"
*ImageableArea T4X6FULL:       "0.0 0.0 288.0 432.0"

*DefaultPaperDimension: LT
*PaperDimension LT:         "612.0 792.0"
*PaperDimension TLT:     "612.0 792.0"
*PaperDimension 4X6FULL:         "288.0 432.0"
*PaperDimension T4X6FULL:     "288.0 432.0"

*OpenUI *Quality/Quality: PickOne
*OrderDependency: 20 AnySetup *Quality
*DefaultQuality: PLAIN_NORMAL
*Quality PLAIN_NORMAL/ plain papers - Normal:                      "<</HWResolution[360 360]>>setpagedevice"
*Quality PMPHOTO_NORMAL/ EPSON Premium Glossy - Normal:                      "<</HWResolution[360 360]>>setpagedevice"
*CloseUI: *Quality

*OpenUI *Ink/Ink: PickOne
*OrderDependency: 30 AnySetup *Ink
*DefaultInk: COLOR
*Ink COLOR/Color:     "<</cupsBitsPerColor 8/cupsColorOrder 0/cupsColorSpace 1/cupsCompression 1>>setpagedevice"
*Ink MONO/Monochrome: "<</cupsBitsPerColor 8/cupsColorOrder 0/cupsColorSpace 0/cupsCompression 1>>setpagedevice"
*CloseUI: *Ink

*DefaultFont: Courier
*Font AvantGarde-Book: Standard "(001.006S)" Standard ROM
*Font AvantGarde-BookOblique: Standard "(001.006S)" Standard ROM
*Font AvantGarde-Demi: Standard "(001.007S)" Standard ROM
*Font AvantGarde-DemiOblique: Standard "(001.007S)" Standard ROM
*Font Bookman-Demi: Standard "(001.004S)" Standard ROM
*Font Bookman-DemiItalic: Standard "(001.004S)" Standard ROM
*Font Bookman-Light: Standard "(001.004S)" Standard ROM
*Font Bookman-LightItalic: Standard "(001.004S)" Standard ROM
*Font Courier: Standard "(002.004S)" Standard ROM
*Font Courier-Bold: Standard "(002.004S)" Standard ROM
*Font Courier-BoldOblique: Standard "(002.004S)" Standard ROM
*Font Courier-Oblique: Standard "(002.004S)" Standard ROM
*Font Helvetica: Standard "(001.006S)" Standard ROM
*Font Helvetica-Bold: Standard "(001.007S)" Standard ROM
*Font Helvetica-BoldOblique: Standard "(001.007S)" Standard ROM
*Font Helvetica-Narrow: Standard "(001.006S)" Standard ROM
*Font Helvetica-Narrow-Bold: Standard "(001.007S)" Standard ROM
*Font Helvetica-Narrow-BoldOblique: Standard "(001.007S)" Standard ROM
*Font Helvetica-Narrow-Oblique: Standard "(001.006S)" Standard ROM
*Font Helvetica-Oblique: Standard "(001.006S)" Standard ROM
*Font NewCenturySchlbk-Bold: Standard "(001.009S)" Standard ROM
*Font NewCenturySchlbk-BoldItalic: Standard "(001.007S)" Standard ROM
*Font NewCenturySchlbk-Italic: Standard "(001.006S)" Standard ROM
*Font NewCenturySchlbk-Roman: Standard "(001.007S)" Standard ROM
*Font Palatino-Bold: Standard "(001.005S)" Standard ROM
*Font Palatino-BoldItalic: Standard "(001.005S)" Standard ROM
*Font Palatino-Italic: Standard "(001.005S)" Standard ROM
*Font Palatino-Roman: Standard "(001.005S)" Standard ROM
*Font Symbol: Special "(001.007S)" Special ROM
*Font Times-Bold: Standard "(001.007S)" Standard ROM
*Font Times-BoldItalic: Standard "(001.009S)" Standard ROM
*Font Times-Italic: Standard "(001.007S)" Standard ROM
*Font Times-Roman: Standard "(001.007S)" Standard ROM
*Font ZapfChancery-MediumItalic: Standard "(001.007S)" Standard ROM
*Font ZapfDingbats: Special "(001.004S)" Standard ROM

```
Hope it helps some of you.

---

