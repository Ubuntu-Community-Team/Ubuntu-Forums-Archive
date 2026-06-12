---
title: "How to install *.RPM file"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by jmfa59 on 2007-07-08
I am trying to install Acronis and I was sent this file and the instructins saya that I should do: 

# rpm -Uvh snapapi26_modules-0.7.19-2.noarch.rpm

I couldn't do anything from the terminal by cutting and pasting the command what is wrong.
THANKS

---

### Post by BL00dFox on 2007-07-08
Are you sure that you are running that command while in the appropriate directory? If not, browse to where you have saved that RPM and try again...

---

### Post by Malibu Illusion on 2007-07-08
RPM files are Red Hat's version of Debian's DEB.  You need to acquire a .deb file in order to install whatever it is you're attempting to install, or build it from source.

There is another, somewhat experimental option, for converting RPM files into DEBs - Alien.  Install it like so:

```
sudo aptitude install alien
```

Then try and convert the file:

```
sudo alien snapapi26_modules-0.7.19-2.noarch.rpm
```

Then install it:

```
dpkg -i NAME.deb
```

I would recommend trying to find a native .deb package or building from source over the last option, where it can be helped.

Take care.

---

### Post by Sef on 2007-07-08
Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by ramjet_1953 on 2007-07-08
A much better solution is to search for a deb package, as Alien sometimes doesn't convert too well.

Off-topic, but another solution is to download the [COLOR="Blue"]Ghost for Linux[/COLOR] iso and burn it to a CD ROM. 

You just boot from the CD ROM and if you want to clone a HDD, just choose the option to do so.

[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)


Regards,
Roger 8)

---

