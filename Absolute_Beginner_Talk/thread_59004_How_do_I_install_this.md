---
title: "How do I install this?"
date: 2005-08-22
forum: Absolute Beginner Talk
---

### Post by Muhammad on 2005-08-22
intel8x0-alsa-1.0.1.sh.gz

or

intel8x0-alsa-1.0.1.sh

---

### Post by KingBahamut on 2005-08-22
at a command line

sudo sh intel8x0-alsa-1.0.1.sh

---

### Post by Muhammad on 2005-08-22
OK Thanks, but what's this?

> Starting installer, please wait...

Error:
The installer could not find the kernel source on your
system.  Please install the kernel source and try again.

Locations searched:
/usr/src/linux
/usr/src/linux-2.4
/usr/src/2.6.10-5-686


---

### Post by KingBahamut on 2005-08-22
You will most likely need the linux-headers for your compiled source. 

do a uname -a which will breed your kernel version. Something like 2.6.10-5-<compiled version, probably 386> 

then do a 

sudo apt-get install linux-headers-2.6.10-5-<compiled version found in uname command>

and install. 

You may need to change the shell script to actually point to the proper directory after you install the header files.

---

### Post by Muhammad on 2005-08-22
I installed the header before I installed the nvidia driver

> Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.10-5-686 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


How do I change the shell script?

---

### Post by KingBahamut on 2005-08-22
nano <nameofthescript>.sh 

find where it defines the kernel headers....and make sure that its pointing to the right place.

---

### Post by Muhammad on 2005-08-22
OK, I'm 100% pure noob, I downloaded the file from this site

[http://downloadfinder.intel.com/scripts-df-external/detail_desc.aspx?agr=N&ProductID=950&DwnldID=7236&strOss=All&OSFullName=All%20Operating%20Systems&lang=eng](http://downloadfinder.intel.com/scripts-df-external/detail_desc.aspx?agr=N&ProductID=950&DwnldID=7236&strOss=All&OSFullName=All%20Operating%20Systems&lang=eng)

Ubuntu not supported?

---

### Post by KingBahamut on 2005-08-22
How big is the file?

and more specifically, are you doing this to address an audio issue , as in not getting any audio?

---

### Post by Muhammad on 2005-08-22
It's only 2.5 MBs. Also No, Audio works great, even in Doom3... 

But Doom3's Audio Quality is alot better in windows because of SoundMAX, that's why I was trying to install it on Linux.

---

### Post by Muhammad on 2005-08-22
I guess it's not possible to install this on Ubuntu... Thanks alot for your time fellow Final Fantasy Fan. :)

---

### Post by KingBahamut on 2005-08-22
Muhammad.....gonna give you a bit of a smack down....=) friendly one at least. 

Bahamut - Forgotten Realms, King of All Dragons.......

Long before FF ever existed. 
=)

Rant over. 

But I do like FF a little.

---

### Post by Muhammad on 2005-08-22
Shit! I didn't know Bahamut virtually-existed outside the FF universe XD

---

### Post by KingBahamut on 2005-08-22
He existed in the capacity long before FF ever existed I believe.

---

