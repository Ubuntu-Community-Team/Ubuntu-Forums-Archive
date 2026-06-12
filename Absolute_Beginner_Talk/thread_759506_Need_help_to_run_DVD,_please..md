---
title: "Need help to run DVD, please."
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2008-04-19
I have an instructional DVD and when I put it into my DVD-rom I get this message:-

The folder contents could not be displayed.  
You do not have the permissions necessary to view the contents of "cdrom1".

Does this make sense?  Is there something I can do about this?

Is it possible that this DVD was made to only run in Windows?

Your help will be appreciated.

---

### Post by canucked on 2008-04-19
Here is a guide for playing DVDs in Ubuntu:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by canucked on 2008-04-19
You will probably want to install the libdvdcss package through the Medibuntu repository.  Details can be found here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Good luck!

---

### Post by george9233 on 2008-04-19
No matter if the DVD is made to only run in Windows, since even though it cannot run in Linux, the contents should always be able to display.

You may try to open the file manager (nautilus) with root permission by type these in the terminal: ```
gksudo nautilus
``` and then try to open the DVD.

---

### Post by L Campbell on 2008-04-19
> **canucked said:**
> Here is a guide for playing DVDs in Ubuntu:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Thanks for your interest.

I went to this link and did:-

sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh

Unfortunately it doesn't appear to have changed anything as I am still getting the same message.

Kind regards.

---

### Post by L Campbell on 2008-04-19
> **canucked said:**
> You will probably want to install the libdvdcss package through the Medibuntu repository.  Details can be found here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Good luck!

I tried this,

qwer@qwer-desktop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
--08:01:24--  [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.10
Connecting to www.medibuntu.org|87.98.242.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 223 [text/plain]

100%[====================================>] 223           --.--K/s             

08:01:25 (21.17 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [223/223]

qwer@qwer-desktop:~$ 

In Synaptic I can see that I now have libdvdcss2 installed but I still get the same error message when I insert the DVD.

I guess I must be doing something wrong but I don't understand what that would be.

Kind regards.

---

### Post by L Campbell on 2008-04-19
> **george9233 said:**
> No matter if the DVD is made to only run in Windows, since even though it cannot run in Linux, the contents should always be able to display.

You may try to open the file manager (nautilus) with root permission by type these in the terminal: ```
gksudo nautilus
``` and then try to open the DVD.


Thanks for your suggestion.  I tried this but still get the exact same error message.

Kind regards.

---

### Post by L Campbell on 2008-04-20
> **L Campbell said:**
> I have an instructional DVD and when I put it into my DVD-rom I get this message:-

The folder contents could not be displayed.  
You do not have the permissions necessary to view the contents of "cdrom1".

Does this make sense?  Is there something I can do about this?

Is it possible that this DVD was made to only run in Windows?

Your help will be appreciated.

I'm still hoping someone might be able to help me fix this  ........................

---

### Post by buixuanduong1983 on 2008-04-20
Can you post the output of this command:

ls -l /media

and read this:

man chmod

Hope this help.

---

### Post by L Campbell on 2008-04-20
> **buixuanduong1983 said:**
> Can you post the output of this command:

ls -l /media

and read this:

man chmod

Hope this help.

Hi, thanks for your suggestion.

qwer@qwer-desktop:~$ ls -l /media
total 16
lrwxrwxrwx 1 root root    6 2007-10-01 15:24 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-10-01 15:24 cdrom0
drwxr-xr-x 2 root root 4096 2007-10-01 15:24 cdrom1
lrwxrwxrwx 1 root root    7 2007-10-01 15:24 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2007-10-01 15:24 floppy0
drwxr-xr-x 2 root root 4096 2007-12-26 14:39 sdb1
qwer@qwer-desktop:~$ 

I'm trying to find where to read ' man chmod '

Kind regards.

---

### Post by buixuanduong1983 on 2008-04-20
You have 2 CD drive? I only have one (cdrom0), and one link (cdrom) to cdrom0. And my permission letters are same as you.

I don't know how it should be if we have 2 cdrom, need 2 link or not.

Also try to check permission of cdrom drive in /dev, mine is /dev/hdb:

lrwxrwxrwx 1 root   root             3 2008-04-16 15:50 cdrom -> hdb
lrwxrwxrwx 1 root   root             3 2008-04-16 15:50 cdrw -> hdb
brw-rw---- 1 root   cdrom       3,  64 2008-04-16 15:50 hdb

Wish you luck, because I have no other ideal, hope other people in forum can help.

---

