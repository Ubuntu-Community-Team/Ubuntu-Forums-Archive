---
title: "Gimpshop help and resizing images for the web"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2006-12-18
1. After installing Gimpshop I cannot see the help files  and instead get the following message.

"The GIMP help files are not installed.

Could not open '/usr/local/share/gimp/2.0/help/en/gimp-help.xml' for reading: No such file or directory

Please check your installation."

Can anyone help please.

--------------------------------------------------------------------
2. I also wonder how to resize an image  for a web page ( to around 20 - 30 KB's). using Gimpshop? Can't seem to get it lower than Megabite sizes

---

### Post by annda on 2006-12-18
Ad 1. search Synaptics for gimp and install the appropriate gimp-help file.

Ad 2. make sure that after resizing the file you save it as jpeg/gif/png - not the gimp format (includes layers and other extra info, plus it's not compressed). i forgot that once or twice and was irritated by the image file size as well...

---

### Post by ferg on 2006-12-18
1. Here's a link to the GIMP documentation online... [http://docs.gimp.org/en/](http://docs.gimp.org/en/)
But I imagine you probably want it local, so if you open terminal and type:

```
sudo apt-get install gimp-help-en
```Then follow that through it will install all the help files you need :) The local documentation runs in your browser and, as far as I know, is literally a port of online helps files.

2. Depends on what format you are saving to. JPG for example, when you save you have a quality slider you can move about. Obviously the image will look worse if you decrease the quality too much but it will reduce the file size quite significantly. Reducing the pixel size will reduce the file size - although I assume you know this. ;)

Hope this helps,

Ferg

---

### Post by a.v.l on 2006-12-18
> **annda said:**
> Ad 1. search Synaptics for gimp and install the appropriate gimp-help file.

Ad 2. make sure that after resizing the file you save it as jpeg/gif/png - not the gimp format (includes layers and other extra info, plus it's not compressed). i forgot that once or twice and was irritated by the image file size as well...

Thanks for the help I've managed to resize my images as you've suggested...........so easy when you know how.

---

### Post by a.v.l on 2006-12-18
> **ferg said:**
> 1. Here's a link to the GIMP documentation online... [http://docs.gimp.org/en/](http://docs.gimp.org/en/)
But I imagine you probably want it local, so if you open terminal and type:

```
sudo apt-get install gimp-help-en
```Then follow that through it will install all the help files you need :) The local documentation runs in your browser and, as far as I know, is literally a port of online helps files.

Hope this helps,

Ferg


Thanks for your help, but when I copied  the above into the terminal a few things seem to happen and it stops at the following.

------@------- -desktop:~$ sudo apt-get install gimp-help-en
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed
  gimp-help-en
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 444kB of archives.
After unpacking 3764kB of additional disk space will be used.
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main gimp-help-en 2+0.9-1 [444kB]
Fetched 444kB in 2s (156kB/s)
debconf: Unable to initialise frontend: Kde
debconf: (Unable to load Qt -- is libqt-perl installed?)
debconf: falling back to frontend: Dialog
Selecting previously deselected package gimp-help-en.
(Reading database ... 130141 files and directories currently installed.)
Unpacking gimp-help-en (from .../gimp-help-en_2+0.9-1_all.deb) ...
Setting up gimp-help-en (2+0.9-1) ...

 I've looked but I'm still unable to locate the help files where might I find them on my PC please?

Thanks for the web link to the help files they will come in handy for the moment.

---

### Post by ferg on 2006-12-18
To get to the help files (if they are installed) open the GIMP and select Help > Help from the top bar. If you still get that error open Synaptic and search for gimp-help-en and then install the package that way. That command should work though I've used it before... 

Ferg :)

---

### Post by a.v.l on 2006-12-18
> **ferg said:**
> To get to the help files (if they are installed) open the GIMP and select Help > Help from the top bar. If you still get that error open Synaptic and search for gimp-help-en and then install the package that way. That command should work though I've used it before... 

Ferg :)

Thanks once again, I'm getting the same message as before when going to the help top bar in Gimpshop as I did before.  I've also check the repositories and I have gimp-help-en already installed.  I'm completely lost now.

---

