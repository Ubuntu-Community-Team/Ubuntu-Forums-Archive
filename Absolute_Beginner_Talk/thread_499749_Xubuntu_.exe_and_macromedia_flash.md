---
title: "Xubuntu .exe and macromedia flash"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by eulallia1 on 2007-07-13
K i recently installed xubuntu and it owns XD :guitar:

But, .exe will not run (obviously a windows format thing) and macromedia flash will not run, even under the .tar .gz and the .rpm

if someone can solve my problem that would be great, also, does java run in linux?

---

### Post by eulallia1 on 2007-07-13
someone answer =.=

---

### Post by Malibu Illusion on 2007-07-13
Try checking the documentation initially before posting questions; Flash and Java is covered extensively.

[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by eulallia1 on 2007-07-13
im not running ubuntu im running xubuntu -.-

---

### Post by Malibu Illusion on 2007-07-13
The only difference between Ubuntu and Xubuntu is the windows managers; Ubuntu uses GNOME, Xubuntu uses XFCE.  The process for setting up Flash and Java plugins does not change.  It only changes based on your architecture and the differences are covered in the linked page I provided.

Please read the information on that page that will instruct you as to how to set up both Flash and Java.  If you experience difficulties along the way, post the problem here and someone will be able to help you out.  You need to get into the habit of reading and trying things yourself initially though.  If you come here and post a generic question you're only going to be directed to various documentation which you could have found yourself with Google or by searching this forum.

---

### Post by ugm6hr on 2007-07-13
Assuming you use Firefox and have the i386 Xubuntu - ensure all the repositories are enabled in Synaptic Package Manager (in Settings Menu), and search for *flashplugin-nonfree*.

Just install this and it should work.

If you have the AMD64 Xubuntu, it's a lot harder.

---

### Post by crimesaucer on 2007-07-14
There is the new Adobe Shockwave Flash 9.0 r48 located here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW)


There are directions of what to do on that page for the .tar.gz for Linux, it has an installer and that should be easy.


I didn't use the installer, instead, I downloaded the .tar.gz to my home directory, and I then used the Terminal to unpack it with this command:

```
 tar -xvzf install_flash_player_9_linux.tar.gz
```


Next, I moved the new Flash updates into my previous /usr/lib/flashplugin-nonfree directory that had my older version 9.0 r3, with these two commands in Terminal:


```
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/flashplugin-nonfree

```


```
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/flashplugin-nonfree

``` 

this wrote over my previous version with the new update.


I then restarted my Swiftweasel browser, and Firefox browser, and checked my "about : plugins" for both and they were both using the new updated Shockwave Flash 9.0 r48 version.


...but for Swiftfox (which I have in my /opt directory), I had to copy both of those updates into the /opt/swiftfox/plugins directory and then restart Swiftfox for Swiftfox to use the new version 9.0 r4 in the "about : plugins".


This is another thread about it: [http://ubuntuforums.org/showthread.php?t=497826&highlight=Flash+version](http://ubuntuforums.org/showthread.php?t=497826&highlight=Flash+version)

---

