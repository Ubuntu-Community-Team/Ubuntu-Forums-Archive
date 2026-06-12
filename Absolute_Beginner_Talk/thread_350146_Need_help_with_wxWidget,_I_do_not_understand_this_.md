---
title: "Need help with wxWidget, I do not understand this at all....."
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by IronArjen on 2007-01-31
For certain software (treeview) I need to install wxWidget. I have been trying several things but I simply do not understand what is (not) happening. I use dapper on a amd64 machine. I used Synaptic first to install wx2.6-i18n, along with the files surrounding like a .doc file. Then according to the treeview software I need to install I need to, quote:

After building and installing wxWidgets, go to the contrib/src/svg folder in the root of the wxWidgets folder and make and install dcsvg:

	cd contrib/src/svg
	make
	make install

OK, which is the folder? Locate wx shows me lots of folders and files but only wx2.4?? From another webpage I found that 2.6 is not available for dapper 64, OK, uninstall the installed version and install wx2.4. Loctae wx, I get the same. I cannot evenb find the wx2.4-doc.

From the website of wxWidgets I downloaded a zip which is supposed to have a help in HTML but unpacking results in ,chm files. There seems to be no end to this, do you need to be a wizz in order to do this or is there a way out?

Thanks a lot

---

### Post by pay on 2007-01-31
> **IronArjen said:**
> After building and installing wxWidgets, go to the contrib/src/svg folder in the root of the wxWidgets folder and make and install dcsvg:

	cd contrib/src/svg
	make
	make install
That means when you have compiled wxWidgets, change into the folder contrib/src/svg (in the source folder of wxWidgets) and compile dcscg via their instructions aforementioned.

---

### Post by pay on 2007-01-31
This might be simpler than compiling it> Binaries

    * wxGTK Ubuntu packages for 2.8.0 are available. To use them please add

          deb [http://apt.tt-solutions.com/ubuntu/](http://apt.tt-solutions.com/ubuntu/) dapper main

      (or edgy instead of dapper if you use that release) to your /etc/apt/sources.list file and add the public key used for signing wxWidgets packages to the list of keys trusted by apt using the command

          curl [http://www.tt-solutions.com/vz/key.asc](http://www.tt-solutions.com/vz/key.asc) | apt-key add -

      and run apt-get update. You can then use
      apt-cache search --names-only wx\*2.8 command to see the available packages.

      Please notice that Ubuntu packages are only currently available for Dapper x86 and Edgy amd64 architectures.


---

### Post by IronArjen on 2007-01-31
Pay,

2.8 will not work my amd64 so I ll stick to 2.4 that should work. I installed via Synaptic but I find no wxWidget folder (using locate in terminal). Synaptic gives the following properties regarding what is installed.

/.
/usr
/usr/share
/usr/share/locale
/usr/share/locale/cs
/usr/share/locale/cs/LC_MESSAGES
/usr/share/locale/cs/LC_MESSAGES/wxstd.mo
/usr/share/locale/da
/usr/share/locale/da/LC_MESSAGES
/usr/share/locale/da/LC_MESSAGES/wxstd.mo
/usr/share/locale/de
/usr/share/locale/de/LC_MESSAGES
/usr/share/locale/de/LC_MESSAGES/wxstd.mo
/usr/share/locale/es
/usr/share/locale/es/LC_MESSAGES
/usr/share/locale/es/LC_MESSAGES/wxstd.mo
/usr/share/locale/fi
/usr/share/locale/fi/LC_MESSAGES
/usr/share/locale/fi/LC_MESSAGES/wxstd.mo
/usr/share/locale/fr
/usr/share/locale/fr/LC_MESSAGES
/usr/share/locale/fr/LC_MESSAGES/wxstd.mo
/usr/share/locale/hu
/usr/share/locale/hu/LC_MESSAGES
/usr/share/locale/hu/LC_MESSAGES/wxstd.mo
/usr/share/locale/id
/usr/share/locale/id/LC_MESSAGES
/usr/share/locale/id/LC_MESSAGES/wxstd.mo
/usr/share/locale/it
/usr/share/locale/it/LC_MESSAGES
/usr/share/locale/it/LC_MESSAGES/wxstd.mo
/usr/share/locale/nl
/usr/share/locale/nl/LC_MESSAGES
/usr/share/locale/nl/LC_MESSAGES/wxstd.mo
/usr/share/locale/pl
/usr/share/locale/pl/LC_MESSAGES
/usr/share/locale/pl/LC_MESSAGES/wxstd.mo
/usr/share/locale/ru
/usr/share/locale/ru/LC_MESSAGES
/usr/share/locale/ru/LC_MESSAGES/wxstd.mo
/usr/share/locale/sl
/usr/share/locale/sl/LC_MESSAGES
/usr/share/locale/sl/LC_MESSAGES/wxstd.mo
/usr/share/locale/sv
/usr/share/locale/sv/LC_MESSAGES
/usr/share/locale/sv/LC_MESSAGES/wxstd.mo
/usr/share/locale/tr
/usr/share/locale/tr/LC_MESSAGES
/usr/share/locale/tr/LC_MESSAGES/wxstd.mo
/usr/share/locale/zh
/usr/share/locale/zh/LC_MESSAGES
/usr/share/locale/zh/LC_MESSAGES/wxstd.mo
/usr/share/doc
/usr/share/doc/wx2.4-i18n
/usr/share/doc/wx2.4-i18n/copyright
/usr/share/doc/wx2.4-i18n/changelog.gz

So where is the contrib/src/svg folder???:confused: :confused:

---

### Post by pay on 2007-01-31
The contrib/src/svg folder is in the source code which you aren't using.```
sudo aptitude install build-essential checkinstall
wget http://superb-west.dl.sourceforge.net/sourceforge/wxwindows/wxGTK-2.8.0.tar.gz
tar zxvf wxGTK-2.8.0.tar.gz
cd wGTK-2.8.0
./configure --prefix=/usr
make
sudo checkinstall
cd contrib/src/svg
make
sudo checkinstall
```

---

### Post by IronArjen on 2007-02-01
Dear Pay,

I am sorry if this is turning into a pain. It turns out during the configure step that I lack GTK. I thought this was installed since I have GIMP up and running but apparently not or incorrectly. I downloaded the latest GTK stable version 2.6.9, untarred it, opened the install and followed procedure, configured the GTK, then tried make:

arjen@beavis:~/Downloads/gtk+-2.6.9$ make
make: *** No targets specified and no makefile found.  Stop.

make does work on my Ubuntu OS since this I installed yesterday succesfully (and I believe was also included in the steps you put up earlier). Then I installed GNU make, went back to the gtk..... directory, and repeated. Problem still there. According to Synaptic the other required package PKG config is installed.

Stuck again, cannot find more info on the net, Hope you know how this solve this as well. I am getting the idea that I will also need Glib, Pango and ATK, is that correct?

Thanks again. Once this all works I better write a howto based on your explanation.

---

### Post by pay on 2007-02-01
I think that the packages that you need it ```
sudo aptitude install libgtk2.0-dev
```When compiling packages you need the -dev versions of the dependencies. So if it asks you for anymore, put -dev on the end.

---

### Post by IronArjen on 2007-02-02
Yes! This worked, I guess that due the fact my 64 bit machine I need tools in development, I mean in general! Learned a lot again, will write the howto next week.

Cheers!

---

### Post by pay on 2007-02-02
You would need the -dev packages wither you were using 64bit or any other architecture. -dev basically means it adds bits to the packages that aren't needed for general use, but are needed for compiling.

---

