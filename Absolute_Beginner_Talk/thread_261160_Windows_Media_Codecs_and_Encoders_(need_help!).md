---
title: "Windows Media Codecs and Encoders (need help!)"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-09-19
Okay, what do I need from here:

[http://www.microsoft.com/windows/windowsmedia/download/alldownloads.aspx](http://www.microsoft.com/windows/windowsmedia/download/alldownloads.aspx)

to be able to play videos, listen to certain music, etc. And if at all possible could you tell me how to download/install them too.

Greatly appreciated.

---

### Post by enopepsoo on 2006-09-19
you should not need anything from there.  I find if you install automatix and then add the codecs from there (and VLC of course :-P ) that you can play basically anything.

I am not able to play wmv9 on my pc, but I think that this might be an issue with ubuntu 64.  I have not bothered to look into it yet.

---

### Post by voodoonirvana on 2006-09-19
> **enopepsoo said:**
> you should not need anything from there.  I find if you install automatix and then add the codecs from there (and VLC of course :-P ) that you can play basically anything.

I am not able to play wmv9 on my pc, but I think that this might be an issue with ubuntu 64.  I have not bothered to look into it yet.

Oh, cool. Well I think I tried installing Automatix a while back and just messed things all up...could you or someone help me with that?

---

### Post by slibuntu on 2006-09-19
If you don't want to use automatix, and many people don't, try using [this page]("https://help.ubuntu.com/community/RestrictedFormats") . It should tell you what codecs to download
Mostly they are downloadable using synaptic package manager

---

### Post by enopepsoo on 2006-09-19
I think if you install VLC through synaptic it will get most of the codecs you need to play most things.  I have never had any problem with automatix.  If you had a problem with that it might be helpful to look in one of the many automatix threads.:D

---

### Post by voodoonirvana on 2006-09-19
Okay so I used this to try and install automatix:

[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

I got past the Key Import part and now when I try to do this:

sudo apt-get install automatix

it says it couldn't find the package...

---

### Post by voodoonirvana on 2006-09-19
need some help

---

### Post by nudnik on 2006-09-19
Open a terminal and copy and paste the following after the command prompt:

wget -c [http://packages.freecontrib.org/ubuntu/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.deb](http://packages.freecontrib.org/ubuntu/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.deb)
sudo dpkg -i w32codecs_20060611-1plf1_i386.deb

That will install the Windows codecs. Be sure to hit enter when the last bit with "deb" at the end appears during the install process.

No need to fear the terminal, its almost exactly like the command prompt when using Windows as far as the interface is concerned. The command language is different, however.

:D

---

### Post by voodoonirvana on 2006-09-19
> **nudnik said:**
> Open a terminal and copy and paste the following after the command prompt:

wget -c [http://packages.freecontrib.org/ubuntu/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.deb](http://packages.freecontrib.org/ubuntu/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.deb)
sudo dpkg -i w32codecs_20060611-1plf1_i386.deb

That will install the Windows codecs. Be sure to hit enter when the last bit with "deb" at the end appears.

No need to fear the terminal, its almost exactly like the command prompt when using Windows as far as the interface is concerned. The command language is different, however.

:D

I got this when I used the first code:

Connecting to packages.freecontrib.org|88.191.21.245|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
23:47:39 ERROR 404: Not Found.

---

### Post by nudnik on 2006-09-19
The forum has abbreviated my post...hover the mouse over the part with the colons trailing off and you will see the correct information at the bottom of the web browser.

---

### Post by nudnik on 2006-09-19
Visit this webpage [https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5](https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5)

Look at the left hand corner of the screen and you will see a list of items. Among them will be the Win32 codecs. Click on that link and you will see the code I attempted to post.

---

