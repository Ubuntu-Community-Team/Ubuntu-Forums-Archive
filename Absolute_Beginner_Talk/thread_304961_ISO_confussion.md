---
title: "ISO confussion"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by lordvolo on 2006-11-22
Im running Xubuntu and i need another desktop CD, I've downloaded the ISO image but theres a problem, there's two images one has an .ISO extention and the second has an .ISO.part extention which one do i burn with xfburn?

---

### Post by JShadow on 2006-11-22
You should be burning the .ISO

Did you use firefox to download it? Firefox usually creates the .part files as a temporary place to store the file as it is being downloaded. They're usually deleted when the download is complete.

---

### Post by geolr on 2006-11-22
Hi there,

did you use some Bittorrent-client to download?
Did it say the download is completely done without any problems?
If so go ahead and burn the .iso and not the .iso.part since this is only the partially finished download - as far as I know.

Also you should check the md5sum of your iso:
Download this file[URL="http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/MD5SUMS"]
http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/MD5SUMS[/URL]
for the Checksum of your particular CD. Save to the same folder as your iso-file. Then run in a Terminal:
md5sum -c MD5SUMS

You will get prompted if the file is corrupted.

For help check: 
man md5sum

Hope that helps!

---

