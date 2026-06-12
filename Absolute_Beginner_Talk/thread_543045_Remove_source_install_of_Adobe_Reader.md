---
title: "Remove source install of Adobe Reader"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by altonbr on 2007-09-04
I installed the .tar.gz version of Adobe Reader 7.0.9 from here: [http://www.adobe.com/products/acrobat/readstep2.html](http://www.adobe.com/products/acrobat/readstep2.html)

In the tarball, the contents are:
* COMMON.TAR
* ILINXR.TAR
* INSTALL
* LICREAD.TXT
* ReadMe.htm

In ReadMe.htm, there is this:
> To uninstall Adobe Reader 7.0.8 using the command line

1. Open a terminal window.

2. Run the following command as an administrator or root:
rpm -e AdobeReader_enu

To uninstall Adobe Reader, you can simply delete the directory where it was installed. You may choose to do this if you installed using a tarball installer.

I'm a little worried of simply "deleting" the Adobe Reader folder because that won't remove any dependancies or shortcuts that it created, including the Firefox plugin.

Does anyone have any experience with this installer? I hate software that doesn't come with a 'configure' executable.

Then, assuming I can get rid of this, does Evince has a Firefox plugin or do I have to open every PDF externally?

---

### Post by felicity on 2007-09-04
> I'm a little worried of simply "deleting" the Adobe Reader folder because that won't remove any dependancies or shortcuts that it created,

If you installed it manually it wouldn't have installed any dependencies. Only installing through a package manager with dependency support would do that. I'm not aware of the linux version of adobe reader making shortcuts, but you can always check by using:
```
sudo updatedb
```
```
locate adobe
```
or
```
locate Adobe
```

>  including the Firefox plugin.
Firefox plugins can be removed by going to the firefox menu Tools, Add-Ons, choose the plugin you want to uninstall and click Uninstall.

---

### Post by altonbr on 2007-09-04
Well I already know that Adobe Reader 7.0.9 is located in /usr/local/Adobe/ and /usr/lib/Adobe/. I'm just wondering if anyone else has uninstalled it by deleting those directories.

Also, Adobe doesn't install an Add-on, it installs a plug-in. The two are quite different.

Lastly, and off topic, GREAT quote by Dostoevsky.

---

