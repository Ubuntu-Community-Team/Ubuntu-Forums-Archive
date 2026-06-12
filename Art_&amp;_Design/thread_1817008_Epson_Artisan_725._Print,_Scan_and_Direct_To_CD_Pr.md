---
title: "Epson Artisan 725. Print, Scan and Direct To CD Printing (GIMP)"
date: 2011-08-02
forum: Art &amp; Design
---

### Post by nastyrecords on 2011-08-02
I recently just purchased a new printer however it would not work properly. I searched and searched and could not find any information on getting the Epson Artisan 725 printer to work flawlessly with Ubuntu 11.04 (Natty Narwhal). To include printing documents, scanning capabilities and also the direct to CD printing. After a few hours and a few wasted Cd's, ink and paper i finally was able to get it to work as it is intended to. (Quite well i might add). This is essentially a quick guide to others who may encounter this problem to make it less painful and time consuming. Getting the printing and scanning capabilities to work is the easiest part of it all. 

[LIST]
[*]Plug in a USB cable from the printer into your computer. Turn on your computer and printer. Ubuntu will recognize it and ask you which drivers you would like to install. A set of two will show up. Download the one that says "Recommended". Your printer will now have printing capabilities but the scanner will not work.
[*]Getting the scanner to work is rather easy as well. You will need "Image Scan!". Goto the Avasys website ([http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)). Scroll down to the "Form For Download" section. Select model, distribution and version. Click next and follow instructions. NOTE: Download both DATA and CORE deb files. You may need to also install "libltdl3" if you recieve an error message during install of CORE files. You can get that here [http://packages.ubuntu.com/hardy/libltdl3](http://packages.ubuntu.com/hardy/libltdl3).
[*]Now that you have printing and scanning capabilities, time for the more tedious part, direct print to CD. I am using GIMP. You will need the GIMP print plugin, if you do not have it, open the terminal and type **sudo apt-get install gimp-print **followed by your password. After this you will need to install **CDlabel2.scm **which can be downloaded here: [http://www.shallowsky.com/software/cdplugins/](http://www.shallowsky.com/software/cdplugins/). After downloading is complete, open the home folder press CTRL+H (to show hidden folders) click the .gimp folder and then scripts. Copy CDlabel2.scm into here. Open GIMP.
[*]From here, click file/new set width and height to 800x800. Then click filters/script-fu/misc/cdlabel. This now opens a blank CD template. Create your CD art here. After your finished and ready to print, click file/print. Select Artisan-720 in general. Goto page setup and select paper type: CD/DVD. Also select CD/DVD for paper source as well. Click Image Settings and set the following values:

width: 125.00 millimeters
height: 125.00 millimeters
x resolution: 162.560 pixels/in
y resolution: 162.560 pixels/in
check ignore page margins
position left: 0.00
position right: 90.90
position top: 0.00
position bottom: 154.40
center none
[*]The image should now appear in the top left hand corner of the preview box. Click advanced and make sure output paper size is selected to A4 210x297 mm and CD/DVD inner print position is 43 mm, and the other two values under "CD/DVD" are set to 0.0 mm. You are now ready to print! WARNING: Values do not save after opening a new project.

Like i said, after a few hours and a few wasted Cd's, ink and paper i finally was  able to get it to work as it is intended to. (Quite well i might add).  This is essentially a quick guide to others who may encounter this  problem to make it less painful and time consuming. Hopefully this will serve as a great help.
[/LIST]

---

### Post by practic on 2011-08-31
Many thanks for taking the time to post these instructions. 

I've just got an Artisan 725 (so far am quite impressed with the printer), although at the moment it's hooked up to a Windows 7 computer. 

But soon I will try it with Ubuntu, so I will save your instructions.

---

### Post by desktorp on 2011-08-31
> **nastyrecords said:**
> ..after a few hours and a few wasted Cd's, ink and paper i finally was  able to get it to work as it is intended to. (Quite well i might add).  This is essentially a quick guide to others who may encounter this  problem to make it less painful and time consuming. Hopefully this will serve as a great help.

I bestow upon you, the title: Modern Hero

---

### Post by matt0978 on 2012-08-26
> **nastyrecords said:**
> I recently just purchased a new printer however it would not work properly. I searched and searched and could not find any information on getting the Epson Artisan 725 printer to work flawlessly with Ubuntu 11.04 (Natty Narwhal). To include printing documents, scanning capabilities and also the direct to CD printing. After a few hours and a few wasted Cd's, ink and paper i finally was able to get it to work as it is intended to. (Quite well i might add). This is essentially a quick guide to others who may encounter this problem to make it less painful and time consuming. Getting the printing and scanning capabilities to work is the easiest part of it all. 

[LIST]
[*]Plug in a USB cable from the printer into your computer. Turn on your computer and printer. Ubuntu will recognize it and ask you which drivers you would like to install. A set of two will show up. Download the one that says "Recommended". Your printer will now have printing capabilities but the scanner will not work.
[*]Getting the scanner to work is rather easy as well. You will need "Image Scan!". Goto the Avasys website ([http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)). Scroll down to the "Form For Download" section. Select model, distribution and version. Click next and follow instructions. NOTE: Download both DATA and CORE deb files. You may need to also install "libltdl3" if you recieve an error message during install of CORE files. You can get that here [http://packages.ubuntu.com/hardy/libltdl3](http://packages.ubuntu.com/hardy/libltdl3).
[*]Now that you have printing and scanning capabilities, time for the more tedious part, direct print to CD. I am using GIMP. You will need the GIMP print plugin, if you do not have it, open the terminal and type **sudo apt-get install gimp-print **followed by your password. After this you will need to install **CDlabel2.scm **which can be downloaded here: [http://www.shallowsky.com/software/cdplugins/](http://www.shallowsky.com/software/cdplugins/). After downloading is complete, open the home folder press CTRL+H (to show hidden folders) click the .gimp folder and then scripts. Copy CDlabel2.scm into here. Open GIMP.
[*]From here, click file/new set width and height to 800x800. Then click filters/script-fu/misc/cdlabel. This now opens a blank CD template. Create your CD art here. After your finished and ready to print, click file/print. Select Artisan-720 in general. Goto page setup and select paper type: CD/DVD. Also select CD/DVD for paper source as well. Click Image Settings and set the following values:

width: 125.00 millimeters
height: 125.00 millimeters
x resolution: 162.560 pixels/in
y resolution: 162.560 pixels/in
check ignore page margins
position left: 0.00
position right: 90.90
position top: 0.00
position bottom: 154.40
center none
[*]The image should now appear in the top left hand corner of the preview box. Click advanced and make sure output paper size is selected to A4 210x297 mm and CD/DVD inner print position is 43 mm, and the other two values under "CD/DVD" are set to 0.0 mm. You are now ready to print! WARNING: Values do not save after opening a new project.

Like i said, after a few hours and a few wasted Cd's, ink and paper i finally was  able to get it to work as it is intended to. (Quite well i might add).  This is essentially a quick guide to others who may encounter this  problem to make it less painful and time consuming. Hopefully this will serve as a great help.
[/LIST]

sorry to resurrect your post after a year, unfortunately am having trouble with your instructions. my printer is an epson stylus photo px730wd (artisan 730 if you're american). i'm using the gimp 2.6 and it appears it comes pre-loaded with a cd label template, when i go to open an image though a new window opens up instead and i can't duplicate your reference points since the figures keep changing when i move on to the next box, i'm hoping you can help me out.

---

