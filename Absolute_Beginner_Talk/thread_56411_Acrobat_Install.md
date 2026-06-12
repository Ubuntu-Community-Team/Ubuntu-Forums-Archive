---
title: "Acrobat Install"
date: 2005-08-12
forum: Absolute Beginner Talk
---

### Post by spectra1 on 2005-08-12
I am new to Linux. I have installed Ubuntu and everything went well. I am trying to download and install Acrobat Reader and do not seem to be able to do this. Could anyone give me the procedure to do this.
Thanks ](*,)

---

### Post by KingBahamut on 2005-08-12
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
Be sure you have proper repositories


then from command line run

sudo apt-get install acroread
sudo apt-get install mozilla-acroread
sudo apt-get install acroread-plugins 

Restart Firefox, and you should be good to go.

---

### Post by mo_x on 2005-08-12
Download the tar.gz file from [ftp://ftp.adobe.com/pub/adobe/reader/unix/7x/7.0/enu/](ftp://ftp.adobe.com/pub/adobe/reader/unix/7x/7.0/enu/) to your home directory. Open a console window in your home directory and type the following commands:
> tar -xvzf AdbeRdr70_linux_enu.tar.gz
cd AdobeReader
sudo sh INSTALL

The installer will ask where to install. I chose to install to /opt/Acrobat7.0. You can start the reader now by typing:
> /opt/Acrobat7.0/bin/acroread
I created a symbolic link with the following command:
> ln -s /opt/Acrobat7.0/bin/acroread /usr/bin/acroread
The reader can now be started by simply entering the command:
> acroread

---

### Post by Irony on 2005-08-12
xpdf is installed by default so unless you specifically want Acrobat then simply double click on a pdf file and it will open in xpdf.

---

### Post by KingBahamut on 2005-08-12
Acroread is on the backports....a little more intiuitive than xpdf is.

---

### Post by Jonah on 2005-08-27
Even with the backports repositories enabled, "apt-get install acroread" still gets version 5.1. I eventually gave up and used Adobe's installer as suggested by mo_x. I just wanted to add a couple things to mo_x's instructions:
[list]
[*]If you want to be able to view PDFs from within Firefox using Acrobat Reader 7, you'll also need create a link to the browser plugin in your Firefox plugins directory. So if you installed Acrobat in /opt/Acrobat7.0 you would do:
```

sudo ln -s /opt/Acrobat7.0/Browser/intellinux/nppdf.so /usr/lib/mozilla-firefox/plugins/nppdf.so

```
[*]if you later decide you want to get rid of Acrobat, you can "uninstall" it by simply deleting the Acrobat7.0 directory as well as any symlinks you created:
```

sudo rm /usr/lib/mozilla-firefox/plugins/nppdf.so
sudo rm /usr/bin/acroread
sudo rm -r /opt/Acrobat7.0

```
[*]If you want to completely remove all traces of Acrobat, you'll also need to remove it's configuration files, which are stored in ~/.adobe/Acrobat/7.0. If you're sure you don't have any other Adobe programs installed, it should be safe to delete the entire ~/.adobe directory:
```

rm -r ~/.adobe

```
Otherwise, to only remove the configuration files for Acrobat 7.0, while leaving alone any configuration files for other Adobe software, do:
```

rm -r ~./adobe/Acrobat/7.0

```
(If you have multiple users set up on your system, you'll need to repeat this for each user.)
[/list]

---

### Post by sgsax on 2005-09-21
I've done exactly what mo_x outlined above and acroread dies with the message "Aborted".  I've got both the libstdc++5 and libstdc++6 packages installed.  I need acroread instead of xpdf et al because I use fillable pdf forms extensively at work.  Any idea why mine is dying?

Seth

---

### Post by pjs_flyer on 2005-10-21
Hi

I tried Mo_x's install for acroread and...nothing, nada, zip (etc) - no splash screen, no hanging, everything seems to go on as if I hadn't typed a command!  Any ideas?  I'm running Breezy on an Amilo 1630 (AMD64)

Incidentally, the reason I tried that solution was because I couldn't acroread on any of the Breezy repositories.  Is there a problem with acroread and AMD64?

Ta

P

---

