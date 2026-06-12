---
title: "messed-up /etc/gnome/defaults.list and slow performance on startup after dual monitor"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by nosferatu_linux on 2007-12-20
Hi, i installed Ubuntu 7.10 today, and had a hell of a time as someone who is fresh from windows configuring all the settings. Everything was going smoothly except for my nvidia 7600gt card drivers. I opened restricted drivers, and there is my driver sitting there (at least i think it is the right one). 
So i enable it, restart, and everything is working great.
Then i decide to hook up my second monitor like i had on my windows machine, and then the trouble begin... 

first time reboot the computer froze on the start-up screen.
i restarted 3 or 4 times and same story. then i went into recovery mode trying to run init 5 from there and see if that works - it didnt. 
i decided to take things into my own hands and looked through /etc and then /gnome/defaults.list to see if there is anything there that might triger the driver, and being the smartass that i am i used vc (i tihnk) as the editor and didnt realise what happened when it opened, it looked like it wasnt editing but just viewing the file, i tried pressing key's nothing happened, so i went to the botom and pressed delete, and ended up erasing some statements, after which i pressed ctrl alt delete to restart hoping that it wouldnt save, but i think it did.
then i fired up my lappy and googled until i found some command to disable the driver. the init 5 worked, but extramly slow so i restarted only to discover that the generic logon is very slow aswell.
i am able to login now, and got the dual boot to work, but it really troubles me that its very slow on startup, and the fact that i erased sometihng from the default.list

Please help!

---

### Post by nowshining on 2007-12-20
hehe, here is a copy of mine, :)

the contents of mine are below however u gave myself an idea :)

do the following on a computer that works

create a new document and rename it defaults.list and open it up with gedit and copy the contents seen below. :) save and then sudo cp or sudo mv it in there.

example:

to copy

sudo cp /media/thumb/defaults.list /etc/gnome/defaults.list

to

mv
sudo mv /media/thumb/defaults.list /etc/gnome/defaults.list



