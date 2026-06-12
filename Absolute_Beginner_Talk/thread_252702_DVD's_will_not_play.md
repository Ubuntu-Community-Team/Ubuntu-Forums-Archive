---
title: "DVD's will not play"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by sam sarnie on 2006-09-07
I'm having trouble watching dvd's (In any player).  The get a message saying i don't/usr/share/doc/libdvdread3/ have enough rights to watch the disc.  I'm thinking this is a css problem but i have libdvdread and libdvdcss2 installed (and easy ubuntu) but am still having trouble. also i looked in /usr/share/doc/libdvdread3/ and there is no css file.  Can i check css is that css is installed?
any help would be appreciated as I am new to Ubuntu.
Thanks

---

### Post by xyz on 2006-09-07
Hi-
Just a thought...
Do you have this line in your sources.list:
> deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

If you use Breezy, replace dapper with breezy in the quote.
To check what's in your sources.list, run in a console:
```
sudo gedit /etc/apt/sources.list
```. 

Once open, see if you've got the .deb I mention above. If not, add it at the end of your sources.list and Save.

Then, run:
```
sudo aptitude update
```

Are you sure you have all the required codecs installed?  Note that depending on where you live, it may be illigal to install w32codecs.

You could also try to:
```
sudo aptitude install vlc
```
VLC is known to work.

Finally...have you heard about "Automatix"?

---

