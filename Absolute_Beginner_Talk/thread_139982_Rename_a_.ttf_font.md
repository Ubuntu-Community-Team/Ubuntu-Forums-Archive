---
title: "Rename a .ttf font"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by Yumi on 2006-03-05
I downloaded the barcode39.ttf and installed it in /usr/share/fonts/truetype. All seems ok. But in the program font selection it is listed as "New" not the filename. Where can I change this font name?
Michael

---

### Post by Pragmatist on 2006-03-05
Read this Ubuntu HowTo:
[https://wiki.ubuntu.com/FontInstallHowto?highlight=%28font%29#head-a36b764c435d55ebe36e860f84867df303f559c7](https://wiki.ubuntu.com/FontInstallHowto?highlight=%28font%29#head-a36b764c435d55ebe36e860f84867df303f559c7)
Under Installing TrueType fonts the non-GUI way

>  ...it seems to work even though it *might not be the best way* to do things... Presuming you have .ttf files in your home directory:

cd /usr/share/fonts/truetype     (presumably this could be done in /usr/local/share/fonts/truetype, instead) 
sudo mkdir myfonts
cd myfonts
sudo cp ~/*.ttf .
sudo chown root.root *.ttf
sudo mkfontdir
cd ..
fc-cache 


There are other probably better ways too, so read the whole HowTo.

---

