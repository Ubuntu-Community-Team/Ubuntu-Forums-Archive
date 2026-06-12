---
title: "webcam"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by yeshe_tsogyelma on 2007-06-10
I know everyone talked about webcams and there are some threads about this ...So I went there, read the threads, followed the steps and ...nothing. Because the driver that I had to install from that location was removed...
So...here is what I am talking about: 
I have a Genius webcam v2, and i found a thread on it :
 
Originally Posted by arnieboy
try the following howto:
[http://ubuntuforums.org/showthread.php?t=75284](http://ubuntuforums.org/showthread.php?t=75284)

Ok, went to the how to...and at the second step it said the file had been removed...
Any help?:)

---

### Post by Pragmatist on 2007-06-10
Please list here exactly what you did and the errors that you got.

---

### Post by yeshe_tsogyelma on 2007-06-10
> **Pragmatist said:**
> Please list here exactly what you did and the errors that you got.

 I did this:

 sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential

It looked like this:

Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.15-28-386 is already the newest version.
linux-restricted-modules-2.6.15-28-386 is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

then I did this:

wget [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz)

and I got this:

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
](*,)

---

### Post by Pragmatist on 2007-06-10
The thread you are reading is from a while ago.  The location changed slightly (it is considered an "old release") Try typing it this way:

[B]wget [http://mxhaard.free.fr/spca50x/Download/oldrelease/spca5xx-20060501.tar.gz](http://mxhaard.free.fr/spca50x/Download/oldrelease/spca5xx-20060501.tar.gz)

All I did was add the subdirectory "oldrelease" which is in the Download directory.  So, the path is:
[/B]**[mxhaard.free.fr/spca50x/Download/oldrelease/spca5xx-20060501.tar.gz]("http://mxhaard.free.fr/spca50x/Download/oldrelease/spca5xx-20060501.tar.gz")**

---

### Post by yeshe_tsogyelma on 2007-06-11
...It keeps saying the same thing...

  Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
#-o

---

### Post by Pragmatist on 2007-06-11
Are you typing the wget command in a terminal?

I tried the exact command myself and it worked.

---

### Post by yeshe_tsogyelma on 2007-06-12
Yes, i type it ina terminal...I think there is something wrong, because I tried to install macromedia flash player meanwhile, it only installed some fonts or something, not everything, and now it gives me an error everytime I want to download something. I dont have the time now to post the error here, I will do it later on.

---