### Post by bsell on 2006-12-18
> **a.v.l said:**
> Thanks once again, I'm getting the same message as before when going to the help top bar in Gimpshop as I did before.  I've also check the repositories and I have gimp-help-en already installed.  I'm completely lost now.

The GIMP Help files are unavailable in GIMPshop. They are there, but the registry points to GIMPshop and not GIMP so the files don't load. 

The change in the UI makes the Help files unhelpful anyway. You might want to go to the library and pick up a Photoshop tutorial as GIMPshop closely resembles Photoshop.

---

### Post by a.v.l on 2006-12-19
> **bsell said:**
> The GIMP Help files are unavailable in GIMPshop. They are there, but the registry points to GIMPshop and not GIMP so the files don't load. 

The change in the UI makes the Help files unhelpful anyway. You might want to go to the library and pick up a Photoshop tutorial as GIMPshop closely resembles Photoshop.

Thanks for this information, I've also  tried Gimpshop on my works PC and discovered the same situation there, as you say no help files in Gimpshop.  I've also discovered that I cannot access my scanner from within Gimpshop by going File > Aquire.  

Would I be better off with Gimp?

---

### Post by bsell on 2006-12-19
> **a.v.l said:**
> Thanks for this information, I've also  tried Gimpshop on my works PC and discovered the same situation there, as you say no help files in Gimpshop.  I've also discovered that I cannot access my scanner from within Gimpshop by going File > Aquire.  

Would I be better off with Gimp?

Is your scanner configured correctly? I've used my scanner (Epson) with both the GIMP and GIMPshop. You may need to run ```
sane-find-scanner
``` to see if your scanner is supported. 

If you use the GIMP you will be able to access the excellent Help files if you don't mind the UI. You can also download Grokking the GIMP (an ebook) from the repositories as a user's guide. 

Akkana Peck has written an excellent book *Beginning GIMP* (Apress) which has been recently published and "based on the latest GIMP 2.4. release" (cover blurb). I highly recommend it.

---

### Post by ice60 on 2006-12-19
you might need to do this to get the help files installed
```
sudo aptitude install libqt-perl
``` then try installing the help file again with 
```
sudo aptitude install gimp-help-en
```
if that doesn't work maybe you need to add some repos, i'm not sure, someone else will know :)

---

### Post by a.v.l on 2006-12-20
> **bsell said:**
> Is your scanner configured correctly? I've used my scanner (Epson) with both the GIMP and GIMPshop. You may need to run ```
sane-find-scanner
``` to see if your scanner is supported. 

If you use the GIMP you will be able to access the excellent Help files if you don't mind the UI. You can also download Grokking the GIMP (an ebook) from the repositories as a user's guide. 

Akkana Peck has written an excellent book *Beginning GIMP* (Apress) which has been recently published and "based on the latest GIMP 2.4. release" (cover blurb). I highly recommend it.

Have considered all things I've now removed Gimpshop and will be using Gimp instead.  Since reverting to Gimp, my scanner now works as do the help files.   Thanks very much for your help.

---

### Post by a.v.l on 2006-12-20
[QUOTE=bsell;1908526]Is your scanner configured correctly? I've used my scanner (Epson) with both the GIMP and GIMPshop. You may need to run ```
sane-find-scanner
``` to see if your scanner is supported. 

If you use the GIMP you will be able to access the excellent Help files if you don't mind the UI. You can also download Grokking the GIMP (an ebook) from the repositories as a user's guide. 

I've downloaded Grokking the GIMP but cannot find it.  Where should I look please?

---

### Post by UbuWu on 2006-12-20
> **a.v.l said:**
> 
2. I also wonder how to resize an image  for a web page ( to around 20 - 30 KB's). using Gimpshop? Can't seem to get it lower than Megabite sizes

All you need: [http://quickthumbnail.com/](http://quickthumbnail.com/)

---

### Post by bsell on 2006-12-20
> **a.v.l said:**
> 

I've downloaded Grokking the GIMP but cannot find it.  Where should I look please?

The files are viewable in your web browser (like the GIMP's Help files). Paste this into your browser's address bar: ```
file:///**usr/share/doc/grokking-the-gimp/html/**Grokking_the_GIMP.html
```

The file location is bolded. The tutorial is pretty old (2000). You can find excellent introductory tutorials about the latest release on the web. Download the HTML files for offline viewing.

---

