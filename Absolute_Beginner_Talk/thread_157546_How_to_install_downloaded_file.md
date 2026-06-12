---
title: "How to install downloaded file"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by Pum on 2006-04-09
Hi. I downloaded opera file for ubuntu 5.10. How can Install the programm. 
(Very new in Linux)
Thanks

---

### Post by Rumor on 2006-04-09
Pum,
It would depend on what file you downloaded. What *I* would do if I were going to install Opera is use the Automatix script. You can read about it here: [http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405)

or you can get is by opening up your terminal (Applications | Accessories | Terminal) and entering:
```
wget http://beerorkid.com/automatix/automatix_5.7-3_i386.deb
```

Then enter:
```
sudo dpkg -i automatix_5.7-3_i386.deb
```

Then go to Applications | SYstem Tools and choose Automatix. Once it has opened, you can check off Opera and let the script install it for you.

---

### Post by aysiu on 2006-04-09
[https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser)

---

### Post by Bloch on 2006-04-09
The file is presumably a debian package - it will end with .deb 
Download it. 
Now open a terminal ( go to Applications -> Accessories -> terminal  on the top bar)
You should learn a little bit about the commands to use in the terminal - there are tutorial on it around. If you have ever used DOS you will get the idea very quickly. You need to change director to the directory where you saved the debian intallation. (Or if you are stuck, you can move the debian file into your Home Folder - when the terminal starts, it will be in your Home Folder.)
Type 
sudo dpkg -i  blahblah.deb
where you replace blahblah.deb with the correct name of the debian package. (files that end in .deb are called packages)
It will request your password - I presume you know your superuser password (also called root password, or administrative password)
Enter your password and off it goes. It should also place the new program in the menu. This method works for other debian packages, but be aware that they don't always place something in the menu. (this is because the package maker does not know what desktop manager you are using. The debian package for opera on the other hand is specially tailored for ubuntu - you did choose the ubuntu version on the download page, did you?)

Another way to install opera is to add this source to the repositories. To do this open synaptic and go to Settings -> Repositories
Add this source
[http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch
Close synaptic and open it again. It will update its list of packages you can install. Scroll down to opera (or use search) and click to install. You have to be connected to the internet of course. This method is better because you will automatically be notified when an update is available. A beginner should avoid installing packages using dpkg -i  - often the package is already available either in the ubuntu repositories or by adding some trusted external repository. The last time I used dpkg -i  was for an old Mupad program that is no longer freely available.

---

### Post by Bloch on 2006-04-09
The source to add for opera should be;
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free

see the link aysiu provided.  That page tells you how to add this source to your repositories using the commandline. However you can also add it using synaptic, as I describe above.

---

### Post by Bloch on 2006-04-09
with no underline on the http source given above 
This system automatically adds an underline whever it sees a word beginning http
That could really mess up a beginner

---

### Post by Pum on 2006-04-09
OK thanks you all I installed the opera

Now I downloaded file (KTranslator) unpacked it now how can I install it from the console?

---

### Post by Sef on 2006-04-13
To install it download build-essential first.

sudo apt-get update

sudo apt-get install build-essential

then follow the directions on the link below to install ktranslator.


[http://ktranslator.sourceforge.net/download.html]("http://ktranslator.sourceforge.net/download.html")

---

