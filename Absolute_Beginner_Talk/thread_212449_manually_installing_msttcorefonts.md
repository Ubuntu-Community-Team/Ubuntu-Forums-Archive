---
title: "manually installing msttcorefonts"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by Absurd on 2006-07-09
Well, according to the terminal, the site hosting the separate executables for the fonts is currently down.

I was able to find each of the executables somewhere else

so, can anyone tell me how I can install the fonts manually?

---

### Post by adam.tropics on 2006-07-09
[A Gift!]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmultiverse%2Fm%2Fmsttcorefonts%2Fmsttcorefonts_1.2ubuntu3_all.deb&md5sum=d858e7d7cd245f1107009d418671b478&arch=all&type=main") (Then right-click on it and go to the installer)

---

### Post by ciscosurfer on 2006-07-09
> **Absurd said:**
> Well, according to the terminal, the site hosting the separate executables for the fonts is currently down.

I was able to find each of the executables somewhere else

so, can anyone tell me how I can install the fonts manually?

If it's a debian package (.deb) use:```
sudo dpkg -i *packagename*
```Otherwise, untar/decompress it with **tar**, then descend into the directory, issue a **./configure**, then once that completes, issue a **make**, and once that completes, issue a **sudo make install**.

Another way to do this (and have the option of installing many other very useful packages) is to use ***Automatix***.  
Go to [Get Automatix]("http://getautomatix.com/") for details or seach within the threads here on the forums for instructions.

EDIT: Of course "the gift" from above (adam.tropics) is also a nice to way to achieve the desired effect! :)

---

### Post by Absurd on 2006-07-10
Thank you for the help, but that's not what I was talking about.

I know how to use 

```
sudo apt-get install msttcorefonts
``` from the terminal, but my problem is this

```

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--19:01:17--  http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Connection timed out.
--19:01:27--  http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--19:01:37--  http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Connection timed out.
--19:01:47--  http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... failed: Connection timed out.
--19:01:57--  http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Connection timed out.
--19:02:07--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
```I have andale32.exe, etc;  but I want to know if there is a way to manually install the fonts using nothing but the executables.

---

### Post by adam.tropics on 2006-07-10
could you try that again as I just uninstalled and reinstalled from the same repos etc as you, and got

```

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--12:12:23--  http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... 193.190.198.97
Connecting to belnet.dl.sourceforge.net|193.190.198.97|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=belnet.dl.sourceforge.net [following]
--12:12:24--  http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=belnet.dl.sourceforge.net
           => `./andale32.exe?download&failedmirror=belnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [   <=>                               ] 12,091        20.25K/s             

12:12:25 (20.20 KB/s) - `./andale32.exe?download&failedmirror=belnet.dl.sourceforge.net' saved [12091]

.sourceforge.net... 66.35.250.217
> Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
> HTTP request sent, awaiting response... 200 OK
> Length: unspecified [text/html]
> 
>     [   <=>                               ] 12,091        20.25K/s  

```

etc etc, all done no errors

---

### Post by Absurd on 2006-07-18
back

sorry, I haven't had much time to mess with Ubuntu lately

anyway, I still get the timeout errors

```
You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--10:59:20--  http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Connection timed out.
--10:59:30--  http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--10:59:40--  http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Connection timed out.
--10:59:50--  http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... failed: Connection timed out.
--11:00:00--  http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Connection timed out.
--11:00:10--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```does anyone know how I can manually install the fonts using the executables alone? (my original question)

---

### Post by chopsuey on 2006-08-04
same for me...
:sad:

---

### Post by christhemonkey on 2006-08-04
I installed them manually with wine:
```
wine andale32.exe 
```
But then again, you need wine to do that.
(And im not sure if they install system wide or just for wine...)

---