```


[Default Applications]
application/csv=ooo-calc.desktop
application/excel=ooo-calc.desktop
application/msexcel=ooo-calc.desktop
application/msword=ooo-writer.desktop
application/ogg=totem.desktop
application/pdf=evince.desktop
application/postscript=evince.desktop
application/rtf=ooo-writer.desktop
application/tab-separated-values=ooo-calc.desktop
application/vnd.lotus-1-2-3=ooo-calc.desktop
application/vnd.ms-excel=ooo-calc.desktop
application/vnd.ms-word=ooo-writer.desktop
application/vnd.rn-realmedia=totem.desktop
application/vnd.sun.xml.calc=ooo-calc.desktop
application/vnd.sun.xml.calc.template=ooo-calc.desktop
application/vnd.sun.xml.draw=ooo-impress.desktop
application/vnd.sun.xml.draw.template=ooo-impress.desktop
application/vnd.sun.xml.math=ooo-math.desktop
application/vnd.sun.xml.writer=ooo-writer.desktop
application/vnd.sun.xml.writer.template=ooo-writer.desktop
application/vnd.sun.xml.writer.global=ooo-writer.desktop
application/vnd.oasis.opendocument.formula=ooo-math.desktop
application/vnd.oasis.opendocument.graphics=ooo-draw.desktop
application/vnd.oasis.opendocument.graphics-template=ooo-draw.desktop
application/vnd.oasis.opendocument.presentation=ooo-impress.desktop
application/vnd.oasis.opendocument.presentation-template=ooo-impress.desktop
application/vnd.oasis.opendocument.spreadsheet=ooo-calc.desktop
application/vnd.oasis.opendocument.spreadsheet-template=ooo-calc.desktop
application/vnd.oasis.opendocument.text=ooo-writer.desktop
application/vnd.oasis.opendocument.text-template=ooo-writer.desktop
application/vnd.oasis.opendocument.text-web=ooo-writer.desktop
application/vnd.oasis.opendocument.text-master=ooo-writer.desktop
application/vnd.sun.xml.impress=ooo-impress.desktop
application/vnd.sun.xml.impress.template=ooo-impress.desktop
application/vnd.stardivision.calc=ooo-calc.desktop
application/vnd.stardivision.draw=ooo-draw.desktop
application/vnd.stardivision.impress=ooo-impress.desktop
application/vnd.stardivision.math=ooo-math.desktop
application/vnd.stardivision.writer=ooo-writer.desktop
application/mspowerpoint=ooo-impress.desktop
application/vnd.ms-powerpoint=ooo-impress.desktop
application/vnd.wordperfect=ooo-writer.desktop
application/wordperfect=ooo-writer.desktop
application/x-123=ooo-calc.desktop
application/x-abiword=abiword.desktop
application/x-applix-spreadsheet=ooo-calc.desktop
application/x-ar=file-roller.desktop
application/x-arj=file-roller.desktop
application/x-bzip-compressed-tar=file-roller.desktop
application/x-bzip=file-roller.desktop
application/x-cd-image=nautilus-cd-burner-open-iso.desktop
application/x-compressed-tar=file-roller.desktop
application/x-compress=file-roller.desktop
application/x-deb=gdebi.desktop
application/x-debian-package=gdebi.desktop
application/x-dos_ms_excel=ooo-calc.desktop
application/x-ear=file-roller.desktop
application/x-excel=ooo-calc.desktop
application/x-extension-m4a=totem.desktop
application/x-extension-mp4=totem.desktop
application/x-flac=totem.desktop
application/x-glade=glade-2.desktop
application/x-gnumeric=gnumeric.desktop
application/x-gtar=file-roller.desktop
application/x-gzip=file-roller.desktop
application/x-gzpostscript=evince.desktop
application/xhtml+xml=firefox.desktop
application/x-jar=file-roller.desktop
application/x-java-archive=file-roller.desktop
application/x-lha=file-roller.desktop
application/x-lhz=file-roller.desktop
application/xls=ooo-calc.desktop
application/x-lzop=file-roller.desktop
application/x-matroska=totem.desktop
application/x-mps=ooo-calc.desktop
application/x-ms-excel=ooo-calc.desktop
application/x-msexcel=ooo-calc.desktop
application/x-ogg=totem.desktop
application/x-oleo=ooo-calc.desktop
application/x-perl=gedit.desktop
application/x-planperfect=ooo-calc.desktop
application/x-quattropro=ooo-calc.desktop
application/x-rar-compressed=file-roller.desktop
application/x-rar=file-roller.desktop
application/x-rpm=file-roller.desktop
application/x-sc=ooo-calc.desktop
application/x-shockwave-flash=totem.desktop
application/x-sylk=ooo-calc.desktop
application/x-tar=file-roller.desktop
application/x-war=file-roller.desktop
application/x-xbase=ooo-calc.desktop
application/x-xls=ooo-calc.desktop
application/x-zip-compressed=file-roller.desktop
application/x-zip=file-roller.desktop
application/x-zoo=file-roller.desktop
application/zip=file-roller.desktop
audio/mpeg=totem.desktop
audio/mpegurl=totem.desktop
audio/vnd.rn-realaudio=totem.desktop
audio/x-flac=totem.desktop
audio/x-m4a=totem.desktop
audio/x-mp3=totem.desktop
audio/x-mpeg=totem.desktop
audio/x-mpegurl=totem.desktop
audio/x-ms-asf=totem.desktop
audio/x-ms-asx=totem.desktop
audio/x-ms-wax=totem.desktop
audio/x-pn-aiff=totem.desktop
audio/x-pn-au=totem.desktop
audio/x-pn-realaudio-plugin=totem.desktop
audio/x-pn-realaudio=totem.desktop
audio/x-pn-wav=totem.desktop
audio/x-pn-windows-acm=totem.desktop
audio/x-real-audio=totem.desktop
audio/x-scpls=rhythmbox.desktop
audio/x-wav=totem.desktop
image/bmp=eog.desktop
image/gif=eog.desktop
image/jpeg=eog.desktop
image/jpg=eog.desktop
image/pjpeg=eog.desktop
image/png=eog.desktop
image/svg+xml=eog.desktop
image/tiff=eog.desktop
image/vnd.rn-realpix=totem.desktop
image/x-bmp=eog.desktop
image/x-gray=eog.desktop
image/x-icb=eog.desktop
image/x-ico=eog.desktop
image/x-png=eog.desktop
image/x-portable-anymap=eog.desktop
image/x-portable-bitmap=eog.desktop
image/x-portable-graymap=eog.desktop
image/x-portable-pixmap=eog.desktop
image/x-psd=gimp-2.2.desktop
image/x-xbitmap=eog.desktop
image/x-xpixmap=eog.desktop
inode/directory=nautilus-folder-handler.desktop
misc/ultravox=totem.desktop
multipart/x-zip=file-roller.desktop
text/abiword=abiword.desktop
text/comma-separated-values=ooo-calc.desktop
text/csv=ooo-calc.desktop
text/html=firefox.desktop
text/plain=gedit.desktop
text/richtext=abiword.desktop
text/rtf=ooo-writer.desktop
text/spreadsheet=ooo-calc.desktop
text/tab-separated-values=ooo-calc.desktop
text/x-comma-separated-values=ooo-calc.desktop
text/x-chdr=gedit.desktop
text/x-csrc=gedit.desktop
text/x-dtd=gedit.desktop
text/x-java=gedit.desktop
text/mathml=gedit.desktop
text/x-python=gedit.desktop
text/x-sql=gedit.desktop
text/xml=firefox.desktop
video/dv=totem.desktop
video/mp4=totem.desktop
video/mpeg=totem.desktop
video/msvideo=totem.desktop
video/quicktime=totem.desktop
video/vnd.rn-realvideo=totem.desktop
video/x-anim=totem.desktop
video/x-avi=totem.desktop
video/x-flc=totem.desktop
video/x-fli=totem.desktop
video/x-mpeg=totem.desktop
video/x-ms-asf=totem.desktop
video/x-msvideo=totem.desktop
video/x-ms-wmv=totem.desktop
video/x-nsv=totem.desktop
x-directory/normal=nautilus-folder-handler.desktop
zz-application/zz-winassoc-xls=ooo-calc.desktop

  
```

---

