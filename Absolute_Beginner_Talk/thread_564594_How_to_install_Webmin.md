---
title: "How to install Webmin"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by mork on 2007-10-01
How do I start a browser on a new server ubuntu install to actually be able to install Webmin as someone had suggested?

I want to install Webmin, but I don't have any idea how to get to the Internet on this box.

typing wget.... doesn't work.

If I copy the .deb to a CR-RW, I'm not sure how to read it.

Help....

Thanks.

-- M

---

### Post by rubbsdecvik on 2007-10-01
I assume you have installed a server version of Ubuntu.  If this is true, you don't have any graphical user interface.  If you have an Ethernet cable hooked up to the computer, then you should be able to automatically connect.  If this isn't the case then we have a couple issues.  But to help with this one, you can install webmin with the following command.

```
sudo apt-get install webmin
```

That should install it for you.  if that does not work you can copy it to a CD, and then change your directory to the cd using a command like:

```
cd /media/cdrom/
```

If you have multiple CD/DVD drives you may need to add a 0 or a one at the end of the cdrom part.

the you can install it using ```
dpkg --install  *name of the package goes here*
```

If you want a text base browser you can install it using:
```
sudo apt-get install links2
```

if you want a GUI you can use the package called ubuntu-desktop:
```
sudo apt-get install ubuntu-desktop
```

hope that helps... if not let us know.

---

