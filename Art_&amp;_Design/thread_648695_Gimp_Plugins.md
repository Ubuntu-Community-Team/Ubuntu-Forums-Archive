---
title: "Gimp Plugins"
date: 2007-12-23
forum: Art &amp; Design
---

### Post by melfindlay on 2007-12-23
Can anyone help with installing Gimp plugins?:confused: There is a list of plugins that I would like to download/install some plugins from at [http://www.techzilo.com/gimp-plugins/](http://www.techzilo.com/gimp-plugins/). However, I am not sure how to go about doing so? 

Thanks.

---

### Post by smartboyathome on 2007-12-23
Install them by saving the svm files to (your home directory)/.gimp-2.4/plug-ins/

---

### Post by omega_user on 2007-12-25
unfortunately, a lot of these plug-ins are for 2.2 Gimp, whereas the newer 2.4 is now the standard with Gutsy and other *Nix's. Not sure if that makes a difference for a lot of them though

---

### Post by smartboyathome on 2007-12-25
I heard that GIMP 2.4 broke 2.2 plugins, but I guess the only way to find out if it is broken is to try it out.

---

### Post by omega_user on 2007-12-25
yeah, sorry other readers if me and smartboy weren't able to provide much insight, testing is really the only way to find out with these

---

### Post by melfindlay on 2007-12-25
That's okay. Thank you for your help though. I did test them out and unfortunately they don't work. I wish they did though. It would make some things for my photography shots a little easier.

---

### Post by anrom on 2008-05-14
This may be a silly question, but I've added a couple of plug-ins to Gimp 2.4.5, but I'm not sure I'm doing it the right way.  In my home directory, I checked View Hidden Files and just moved the .scm files into plug-ins.  The curious thing is that all 34 folders in .gimp-2.4 are empty, so I'm not sure what's going on at all.  

I've been using Gimp and it's working fine in Ubuntu 8.04.  Why are the Gimp folders empty then?  And have I really added the new plug-ins to the right place?  Thanks for any help.

---

### Post by MetalMusicAddict on 2008-05-14
Here 's how to install the .scm files.

Install libgimp2.0-dev:
**sudo apt-get install libgimp2.0-dev** (That will get you the needed "gimptool")

If you want to install the script for everyone do:
**sudo gimptool-2.0 --install-admin-script /path/to/.scm**

For just your user:
**gimptool-2.0 --install-script /path/to/.scm**

For more concise info: [LINK]("http://www.gimp.org/man/gimptool-2.0.html")

---

### Post by anrom on 2008-05-14
Ok, I've installed libgimp2.0-dev successfully.  When I install the script .scm I get Error: Couldn't find file to build/install/uninstall


I tried it just as you wrote it and also using the name of the plug-in.  the plug-in file in on my desktop.

---

### Post by anrom on 2008-05-14
Fixed it.  I put the .scm files in home folder/.gimp.2.2/scripts instead of plug-ins.  Then I went to the Gimp toolbox and in Xtns/Script-Fu I clicked Refesh Scripts.  I was then able to use the plug-ins.  

BTW, I got the above info here [http://wiki.osphoto.org/index.php/GIMP_scripts]("http://wiki.osphoto.org/index.php/GIMP_scripts") after browsing the Gimp users group over at Flickr.  

I don't know if installing libgimp2.0-dev enabled the plug-ins, or simply moving them into the scripts folder and refreshing scripts did.  I'm just glad they work.  

I still don't understand why all the Gimp folders appear empty in my hidden files, but some mysteries are beyond noobs like me.

---

### Post by whiteraven on 2008-05-14
> I still don't understand why all the Gimp folders appear empty in my hidden files...
The GIMP install routine creates those directories for your personal storage of plugins, scripts, brushes, etc. Whenever you download a plugin, script, etc., simply place the file in the appropriate directory under your .gimp.2.x in your home drectory. One major benefit of doing it this way is that the added files will not be lost if you happen to upgrade or reinstall GIMP.

Hope that was clear enough?

---

