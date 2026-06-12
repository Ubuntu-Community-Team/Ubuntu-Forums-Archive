---
title: "I cant hear a mp3 and i cant watch any movie"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by picallo on 2006-07-06
I installed yesterday Ubuntu 6.06 in my computer. But i cant hear any mp3 or watch any movie. Probably i need to install codecs, but i dont know what, where can i find them and how can i install them.

---

### Post by jdusablon on 2006-07-06
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

Follow that. It should help with mp3 and other common formats.

---

### Post by stevenash on 2006-07-06
I had the same question when I switched to Ubuntu.  Go to the link below and follow the directions.  Come back if you need more help:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by picallo on 2006-07-06
the main problem in my case, is that i have to download all manually because i havent a good internet conection at home (only 56 and not yet configured). Where can i find the listed packages?

---

### Post by Iarwain ben-adar on 2006-07-06
Well,
to give another way to get support:

[http://packages.ubuntu.com/dapper/libs/libxine-extracodecs](http://packages.ubuntu.com/dapper/libs/libxine-extracodecs)
(this is the 386 version : [http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmultiverse%2Fx%2Fxine-extracodecs%2Flibxine-extracodecs_1.1.1%2Bubuntu1-2_i386.deb&md5sum=5512ee45d3d0c9dd30f2588512729aa8&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmultiverse%2Fx%2Fxine-extracodecs%2Flibxine-extracodecs_1.1.1%2Bubuntu1-2_i386.deb&md5sum=5512ee45d3d0c9dd30f2588512729aa8&arch=i386&type=main) )
Here you download the libxine-extracodecs (normally to your Desktop)
and when it is downloaded, right click on the .deb, and select something like "install".
After you type your password, it installs, and you have mp3 support :D


Iarwain

---

### Post by picallo on 2006-07-06
thanks, i found a mirror, i will try later at home.
Btw another question. I istalled the 386 version of ubuntu (what i got in a magazine) but i have amd64 which package should i install?

---

### Post by Iarwain ben-adar on 2006-07-06
Now you should install the 386...

Because your system is 386 =)

If you installed a 64-bit version of Ubuntu, only then you'd install the 64-bit package ;)


Iarwain

---

### Post by picallo on 2006-07-06
Mr. Iarwain, i tried to install libxine-extracodecs, but the systems request libmad0. Is that the only package that i have to install or should i download more?

where can i find it?
Now im at home and i have to switch to Win2 everytime i want to go online...

---

### Post by Iarwain ben-adar on 2006-07-06
Hey picallo,
[Here](http://packages.ubuntu.com/dapper/libs/libmad0) is where you can download libmad0 ...

But a word of "advice" before you download, better check in Adept (or Synaptic if you're Ubuntu instead of Kubuntu) if you have the required packages :D

(the required packages are the ones with a red dot in front of them, on the packages site)

Just type the name in Adept (or Synaptic) and see if you have them installed.

If you do (like i did), you just have to download libxine-extracodecs.
If you don't (like i didn't :D), you'll better install those via Adept (or Synaptic) and then install libxine-extracodecs.

And how come you don't have internet on your Ubuntu box?


Iarwain

---

### Post by picallo on 2006-07-06
well because i dont have broadband, and i have only 56k (Winmodem??). So u cant imagine...

A couple hours ago when i made the first post i wan in an internet cafe, where i go almost everyday to do the hard stuff. So next is to make a list which all the stuff i have to download tomorrow...

---

### Post by John.Michael.Kane on 2006-07-06
You may want to look into this [**ubuntuplus**]("https://ubuntuplus.bountysource.com/") heres the thread for it [** UbuntuPlus - Addon CD**]("http://ubuntuforums.org/showthread.php?t=183933&highlight=dapper+add+cd")

---

### Post by picallo on 2006-07-06
Thanks, thats what i was looking for. Tomorrow the comments.

---

### Post by Iarwain ben-adar on 2006-07-06
Nice,
didn't know about that Addon CD :D


Iarwain

---

### Post by picallo on 2006-07-07
mp3 is working fine, but video is like frozen. Ive downloaded the addon cd but i dont know how can i add the CD to install the packagese (Im using KUbuntu 6.06).

---

### Post by manicka on 2006-07-07
you may find Automatix useful
[URL="http://getautomatix.com"]
getautomatix.com[/URL]

---

### Post by picallo on 2006-07-07
thanks, but for that i need an internet conection...
and i havent configure it yet (and i have only dialup 56k). I only want to install the addons from ubuntusplus, something like Synaptic but for KUbuntu.

---

