---
title: "my Canon i550 isn't working!"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by tillsch on 2006-09-06
Hello english-speaking friends :p ,

I'm writing this because I have serious problems with my printer (Canon i550) and because the german forum [www.ubuntuusers.de](www.ubuntuusers.de) wasn't able to help me. I didn't even get an answer, that's frustrating.
There is a guide in the wiki of ubuntuusers.de how to install a Canon printer and I followed all these steps:

1. First I loaded the bjfiltercups-2.2-1.i386.rpm and the bjfilterpixus550i-2.2-1.i386.rpm from a japanese server and converted them with alien to debs.

2. I installed libxml1, libglade0, libpng3 and libtiff4 and after that the files of step 1.

3. Some symbolics must be set up:
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
sudo ln -s /usr/lib/libpng10.so.0.1.0.18 /usr/lib/libpng.so.2
sudo ln -s /usr/lib/libpng.so.3 /usr/lib/libpng.so.2s

4. To register the new libraries I typed in the console 'sudo ldconfig'

5. I tested the new configuration with 'bjfilterpixus550i':
BJLSTART
ControlMode=Common
SetTime=20060828211125
BJLEND
 

6. Than I installed the printer. 

And now the virtually problem: whatever I want to print, the printing job gets interrupted and a red exclamation mark appears in the panel. The printer should be alright, he did his job perfectly under Windows and Fedora Core 5 on the same computer (The problem is that I deleted the other partitions and now can not print anymore, but have to :-k ).
Here is the cups error_log, maybe it will help to aproximate to the problem:

tilmann@desktop:/var/log/cups$ cat error_log | tail
E [28/Aug/2006:21:27:00 +0200] cupsdAuthorize: Local authentication certificate not found!
E [28/Aug/2006:21:27:00 +0200] Resume-Printer: Unauthorized
E [28/Aug/2006:21:27:00 +0200] PID 8168 (/usr/lib/cups/backend/canon_parallel) stopped with status 1!
E [28/Aug/2006:21:27:00 +0200] [Job 9] No %%BoundingBox: comment in header!
E [28/Aug/2006:21:27:00 +0200] [Job 9] Unable to open parallel port device file "": No such file or directory
E [28/Aug/2006:21:27:49 +0200] cupsdAuthorize: Local authentication certificate not found!
E [28/Aug/2006:21:27:54 +0200] cupsdAuthorize: Local authentication certificate not found!
E [28/Aug/2006:21:27:54 +0200] cupsdAuthorize: Local authentication certificate not found!
E [28/Aug/2006:21:27:59 +0200] cupsdAuthorize: Local authentication certificate not found!
E [28/Aug/2006:21:27:59 +0200] cupsdAuthorize: Local authentication certificate not found!

I hope you could help me, this is serious because I need the printer soon. Hope you have some ideas. I'm very grateful to all kind of answers.

regards to all, till

---

### Post by robbyt on 2006-10-18
hey i'm seeing the same thing with my brother 2820 MFC.
I'm running edgy, but the printer worked swell in dapper.

i'm seeing this all over the cups logs:

 No %%BoundingBox: comment in header!



!!!???!!!

---

### Post by Dr. Nick on 2006-10-18
With the i550 that I used to use I just used the canon bjc-7000 drivers If I Recall Correctly. They are included in cups.

Maybe the driver file you have isnt working with the newer version of cups

---

### Post by jerrykenny on 2006-11-24
Hi Tilsch,

I've had this printer working with "Hoary", and Fedora 6 . . . . now onto Debian Etch , however.

This looks very familiar, so try using the usb interface instead, and definitley configure using the cups web interface (port 631 ?)

Beware ! even the cups web interface offers you some duff options . . . you'll need to install usbutils, then "lsusb" to see the correct usb interface you'll need.  

Also you're probably trying to configure a printer which isnt even on a "parallel port" but the older "LPT1" see if that option is available on the cups interface before you try usb.

Footnote . . . . 

**Whayhey, got it working on Debian Etch,**

installed libpng and libtiff, (newest versions) then in /usr/lib/ created symbolic links from libpng2 to the new version (repeat for libtiff)

Next, created .debs from rpm's (you need the 2.2.1 version for the 550i), next manually install the .debs

Restart the cups server

connect the dratted thing on the Printer-Port  (I wonder if that requires a reboot)  : )

Access the cups admin on [http://localhost:631](http://localhost:631)

IGNORE the option to install the "detected" printer . . .instead go to "add printer" . . . . and go thru the details  . . . you MUST specify the LPT Port !!!!!!!!!!!!! 

In my case I had to specify a ppd file, they're in /usr/share/cups/model


Good Luck


Incidentally, once you've installed your .debs, its worth cheking to see if you created your symbolic links OK. . . . do this by typing in  a terminal  

bjfilterpixus550i

and you should get this output

BJLSTART
ControlMode=Common
SetTime=20061124191541
BJLEND

but if your symlinks are not to the correct libraries, it'll let you know. . . . (unusually helpfull)

---

