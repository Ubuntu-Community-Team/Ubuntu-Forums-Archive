---
title: "Problem on install to External HDD for Apple"
date: 2009-07-26
forum: Apple Hardware Users
---

### Post by andrew1 on 2009-07-26
I used my mac, which is one year old, to format and external hardrive with ubuntu that I was planning to install in an old IBM laptop.  I did a temporary install and then seleted install disk from the desktop.  I then selected my external drive for the instalation.  When it asked about partitioning my Mac Hard Drive, I closed the dialog box.  Now when I log on to my mac and my external drive is disconnected I get a flashing folder with a question mark in it.  I do see my folders though under the Machintosh Hd that shows up when I lauch the temporary Ubuntu?  Can someone help so that I can get my mac to start up normally?  This is urgent...my heart is racing.  Thanks

---

### Post by pxwpxw on 2009-07-26
> **andrew1 said:**
> I used my mac, which is one year old, to format and external hardrive with ubuntu that I was planning to install in an old IBM laptop.  I did a temporary install and then seleted install disk from the desktop.  I then selected my external drive for the instalation.  When it asked about partitioning my Mac Hard Drive, I closed the dialog box.  Now when I log on to my mac and my external drive is disconnected I get a flashing folder with a question mark in it.  I do see my folders though under the Machintosh Hd that shows up when I lauch the temporary Ubuntu?  Can someone help so that I can get my mac to start up normally?  This is urgent...my heart is racing.  Thanks

You probably need to restore the MBR partion table because the installer may have changed it.
Normally do this using the rEFIt partion tool, but you cant do that if you cant start. ([http://refit.sourceforge.net/](http://refit.sourceforge.net/))

You can do it from the ubuntu live CD,  using the linux version of 'gptsync. from your Live CD,
you can download the appropriate amd64 or i386 version of gprsync package I posted in a thread - 

gptsync packages for MBR sync update intel macs
[http://ubuntuforums.org/showthread.php?t=1117464](http://ubuntuforums.org/showthread.php?t=1117464)

Install it temporarily with the Live CD from where you downloaded it (you should have only the one gptsync deb package)
```

sudo dpkg -i *.deb

```

then run it to sync the Mac HD MBR.
```

sudo gptsync /dev/sda

```

---

