---
title: "What do I need to be able to veiwe.wmv video?"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by bvexen2 on 2006-06-14
Please help....beginner here!

---

### Post by givré on 2006-06-14
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) ;)

---

### Post by bvexen2 on 2006-06-14
I may be an idiot but I still don't see what I need to do.....

---

### Post by Jucato on 2006-06-14
You have to download and install the package called w32codecs. The download link is located in that page. Scroll down to the part about Windows media (or use your browser's search function and look for "wmv")

---

### Post by nitricacid on 2006-06-14
You need to open a bash window and use this code to install codecs

```
sudo wget -c ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.4_i386.deb
```

After that says done then use  this code to install the package

```
sudo dpkg -i w32codecs_20050412-0.4_i386.deb
```
-----

Would anyone happen to know why I still can't view .wmv files after installing this?

---

### Post by Kilz on 2006-06-14
[QUOTE=nitricacid]You need to open a bash window and use this code to install codecs

```
sudo wget -c ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.4_i386.deb
```

After that says done then use  this code to install the package

```
sudo dpkg -i w32codecs_20050412-0.4_i386.deb
```
-----

Would anyone happen to know why I still can't view .wmv files after installing this?[/QUOTE]

Maybe its a wmv 10 file?

---

### Post by harishg on 2006-06-14
Google for easyubuntu and in multimedia of that install the w32 and restriced formats.You are ready to go

---

### Post by tommcd on 2006-06-15
Assuming you installed the codecs correctly, get Mplayer from synaptic. Then download a .wmv file, right-click on it a nd choose 'properties', under the 'open with' tab, set it to open with Mplayer. Then each time you view a .wmv file it will use Mplayer. I can't watch .wmv files with Totem, I'm not sure if Totem supports .wmv, so I use Mplayer.

---

### Post by bionnaki on 2006-06-15
I think totem will play them if you rename the extension from ".wmv" to ".asf" - could be wrong though. try it.

---

### Post by Jagot on 2006-06-15
WMV's work fine in Totem for me after installing the codecs.  No need to rename the file.

---

### Post by Christmas on 2006-06-15
[quote=nitricacid]Would anyone happen to know why I still can't view .wmv files after installing this?[/quote]
I don't know exactly what it means but from the Restricted Formats page on Wiki:
> WMV files encoded with DRM (Digital Rights Management) are not playable by the codecs.

---

### Post by Jagot on 2006-06-15
WMV files encoded with DRM will essentially be paid-for content that is copyrighted, or protected in some way.

---

### Post by PowerWCRulez on 2006-07-07
download the codecs first then open the gxine works prefectly either wmv or asf.

How I set the default to gxine for wmv and asf run from the ff browser?

---

