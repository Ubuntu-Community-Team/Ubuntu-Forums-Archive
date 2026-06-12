---
title: "Google Earth"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Salieri on 2007-08-22
I have download googleearth.bin
I running ubuntu 7
In a terminal window I did the following
cd ~/Desktop$
chmod 755 GoogleEarthLinux.bin
./GoogleEarth.bin

I get the installation screen and I walk though it and it appears to run ok
I get the Google Earth logo on the Desktop

but when I click on the logo to run the application the screen goes black and reboots ubuntu

Help, what am I doing wrong

Thanks

---

### Post by rfruth on 2007-08-22
why chmod & ./ ?
[http://earth.google.com/support/bin/answer.py?answer=44713&topic=1135]("http://earth.google.com/support/bin/answer.py?answer=44713&topic=1135")

---

### Post by _simon_ on 2007-08-22
Have you got 3D enabled video drivers installed?

I don't think it will work without, but not sure why that would cause a reboot.

---

### Post by sbazin on 2007-08-22
For a simple installation of Google Earth your can use Synaptic and the Medibuntu repository.
Simply follow this link for information on adding Medibuntu:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then Google Earth will be available in Synaptic.

---

### Post by martin saint martin on 2008-03-31
will this work with 64bit ubuntu?

---

### Post by stchman on 2008-03-31
> **Salieri said:**
> I have download googleearth.bin
I running ubuntu 7
In a terminal window I did the following
cd ~/Desktop$
chmod 755 GoogleEarthLinux.bin
./GoogleEarth.bin

I get the installation screen and I walk though it and it appears to run ok
I get the Google Earth logo on the Desktop

but when I click on the logo to run the application the screen goes black and reboots ubuntu

Help, what am I doing wrong

Thanks

Google earth is available via Medibuntu.

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

Follow the first pat of my tutorial on installing the Medibuntu repos and then.

```

sudo apt-get install googleearth
```

---

