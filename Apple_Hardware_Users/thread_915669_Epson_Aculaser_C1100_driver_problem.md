---
title: "Epson Aculaser C1100 driver problem"
date: 2008-09-10
forum: Apple Hardware Users
---

### Post by villaa on 2008-09-10
Hi there,

i'm using ubuntu 6.06 LTS on a mac ppc and i'd like to connect it to a Epson Aculaser C1100 printer via a local usb port.

I got the driver provided by avasys "Epson-ALC1100-filter-1.2.tar.gz". The installation process and the settings using cups didn't show any problem relating to permissions, dependencies etc. I'm aware about the requirements (including cups-config), root privilegies, cups restart etc., in spite of this the printer doesn't work. In addition, when i start a job printing the printer data led doesn't blink.

I'm afraid that the driver doesn't run on a ppc architecture, could anyone help me?

Thanks a lot!

---

### Post by Marc Higgins on 2009-01-03
Firstly this may not work on Mac architecture but it worked for me on i386.

It looks like something that ships with Ubuntu doesn't work with the Epson C1100r & the source file Epson-ALC1100-filter-1.2.tar.gz from epsons site [www.avasts.jp]("www.avasts.jp") doesn't work either (well I can't get it to work). However the rpm's available on the same site DO work if they are converted to deb's & installed.

#1 Install the dependencies (this is REALLY  important, if you don't do 
this it won't work)

```
sudo aptitude install gcc-3.3-base libstdc++5
```

or you could just use synaptic System > Administration > Synaptic & just search for & install gcc-3.3-base & libstdc++5

From here you can decide to;

[B]OPTION A
[B]
the simplest way to get your Epson C1100 printing on ubuntu is to just install the deb files direct from our site below[/B]
 
[http://www.hunny.be/epson-alc1100-filter_1.2-1_i386.deb]("http://www.hunny.be/epson-alc1100-filter_1.2-1_i386.deb")

[http://www.hunny.be/epson-alc1100-filter-cups_1.2-1_i386.deb]("http://www.hunny.be/epson-alc1100-filter-cups_1.2-1_i386.deb")


Just double click on EACH of these links, that will invoke the Gdebi package installer & install the files.

Then install the printer normally using System > Administration > Printers (AKA system-config-printer) & hopefully you will be printing happily in seconds :)

OR

OPTION B

you can make your own install files using Alien, the same way we did

Install Alien

```
sudo aptitude install alien

```
or just use synaptic System > Administration > Synaptic & search for & install alien

Then go to [URL="http://www.avasys.jp/english/linux_e/dl_laser.html"]http://www.avasys.jp/english/linux_e/dl_laser.html
[/URL]
download these 2 files

For Turbo/RedHat/Fedora (Epson-ALC1100-filter-1.2-0.i386.rpm)
For Turbo/RedHat/Fedora (Epson-ALC1100-filter-cups-1.2-0.i386.rpm)

then from a terminal run

```
sudo alien Epson-ALC1100-filter-1.2-0.i386.rpm

```

```
sudo alien Epson-ALC1100-filter-cups-1.2-0.i386.rpm

```
that will create 2 files

epson-alc1100-filter_1.2-1_i386.deb
epson-alc1100-filter-cups_1.2-1_i386.deb

you can then use dpkg -i

```
dpkg -i epson-alc1100-filter_1.2-1_i386.deb
```

```
dpkg -i epson-alc1100-filter-cups_1.2-1_i386.deb
```

or just double click the deb files with your mouse that will invoke the Gdebi package installer to install the files.

Then just install the printer normally using System > Administration > Printers (AKA system-config-printer) & hopefully you will be now be printing happily :)

---

### Post by villaa on 2009-01-08
Thank you for your help Marc, unfortunately this doesn't fix the problem: when I try to install the two packages a "wrong architecture: "i386"" error message appear and the installation fails.

---

### Post by pe7er on 2009-01-08
> **Marc Higgins said:**
> Firstly this may not work on Mac architecture but it worked for me on i386.
Thank you very much for this helpful extensive description!
I successfully installed my AcuLaser C1100 printer on my i386 machine.

---

### Post by Marc Higgins on 2009-01-09
Sorry Villaa your in an apple forum & your original post tells us your running a mac power pc.

The error you are getting is because the package is for an i386 machine.

What we need to be doing is building the debs direct from [the source file]("http://www.hunny.be/Epson-ALC1100-filter-1.2.tar.gz"). Unfortunately I was unsuccessful installing from the source file & I am not confident of building a ppc based deb package.

The rest of this is written as if you were trying to install on a 64bit machine. It may prove helpful as I think the principle is the same. You can not use alien to translate a 32bit.rpm to a 64bit.deb, it follows the same would be true for ppc. You just need to find a ppc equivalent to ia32-libs

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

I don't have a 64bit machine so this is trial & error. BACKUP! ... all care but no responsibility & all that.

Firstly install the 32-bit compatibility libraries for AMD64 & the tools for the job of converting.

```
sudo aptitude install ia32-libs fakeroot alien
```

Then go to [http://www.avasys.jp/english/linux_e/dl_laser.html](http://www.avasys.jp/english/linux_e/dl_laser.html)

download these 2 files

For Turbo/RedHat/Fedora (Epson-ALC1100-filter-1.2-0.i386.rpm)
For Turbo/RedHat/Fedora (Epson-ALC1100-filter-cups-1.2-0.i386.rpm)

and converted both of them to tgz files

```
sudo fakeroot -t alien Epson-ALC1100-filter-1.2-0.i386.rpm

```
```
sudo fakeroot -t alien Epson-ALC1100-filter-cups-1.2-0.i386.rpm

```
Then converted the two tgz files back into .deb's using alien

```
sudo alien Epson-ALC1100-filter-1.2-0.i386.tgz

```

```
sudo alien Epson-ALC1100-filter-cups-1.2-0.i386.tgz

```

from there it is the usual installation procedure

your have created 2 new files

epson-alc1100-filter_1.2-1_i386.deb
epson-alc1100-filter-cups_1.2-1_i386.deb

you can then use dpkg -i

```
dpkg -i epson-alc1100-filter_1.2-1_i386.deb

```

```
dpkg -i epson-alc1100-filter-cups_1.2-1_i386.deb

```
or just double click the deb files with your mouse that will invoke the Gdebi package installer to install the files.

Please let me know how if this works for you.

---

### Post by paul.macdonnell@gmail.com on 2009-11-08
Hi - I've just installed these to Debian files on my Dell inspiron laptop running Ubuntu 8.04 and they installed successfully. But when I try to print the Data light begins to light up - showing there is communication - but then it stops and nothing happens. It does print from my PC running XP. Any thoughts...?

---

### Post by paul.macdonnell@gmail.com on 2009-11-13
q

---

### Post by kububa on 2009-11-28
I had problem installing this printer in Ubuntu 9.10.

I found the solution on this page:

[http://forum.schnellsuche.de/tutorials-howto/howto-epson-aculaser-c1100-debian-ubuntu-installieren-t2619.html]("http://forum.schnellsuche.de/tutorials-howto/howto-epson-aculaser-c1100-debian-ubuntu-installieren-t2619.html")

I had to install this package:
[http://packages.ubuntu.com/jaunty/i386/libstdc++5/download]("http://packages.ubuntu.com/jaunty/i386/libstdc++5/download")

and now it works great.

---

### Post by paul.macdonnell@gmail.com on 2009-11-30
Thanks for this information. It worked.

---

### Post by Marc Higgins on 2010-01-02
9.10 seems to be missing libstdc++5_3.3.6-17ubuntu1_i386.deb

In order to install the Epson C1100 under 9.10 on the standard i386 platform please open an terminal via ACCESSORIES > TERMINAL & make a directory as explained below to store your installation files;

```
mkdir epson_install
```

move to the installation directory you just created;

```
cd epson_install
```

get the installation files from our website [[COLOR="Blue"]000it.com[/COLOR]]("http://www.000it.com")

```
wget http://000it.com/files/epson_c1100/epson_c1100_install.tar.gz
```

extract the compressed file;

```
tar -zxvf epson_c1100_install.tar.gz
```

install the deb installation files you have just extracted;

```
sudo dpkg -i *.deb
```

from here you can install your Epson C1100 just as you would normally install any other printer using the SYSTEM > ADMINISTRATION > PRINTERS menu. When/if called for the ppd (PostScript® printer description) file, please point to the "epson_install" directory & select the file Epson-AL-C1100-fm3.ppd

This has worked on +20 machines in our group without failure, so please let me know if  you have a better way, &/or if this didn't work for you.

---

### Post by stewartv on 2010-07-28
Been meaning to do this for months.

I had the AL-C1100 working using Marc Higgins' method on 32bit 10.04 but couldn't get it working on 64bit. I messaged Marc who said that I needed to make 64bit versions of the .deb installer packages.

I finally did this:

sudo fakeroot alien -t Epson-ALC1100-filter-1.2-0.i386.rpm
sudo fakeroot alien -t Epson-ALC1100-filter-cups-1.2-0.i386.rpm


sudo alien Epson-ALC1100-filter-1.2.tgz
sudo alien Epson-ALC1100-filter-cups-1.2.tgz


sudo dpkg -i epson-alc1100-filter_1.2-2_all.deb
sudo dpkg -i epson-alc1100-filter-cups_1.2-2_all.deb

It all works perfectly. I installed the printer through CUPS, you end up with a driver called EPSON AL-C1100 ESC/PageS

I have the .deb files if you'd like them emailed to you. Marc offered to host them and I'll get in touch with him.

The process above was suggested by Marc. He's the one to thank.

---

### Post by Jon69 on 2010-11-03
Just wanted to say thanks to Marc Higgins for the reply above (2nd Jan 2010) I also had problems my Epson C1100 wasn't working on Ubuntu 10.10 and the Help gave no answer.

Now sorted thanks to Marc's detailed step-by-step instructions.

I then went to >System>Admin>Printing >  clicked "Add" and created a new name for the printer. It works, so I suppose I can remove the old name.

Nice one Marc.

---

### Post by CycTima on 2010-12-02
After reading this thread and creating my own debs, installing them and still failing, I too followed the instructions from Marc Higgins January 2nd post - and it's absolutely perfect... just printed my test page and it's no trouble whatsoever... 

and this on an EeeBox 1502 running Ubuntu 10.10.... 

So - the solution for installing AcuLaser C1100 on Ubuntu Linux is here...!!!

Hopefully it will appear closer to the top of the google search now... 

I can't believe I just wasted so much time on the earlier solutions given elsewhere, when the most recent solution given here takes about 6 seconds and works perfectly... 


Thanks Marc - 
Tim..

---

