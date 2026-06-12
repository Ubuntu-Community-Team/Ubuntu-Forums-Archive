---
title: "On calender with Rainlender"
date: 2007-12-29
forum: Art &amp; Design
---

### Post by delilahjed44 on 2007-12-29
Hello, I downloaded both 1 and 2 of Rainlender, I am using Ubuntu 710, here is the error I am receiveing,

An error occured while extracting
Command line input

When I double clk it sais
no application sutiable for automatic installation.

I dont know what to use in Beta, if there is anything to use, is anyone else using this, I dont like evolution, havent used it but I dont care for it.


__________________

Can I Use the KDE PIM calender thing? I have a gnome desktop not KDE, and is this in the repos?

Sherri

---

### Post by smartboyathome on 2007-12-29
I use Sunbird, it is really nice. You could try it or even the Lightning extention for Thunderbird.

---

### Post by delilahjed44 on 2007-12-30
> **smartboyathome said:**
> I use Sunbird, it is really nice. You could try it or even the Lightning extention for Thunderbird.

  Wow! cool wallpapers in your blog, I like the black and white one completed in Gimp.  Ok I am going to do a search on this sundbird, so if I cant get it going I will be back, I need calender bad, I have it in windows on another pc, but I want to use Ubuntu eventually on both.

 Thanks 
 Sherri

---

### Post by delilahjed44 on 2007-12-30
Ok, I found Sunbird, downloaded the Linux 86, because anything else that gives as far as finding it in the parent file or any of those files it was indicating is something I have not done nor understand.  What I did try to do, I chose ( run in termin) this file > run-mozilla.sh and it the window opens then disapears.  I dont see the calender anywhere so I am not sure its installed just yet.  I extracted the files to my home folder.

  ??

   Thanks 
    Sherri

---

### Post by smartboyathome on 2007-12-30
> **delilahjed44 said:**
> Ok, I found Sunbird, downloaded the Linux 86, because anything else that gives as far as finding it in the parent file or any of those files it was indicating is something I have not done nor understand.  What I did try to do, I chose ( run in termin) this file > run-mozilla.sh and it the window opens then disapears.  I dont see the calender anywhere so I am not sure its installed just yet.  I extracted the files to my home folder.

  ??

   Thanks 
    Sherri

You didn't install it yet if you ran that. You can run it from within that folder by double clicking on the file named sunbird. If you want to install it, try reading the readme.

Also, thanks for the compliment on the wallpaper. :)

---

### Post by delilahjed44 on 2007-12-30
Install Sunbird Under Ubuntu

    * download sunbird linux version at mozilla website
    * unzip into /opt/sunbird
    * sudo gedit /usr/share/applications/sunbird.desktop < this gave me an open text, empty???

      Below is not clear to me, as I have not used the terminal very often and do now understand exactly what this requirement below is actually asking??? 
Does this info go into the empty text note it gave me or in the terminal? 

      [Desktop Entry]
      Name=Sunbird
      Comment=Calendar Application
      Exec=/opt/sunbird/sunbird
      Icon=/opt/sunbird/chrome/icons/default/default.xpm
      Terminal=false
      Type=Application
      Categories=Application;Office;
    * If meet 'Segmentation fault' error, Just add this line of code after first line on sunbird executable script:
      GTK_IM_MODULE=scim-bridge

    reason: Scim cause this problem and it is also happened to firefox, thunderbird, ...

    * Google Calendar:

    download and install 'Provider for Google Calendar' add-on. Use 'subscript to remote calendar' to add google calendar. When asks for Location use private address, either XML or iCal format.

Sherri

---

### Post by smartboyathome on 2007-12-30
Ok, here are some terminal commands to help you (note, the files you extracted from the sunbird file you got off of the site need to be in your home directory):
```
sudo cp ~/sunbird /opt
```
This puts your extracted files into the /opt directory.
```
sudo gedit /usr/share/applications/sunbird.desktop
```
Yes, this is supposed to open an empty text file. Put the following in the file:
```
[Desktop Entry]
Name=Sunbird
Comment=Calendar Application
Exec=/opt/sunbird/sunbird
Icon=/opt/sunbird/chrome/icons/default/default.xpm
Terminal=false
Type=Application
Categories=Application;Office;
```

If you get a segmentation fault when trying to run Sunbird, run this command:
```
sudo gedit /opt/sunbird/sunbird
```
And insert this on a new line after the first in the file that comes up:
```
GTK_IM_MODULE=scim-bridge
```

Now you should be able to use it.

---

