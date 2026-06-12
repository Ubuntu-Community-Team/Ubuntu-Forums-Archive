---
title: "[SOLVED] What program to make cd &amp;amp; dvd labels"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by jryprt on 2008-01-18
I have a lightscribe label burner , what do I use to make labels.
I have the burning software I just need to design the label.
I looked a gimp & open office do not see templates.

---

### Post by stoodleysnow on 2008-01-18
I have an LG lightscribe drive and need to know this too.:confused:

---

### Post by Stunt Double on 2008-01-18
KBarcode Label Editor

---

### Post by disturbed1 on 2008-01-18
You need first the hp lightscribe system drivers ( [http://www.lightscribe.com/downloadSection/linux/index.aspx?id=814](http://www.lightscribe.com/downloadSection/linux/index.aspx?id=814) ), optional is the simple labler ( [http://www.lightscribe.com/downloadSection/linux/index.aspx?id=815](http://www.lightscribe.com/downloadSection/linux/index.aspx?id=815) ). The simple labler is very simple, doesn't have the option to import your own pictures or templates. To print pictures on the disc, I use LaCie's utility ( [http://www.lacie.com/support/drivers/driver.htm?id=10094](http://www.lacie.com/support/drivers/driver.htm?id=10094) ). If you have hp's lightscribe system software, you do not need LaCie's host software. You need alien and rpm tools to convert the RPM to deb.
```

fakeroot alien -d 4L-1.0-r6.i586.rpm
sudo dpkg -i 4l_1.0-1_i386.deb
```It gets installed to /usr/4L/ type 4L-gui to run the program.

For label design, I use Gimp with script-fu. Get the script from here [http://www.shallowsky.com/software/cdplugins/](http://www.shallowsky.com/software/cdplugins/) right click CDlabel2.scm and save. This file goes in /$HOME/.gimp2.x/scripts. Launch Gimp, create a new image, then click Script-Fu and apply the mask. Or you can open an image and apply the mask to it.

---

### Post by jryprt on 2008-01-18
Ok I got it. [QUOTE=]For label design, I use Gimp with script-fu. Get the script from here [http://www.shallowsky.com/software/cdplugins/](http://www.shallowsky.com/software/cdplugins/) right click CDlabel2.scm and save. This file goes in /$HOME/.gimp2.x/scripts. Launch Gimp, create a new image, then click Script-Fu and apply the mask. Or you can open an image and apply the mask to it.[/QUOTE]  This worked & I did a test 
It works on HP 740 . It took 17 mins. to do a happy face (see screenshot).

FOR THE SOFTWARE DO THE FOLLOWING.
 Open Terminal
#1 Code this one at a time.```
sudo su
apt-get install rpm
apt-get install alien
apt-get install libpng3
apt-get install libqt3-mt
exit
```
#2 Download [This](http://www.lightscribe.com/downloadSection/linux/index.aspx?id=814)   
Is a .deb
#3 Download [This](http://www.lightscribe.com/downloadSection/linux/index.aspx?id=815)
Is a .deb  The simple labler is very simple.
To print pictures on the disc use 4L
#4 Go [Here](http://www.lacie.com/support/drivers/driver.htm?id=10094)
Right click on the Linux(Download) than  Save Link As  (box come up) watch where you save it (mine saved in a strange place) .
#5 Go to where you saved it & copy it to your Desktop.
#6 Open Terminal ```
fakeroot alien -d 4L-1.0-r6.i586.rpm
``` It Might say you need fackeroot if so  ```
sudo apt-get install fakeroot
```  Then agine ```
fakeroot alien -d 4L-1.0-r6.i586.rpm
``` .
#7 ```
sudo dpkg -i 4l_1.0-1_i386.deb
```  do password it will install.
It gets installed to /usr/4L/  Close the terminal .
To start it in the terminal ```
4L-gui
```

---

### Post by reiki on 2008-01-27
You can also use Inkscape and I found it easier to figure out the curved text. I made a template. I made it for ME but a few people have asked for it. I'll attach it. Instructions are in a layer in the svg...

After you install Inkscape you'll have a .inkscape directory in your home directory.

cd .inkscape
(don't forget the dot before inkscape... it's a hidden folder)
mkdir templates

now copy the attached file into that templates directory.

Restart Inkscape, choose File -> New and you should see A_Lightscribe_Disk" at the top of the list.

Enjoy!

---

