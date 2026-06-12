---
title: "Where to put codecs?"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by red van man on 2006-08-03
Hello all,
My (pre-ubuntu) music collection consists of MP3s and WMAs and I'd like to play them on my new OS (unsurprisingly).  "Simple", you say, "just install the codecs from EasyUbunu" or some such.  The problem is this (you may want to sit down): I DON'T HAVE AN INTERNET CONNECTION!  At least, not at home, although I can use the internet at work, no hassle.
So...could I download the codecs, save them to a USB stick?  Is it then just a matter of saving them to the appropriate directory?  Please bear in mind I am very much a casual user and brand new to Linux and terminals and what-have-you.

---

### Post by carlosqueso on 2006-08-03
[http://packages.ubuntu.com](http://packages.ubuntu.com) has debs for most things (just grab all of the debs in the wiki [https://help.ubuntu.com/community/RestrictedFormats#head-1340337f2ca1d0c54900935468515ba7630fcc59](https://help.ubuntu.com/community/RestrictedFormats#head-1340337f2ca1d0c54900935468515ba7630fcc59) )  
For WMA/WMV you can (if it's legal where you live ;-)) use [http://www.ubuntuforums.org/showpost.php?p=411934&postcount=12](http://www.ubuntuforums.org/showpost.php?p=411934&postcount=12) if you don't want to download from the site in the wiki.  

Once you get those deb files, copy them to your home machine and install them by opening up a terminal and typing (where <package name> is the name of the file) ```
sudo dpkg -i <package name>
```  I've heard that in Dapper, you can also install them by double-clicking, but haven't tried that yet.

---

### Post by red van man on 2006-08-04
Great stuff Carlos, I'll give it a go when I get back to work!

---

### Post by Drakkor on 2006-08-04
I can confirm in 6.0.6 you **can** install .deb files by double-clicking !
:p

---

### Post by LORD_PoLvO on 2006-08-04
yes there is a program in 6.06 so deb files can be instaleed just liek u install an .exe in windows (double-click) also i sugest you install using apt not from debian packages follow this howto verry simple just gives you commands for every restricted codec and non free adon you could think of [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

