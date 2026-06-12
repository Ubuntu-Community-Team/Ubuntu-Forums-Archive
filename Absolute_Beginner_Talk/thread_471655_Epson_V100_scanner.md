---
title: "Epson V100 scanner"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by bean77 on 2007-06-12
Anyone know how I can get this to work with Ubuntu?  (Feisty)

---

### Post by cotcot on 2007-06-12
Have you checked the drivers from Epson Avasys ? [[COLOR="Red"]EpsonAvasys[/COLOR]]("http://avasys.jp/hp/menu000000500/hpg000000442.htm") Your scanner is supported.

---

### Post by bean77 on 2007-08-07
I am so clueless, I can't figure out how to get the software working once I have it downloaded...

---

### Post by wflu on 2007-08-31
This is how I got an Epson V10 to work with Epson iScan on Feasty (it should apply to Edgy, and to otherere Epson scanners too). 

I found instructions here:
[http://doc.ubuntu-fr.org/materiel/scanner_epson]("http://doc.ubuntu-fr.org/materiel/scanner_epson")

The short version in english:

First make sure that you have sane and related packages installed. Make sure the scanner is turned on and attached.

Run 
 sane-find-scanner
This should produce a list of available scanners, hopefully including the one you want to use. If not, something is wrong (scanner not attached or similar).

I found the official Epson binary packages here:
[http://avasys.jp/hp/menu000000500/hpg000000442.htm]("http://avasys.jp/hp/menu000000500/hpg000000442.htm")
There are no .deb packages, so just go for the RPM (you will be asked to tell what system you use, one of the options being debian, but it leads to RPMs anyway). I fetched the RPMs for GCC-3.4.

Use 'alien' to convert RPMS to binaries (requires root priviledges):
 sudo alien --scripts iscan-2.3.0-1.c2.i386.rpm iscan-plugin-gt-s600-2.0.0-1.c2.i386.rpm
This should produce two debian packages. Install these (again, requires root)
 sudo dpkg -i  iscan_2.3.0-2_i386.deb iscan-plugin-gt-s600_2.0.0-2_i386.deb
This should install 'iscan'.

Run 
 scanimage -L
If this listed you scanner, everything is OK, and you can start 'iscan' and let the fun begin. 

On my installation the scanner (Perfection V10) was not recognized by udev.  To fix this, run again
 sane-find-scanner
and make a note of the relevant line, in particular the vendor and product IDs. Then run
 sudo gedit /etc/udev/rules.d/45-libsane.rules
Locate the Epson scanners and add a line for your scanner. For an Epson V10 I added
--
 # Epson Perfection V10
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="012d", MODE="664", GROUP="scanner"
--
where the values for idVendor and idProduct are the ones shown by sane-find-scanner.

Finally, unplug your scanner and plug it in again to let udev find it. Run
 scanimage -L
to verify that the scannerr was indeed found, and run 'iscan' to start scanning.

----------
A couple of additional notes:
I am running Ubuntu Feasty, generic kernel (which probably means 32bit).

I installed iscan from an RPM, but you can also grab the .tar.gz and install that. I tried that, and it seems to work too, but I do not know if it works for the x64 version. 

I did this: Fetch the .tar.gz (I got the GCC-3.4 version) and make sure sane, libsane-dev (I don't know is this is necessary) and gcc are installed. Unpack the source using
 tar xzvf iscan-2.3.0-1.c2.tar.gz
then configure and build (note: I install in /usr/local ot avoid messing too much with installed packages)
 cd iscan-2.3.0
 ./configure --prefix=/usr/local
 make && make install
You may have to add 
 /usr/local/bin
to the PATH environment variable, and
 /usr/local/lib
to the LD_LIBRARY_PATH environment variable. Then proceed as above.

---

### Post by bsmith1051 on 2007-09-09
If I've already gotten my Epson 4990 to work with the default SANE driver (Ubuntu 7.04) what will I gain by installing the Epson iscan driver?  Anything?  My scanner has 'Digital ICE' which is not supported by SANE, but I don't see it mentioned in the iscan docs either.

---

### Post by robino on 2007-10-10
Howto get your 'Epson V100 Photo' scanner work?

First I followed the first 2 points of this manual > [http://push.cx/2007/epson-perfection-v100-in-ubuntu](http://push.cx/2007/epson-perfection-v100-in-ubuntu) On the bottom of the document are more comments of users, which I also used to make it work.

Step 1
Download the iscan and iscan-plugin-gt rpms from the provider to your desktop or any other folder: [http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html) I selected V100 and Debian. 

Step 2
Open your terminal, go to the location of the file where you saved it (type 'cd Desktop') and type:

```
sudo alien iscan-2.3.0-1.c2.i386.rpm --script
sudo alien iscan-plugin-gt-s600-2.0.0-1.c2.i386.rpm --script
sudo dpkg -i iscan_2.3.0-1_i386.deb
sudo dpkg -i iscan-plugin-gt-s600_2.0.0-2_i386.deb
```

The third and fourth line gave me a dependency problem so I first had to remove an aplication I had installed before: 

```
sudo apt-get remove libsane-extras
```

Step 3
Now I added epkowa in the file /etc/sane.d/dll.conf by using nano as my texteditor

```
sudo nano /etc/sane.d/dll.conf
```

Step 4 
Somehow I could only run the iscan program as root. But after the following code I could run the program as a normal user

```
 sudo addgroup `whoami` scanner 
exit 
```

Now run Xsane through your application menu and it should work.

---

### Post by adamc55 on 2007-10-28
Cautionary note: doesn't seem to work if you architecture is x86_4 -- the RPM's apparently don't support that architecture. Which leaves us with compiling & linking the source, but I'm hitting problems there, too:
```
/usr/bin/ld: ./.libs/libsane-epkowa-s.a(libsane_epkowa_s_la-epkowa-s.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
./.libs/libsane-epkowa-s.a(libsane_epkowa_s_la-epkowa-s.o): could not read symbols: Bad value
collect2: ld returned 1 exit status

```

I guess the next step is to figure out where to insert an -fPIC flag and see if that works...

---

