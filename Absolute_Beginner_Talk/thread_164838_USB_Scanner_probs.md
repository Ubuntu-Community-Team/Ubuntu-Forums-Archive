---
title: "USB Scanner probs"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by Gaspode on 2006-04-23
Hi folk,
        I have wandered over here from fedoraland where I have just spent the last month trying to get my Epson printer/scanner/copier ,stylus CX1500
to talk to my system.The problem probably has a whole lot more to do with what I don't know rather than what fedora cant do.

One good thing to come out of it was that I know a heap more about Linux now than when I started and this time I'm not going to run off back to M$ with my tail between my legs. With a bit more knowledge on board I found ubuntu quite easy to install.

Any way about my scanner.
Epson stylus CX1500 MPR on usb
System is basic desktop PII 600 MHz (more or less)
This setup runs OK with M$ .There are no wiring, coupling, physical incompatibility issues.

gaspode@ubuntu:~$  /usr/sbin/lsusb
Bus 001 Device 002: ID 04b8:080c Seiko Epson Corp.
Bus 001 Device 001: ID 0000:0000

gaspode@ubuntu:~$ sane-find-scanner
found USB scanner (vendor=0x04b8, product=0x080c) at libusb:001:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

gaspode@ubuntu:~$ scanimage -l
scanimage: no SANE devices found
gaspode@ubuntu:~$

If I run the Gnome xsane I get the same thing.

I have not installed any sane backends , there seem to be a heap already onboard and it did not help doing that with Fedora C4. Nor have I mussed
with fstab or specific /etc/sane.d files like epson.conf because it also didnt work in Fedora , and lets face it I haven't got a clue what i'm doing.

Any help really appreciated.
Also please let me know if this is not the right bit of the forum for this level of post.

Regards all.
Gaspode.
P.S.
Does ubuntu have yum ? cant find it and no man entry ?.
Ta
G.:confused:

---

### Post by Zimmer on 2006-04-24
Ubuntu uses Synaptic for package management.. apt-get... it is very easy to use from System>Administration>Synaptic Package Manager . or if you must use the command line  then the apt-get commands are the ones to investigate.

As for your multi Epson device, I have seen similar problems for these on these forums. I have no experience of them, but I get the impression that the drivers are not available. I Have looked at the wiki hardware page and found no mention of ti, which is not good :(
Maybe this thread will give you some help/comfort?
[http://ubuntuforums.org/showthread.php?t=121540&page=2](http://ubuntuforums.org/showthread.php?t=121540&page=2)
SANE reports it is unsupported. 
I have a hardly used AGFA Snapscan Parallel scanner that I had to make redundant when I got XP  4 years ago : no XP drivers!! No SANE support for that either..so I had to go buy a new scanner (I made sure I checked for both XP & Linux support for the new one before I bought it).

---

### Post by campidg on 2006-04-28
Hi folks,

I haven't even got close to trying to make my scanner work on my Stylus XC1500.  I'm still trying to make the printer work.  I tried tried configuring gutenprint using [this]("http://ubuntuforums.org/showthread.php?t=119595&highlight=CX1500") thread but for some reason the Ubuntu online repository no longer had the files I needed to download:

[I]No such file `gutenprint_4.3.99+cvs20051122.dfsg.1-2.dsc'.
No such file `gutenprint_4.3.99+cvs20051122.dfsg.1-2.diff.gz'.
No such file `gutenprint_4.3.99+cvs20051122.dfsg.1.orig.tar.gz' .[/I]

Gaspode (the wonder dog?), sorry I can't help with the scanner issue but I would be greatfull if you let me know how you got your printer working.  I got this printer despite all the warnings from linux hardware guides not to by cheap stuff because it was cheaper than an ink cartridge for my old canon 2100sp.

Cheers

Cam

---

### Post by claydoh on 2006-04-28
The scanner part looks to be a [snapscan]("http://snapscan.sourceforge.net/") variant, and you may need a firmware file for it to work with sane, as well as some configuration. the sane snapscan page is not very easy to understand, so i would suggest a search here in the forums for better help there

>  found USB scanner (vendor=0x04b8, product=0x080c) at libusb:001:002 
looking at the above, there does not seem to be a firmware file that correlates to the vendor and product strings, but you should be able to find a XXXXX.bin file on your scanner's driver cd if you have it.

but upon further digging, [your scanner part may only be supported with a sane backend version built from the latest CVS code at the momment]("http://www.sane-project.org/cgi-bin/driver.pl?manu=+epson&model=&bus=any")

As for the printing bit, try [setting it up as an Epson C46/C48]("http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX1500")

as I do not have this hardware, remember - ymmv

---

### Post by campidg on 2006-04-30
No can do Claydoh.  C46/C48 aren't on the list of printers in the GUI printer installer.  I have some idea that I need a more complete and upto date drivers list but I don't know how to get this.

Cheers

Cam

---

### Post by campidg on 2006-05-03
I got the printer to work using the Epson C42UX driver already in the GUI printer installer as advised on another thread.  

As for the scanner, I have tried downloading and installing the latest sane backends but with no success.  Entering the vendor and product number in the appropriate scanpscan.conf and hotplug mapping file got the scanimage -L command to recognised the device but only once and caused the device to sieze up, refusing to print or be turned off with its own switch and could not even be recognised again by the sane-find-scanner command.  Pulling the plug on the printer/scanner was the only way to reset it.

I looked at the link Calydoh provided and found unstable files for the snapscan driver that specifically state the inclusion of CX1500 support.  I'm no developer but the files look like components rather than the complete driver.  It seems that someone who knows how could build a driver from these components could, but people like me will have to wait for the next stable sane backend version.  But at least it looks as though support fot this scanner will *be in* the next version.......dosen't it?  

The other encouraging thing that I found on the sane sites front page was that the CX1500 was listed as being supported with a "good" rating by the snapscan driver.  I am hoping that this means sane support for the CX1500 is imminent.

Cheers

Cam

---

