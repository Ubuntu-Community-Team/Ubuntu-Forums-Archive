---
title: "cd / dvd catalogue (catalog) / database"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by zi99y on 2006-02-01
Hi folks,

I have had a search around but can't find anything relating to this.

Problem is, I've accumulated a gazillion cd's and dvd's over the years, and I'd like to catalogue them all in a searchable database type system. Nothing fancy, just directory/file listings. I realise I could quite easily script something to do an ls -R > mydisc.txt on every disc in my collection, but there must be some cool app waiting out there for me that would be a bit more exciting!

Thanks in advance,

the zi95ter

---

### Post by joselin on 2006-02-01
I use GCFilms for dvd and movies, is cool.

[http://home.gna.org/gcfilms/]("http://home.gna.org/gcfilms/")

---

### Post by qpieus on 2006-09-09
Try gtktalog. You can get in via synaptic. It's a simple interface, just what I was looking for.

---

### Post by zi99y on 2006-09-10
thanks qpieus, I've tried various different ways of doing this since I posted but none were that great, gtktalog does seem pretty good though, so thanks!

---

### Post by qpieus on 2006-09-11
You're welcome. I use Advanced Disk Catalog in Windows, which I like a lot. Unfortunately, I couldn't get it to work right via wine or crossover office. The program installs OK, but I can't get it to read CDs or DVDs, it says invalid device or something like that. That's a pain because all my stuff is catalogged in that program's database.

---

### Post by ksenos on 2006-09-27
Hi,

I am trying to find a utility for the same purpose too. I used gtkatalog for quite a long time, but I can't bear the old gtk+ anymore. Isn't there another app that would do the job but depend on gtk2? Thanks a lot.

---

### Post by gurgle on 2006-12-08
^^ i would like to know as well. maybe some kind of database that can run on a LAMP server?

---

### Post by cbsim on 2006-12-11
Gnome Disk Catalog
Hyper's CdCatalog
Gnome Catalog
Indexator.NET
CDCollect
GWhere
rarch

Still looking for something that can replace Advanced CATaloguer on my Windows.

---

### Post by gurgle on 2006-12-13
thanks for the recommendations. I will try them out - anyone have their own ideas?

---

### Post by Lucifiel on 2007-04-22
Thank you all for the recommendations. =)

Before I backup my hard disk, I do want to try cataloguing some of my stuff first.

---

### Post by stinger30au on 2007-07-15
in windows i use this program all the time, i love it
[http://www.lyrasoftware.com//content/view/4/8/](http://www.lyrasoftware.com//content/view/4/8/)

it is disclib

im yet to try it under wine

---

### Post by condamine on 2007-08-09
> **cbsim said:**
> Gnome Disk Catalog
Hyper's CdCatalog
Gnome Catalog
Indexator.NET
CDCollect
GWhere
rarch

Still looking for something that can replace Advanced CATaloguer on my Windows.

I've been looking for a decent Linux solution as well.

On Windoze I use the commercial CDWinder, I have a registered version on Window$ while using the Mac version, unregistered limited to 10 catalogues available at any one time. It is OK but very slow, it also has had a few problems reading  some of the Linux disks I have burnt (SUSE & Ubuntu).

I liked GTKtalog [http://www.nongnu.org/gtktalog/]("http://www.nongnu.org/gtktalog/"), but it is not maintained and I gave up trying to get it to work with bz2 archives. As installed it worked OK with gz archives. I felt I had worked out how to tell it to interpret tar.bz2 files - but the data it generated was garbled.

So then I tried [http://cdcat.sourceforge.net]("http://cdcat.sourceforge.net") known as CdCat by Hyper [http://cdcat.sf.net]("http://cdcat.sf.net"). Clean and simple and when I saw the Import GTKtalog option I thought "beauty Hyper" -- but it uses the xml report format rather than the native database format, too much work to double handle the catalogue files considering that Hyper's CdCat currently has no built in archive support. This one is however under active development and worth keeping an eye on.

Next I had a quick look at CdCollect, the new Gnome 2 replacement for GTKtalog which again has a clean simple interface with active maintenance. [http://cdcollect.sourceforge.net]("http://cdcollect.sourceforge.net"), currently lacking is an ability to create a report and import the catalogues I already have.

Another contender is the GWhere [http://www.gwhere.org/home.php3]("http://www.gwhere.org/home.php3") which is also being actively maintained, but currently has no plug-ins or ability to read archives.

I have not looked at rarch yet [http://rarch.sourceforge.net/]("http://rarch.sourceforge.net/") as it is still in beta (no stable version yet available). I was amused by the screen shots page > rarch is a console based program. If you want a screenshot, download the tarball, compile it and run it.. Worth a look some time down the track is all I can say.

On SUSE, KDE I have used Katalog which again is very slow and has crashed occasionally. I couldn't get it to work as a service in Konqueror  (I'm guessing that it is not included in the usual KDE installation because it has problems). Older versions I tried, a while ago, had a native xml format which I liked, but this version (0.4) uses sqlLite.

So the upshot is there is not an ideal solution at this stage. :(

---

### Post by stchman on 2007-08-09
Are these programs similar to DVD Profiler?

---

### Post by condamine on 2007-08-17
> **stchman said:**
> Are these programs similar to DVD Profiler?

After I checked out the features page at [http://www.invelos.com/dvdpro/Info.aspx]("http://www.invelos.com/dvdpro/Info.aspx"), as I hadn't heard of DVD profiler, I can confidently say that NO the programs mentioned here are not like DVD profiler.
The programs mentioned here I use to create a searchable list of file names on backup CD/DVDs that I burn, as an aid to finding stuff I have backed up and deleted from my current file systems.
Looks like DVD profiler is used for commercially purchased DVDs.

---

### Post by condamine on 2007-09-30
Another entry that is definitely worth a look is [Virtual Volumes View]("http://sourceforge.net/projects/vvvapp/") or [VVV]("http://vvvapp.sourceforge.net/")
From the project summary
> Catalog the content of removable volumes like CD and DVD disks for off-line searching. Folders and files can also be arranged in a single, virtual file system. Each folder of this virtual file system can contain files from many disks.
It uses the [Firebird database engine]("http://www.firebidsql.org")
Has both windows and linux versions
Very simple installation
> VVV does not need to be installed. Everything it needs is contained in is folder.
Just expand the program in a suitable folder and execute "vvv-start.sh".

---

### Post by CosminGC on 2007-12-27
> **condamine said:**
> Another entry that is definitely worth a look is [Virtual Volumes View]("http://sourceforge.net/projects/vvvapp/") or [VVV]("http://vvvapp.sourceforge.net/")
From the project summary

It uses the [Firebird database engine]("http://www.firebidsql.org")
Has both windows and linux versions
Very simple installation

basic, but nice. It could have a bright future.

---

### Post by ilpiero on 2008-06-18
I'm looking too for a program to build a CD database. I just need to catalogue my musical cd collection, does one of the programs mentioned above (just the linux ones) support Cddb/freedb connection ?

Thank you!!

---

