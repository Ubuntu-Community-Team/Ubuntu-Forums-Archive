---
title: "Installing Flash 9 Beta"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-10-30
I know there is a lot of stuff on this out there, but I can't find any of it.

How can I install Flash 9 beta? Thanks!

---

### Post by compmodder26 on 2006-10-30
1. Download it from the Flash site.

2. Uncompress it (I left it in my home folder).

3. Either copy it or create a symbolic link to it (the .so file) in /home/<your username>/.mozilla/plugins/

4.  Restart firefox and you should be using flash 9

---

### Post by NegativeSpace on 2006-10-30
For Firefox:

Go here:

[http://labs.adobe.com/downloads/flashplayer9.html]("http://labs.adobe.com/downloads/flashplayer9.html")

Download the Linux installer and extract it.

Then move the file *libflashplayer.so* into Firefox's plugins folder (/usr/lib/firefox/plugins.)

Hope that helps.

---

### Post by nickle on 2006-10-30
try Automatix2. it will install Falsh as well as lots of other stuff without any bother.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by Sef on 2006-10-30
> try Automatix2. it will install Falsh as well as lots of other stuff without any bother.


If automatix works well, it does a nice job.  However, if it don't work well, then it is a real pain.

---

### Post by jkvv_1973 on 2006-10-30
> **nickle said:**
> try Automatix2. it will install Falsh as well as lots of other stuff without any bother.

[http://www.getautomatix.com/](http://www.getautomatix.com/)


this is not guaranteed to install the latest flash...

you have to remove/uninstall the flash non free (all traces of it-via synaptic) then manually download install via terminal

heres the link

[http://www.kungfuice.com/index.php/2...n-ubuntu-edgy/](http://www.kungfuice.com/index.php/2...n-ubuntu-edgy/)

---

### Post by DoomedTX on 2006-10-31
I'm having a problem even downloading the beta for some reason. I had [http://labs.adobe.com/downloads/flashplayer9.html]("http://labs.adobe.com/downloads/flashplayer9.html") open on another tab and clicked on the "Download Installer for Linux" link. When the download box came up I couldn't remember if I needed the installer or standalone so I canceled and jumped back to this thread. When I went over to the Adobe tab and clicked on the link, I got .3 seconds of activity according to Fasterfox and then nothing. I tried this with all the other links and had similar results. From Windows ActiveX down to Mac Intel I can download and cancel as many times as I want. The bottom 3 (Mac standalone and both Linux versions) let me try the download once, but after hitting cancel I cannot try again.

I've tried reloading the page, navigating directly to the download site and restarting FireFox, all to no avail. Guess I'll try another computer now. ](*,)

---

### Post by Dinerty on 2006-10-31
Follow this:

[http://www.ubuntuforums.org/showthread.php?t=282610&highlight=installing+macromedia+flash](http://www.ubuntuforums.org/showthread.php?t=282610&highlight=installing+macromedia+flash)

look for post #7

---

### Post by facefur on 2006-10-31
I've succesfully done the beta install on two machines.  I pulled the F9-beta tar file from adobe's site, unpacked it to a folder on my desktop, then followed the instructions for moving the flash ".so" file.  On my first machine, I moved it into my /usr directory, and created a link in my /home folder.  On theo ther machine, I simply put the file into the .mozilla folder in my /home directory.

I haven't really exercised it that much, but it does play things the old v7 would not.

---

### Post by jkvv_1973 on 2006-10-31
ive read so many flash 9 threads -

I noticed fail to mention to erase the older version first before 

installing ver 9 beta...tip:via synaptic search "Flash" and 

complete removal

---

