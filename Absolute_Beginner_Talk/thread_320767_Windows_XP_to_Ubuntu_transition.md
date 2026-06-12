---
title: "Windows XP to Ubuntu transition"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by mtibesar on 2006-12-17
Hello,

I am contemplating abandoning Windows XP and transitioning to Ubuntu.

Which linux/ubuntu program(s) would replace the following Windows programs that I seem to always use:

Notepad (HTML editor)

WS_FTP (ftp transfers)

Microsoft Money (personal finance)

Internet Explorer 7 (my browser)

Microsoft Digital Image Suite (photo touchups)

Microsoft Office

TurboTax (personal taxes)

Nero (cd/dvd burning)

Family Tree Maker (family genealogy)

Any assistance or recommendations are sincerely appreciated!

Hoping to be ex-Windows user soon!

Marc

---

### Post by d3v1ant_0n3 on 2006-12-17
I'll reply for the ones I know:

Notepad can be replaced with gedit (gnome editor) and many, many other text editors. Comes as default with ubuntu.

IE7 can (and should) be replaced (both on windows and linux) with Firefox. Ubuntu Dapper comes with 1.5 as default, Edgy comes with 2.0.

MS Office can be replaced with (in 90% of cases) Open Office. Comes as default with Ubuntu. There are some very specialist tasks that OO can't do, but I've never run into them personally.

Nero can be replaced with Gnomebaker (comes as default with Ubuntu) or k3b, which has a more nero-like feel, but needs to be installed seperately.

No idea about the rest, I'm sure other people might be able to help tho':D

---

### Post by benuski on 2006-12-17
[This]("http://www.ubuntuforums.org/showthread.php?t=33183") post should have everything you're looking for.

---

### Post by rbprogrammer on 2006-12-17
> **mtibesar said:**
> 
Notepad (HTML editor)
WS_FTP (ftp transfers)
Microsoft Money (personal finance)
Internet Explorer 7 (my browser)
Microsoft Digital Image Suite (photo touchups)
Microsoft Office
TurboTax (personal taxes)
Nero (cd/dvd burning)
Family Tree Maker (family genealogy)


both ubuntu and kubuntu have basic text editors like the notepad (in kubuntu its KATE - KDE Advanced Text Editor)

firefox can replace internet explorer.

open office replaces microsoft office

and there are a plethora of cd/dvd burning software.  in kubuntu, you can use K3B.

i'm not familiar with the other programs you mentioned, but i'm sure you can find something that does the same thing.  or you can use the windows version and run them under [wine]("http://www.winehq.com"). as for firefox and open office, they both have windows versions, so you can test them out on windows before migrating to linux.

---

### Post by riven0 on 2006-12-17
> **mtibesar said:**
> 

Notepad (HTML editor)

Gedit, Kate, Nedit

> WS_FTP (ftp transfers)

Gftp, Konqueror, Nftp

> Microsoft Money (personal finance)

GNUcash, Kmymoney

> 
Internet Explorer 7 (my browser)

Firefox, Opera, Epiphany, Konqueror

> Microsoft Digital Image Suite (photo touchups)

Gimp

> Microsoft Office

Open Office, Abiword, StarOffice

TurboTax (personal taxes)
> 

Not sure. Never checked on this.

Nero (cd/dvd burning)

K3b

> Family Tree Maker (family genealogy)

Not sure about this one.

For more info, [this is a good place to look at]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html").

---

### Post by reiatzu on 2006-12-17
mtibesar, I highly advise that you dual boot Win32 with Ubuntu for the time being. It's an easy step. You simply have to modify your partition table so that there's space for your / & swap. Perhaps if you'd like your /boot directory on another partition or alternatively something else you're free to add another primary/extended partition. This way you'll be able to decide on which OS to use upon boot.

---

### Post by aysiu on 2006-12-17
I'll give you some suggestions in **bold**, but I think you should take this migration as slowly as possible. Your first step should be getting used to using open source software in Windows XP. Try [Notepad++](http://notepad-plus.sourceforge.net/uk/download.php) instead of Notepad, [Firefox](http://www.mozilla.com/en-US/firefox/) instead of Internet Explorer, [FileZilla](http://sourceforge.net/project/showfiles.php?group_id=21558) instead of WS_FTP, [OpenOffice](http://download.openoffice.org/2.1.0/index.html) instead of MS Office, and [GIMP](http://www.gimp.org/windows/) instead of Digital Image Suite.

Get used to using those programs in Windows first. When you feel you're ready to get off Windows-only software, try the Ubuntu live CD (officially called the **Desktop CD**). The live CD runs completely off the CD itself and your computer's RAM. It does not touch your hard drive in any way. It also gives you a complete (albeit slower than a regular installation) working environment so you can see what Ubuntu's like and what hardware problems you might run into later.

After you play with Ubuntu's live CD for a couple of weeks, set up a dual-boot. Gradually, you can wean yourself off Windows and then erase it completely.

I'd say you should give yourself two months for the entire migration process--one month using open source programs in Windows, two weeks on the live CD, two weeks with a dual-boot...

Notepad (HTML editor) ** Gedit**

WS_FTP (ftp transfers) **FireFTP** (but you can also use gFTP or KFTPGrabber or a whole host of other FTP clients.

Microsoft Money (personal finance) **KMyMoney**? I don't know. I don't use financial software.

Internet Explorer 7 (my browser) **Firefox** (or Opera or Konqueror or Epiphany)

Microsoft Digital Image Suite (photo touchups) **GIMP**

Microsoft Office **OpenOffice**

TurboTax (personal taxes)  **GnuCash**?

Nero (cd/dvd burning) **K3B** (or Nautilus)

Family Tree Maker (family genealogy) **GRAMPS** (or geneweb or lifelines)

Here's an entire webpage devoted to Linux equivalents to Windows software:
[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

For downloading and burning Ubuntu, this guide will help:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

When you get down to actually installing the dual-boot, this will help:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by reiatzu on 2006-12-17
Thats a wise step aswell, on the Ubuntu 6.10 installer CD, it includes some applications that're found on Ubuntu but which have been ported to Win32. Gaim/Firefox/Abiword, amongst others. You should check that out. It's not a hard transition, dualbooting would keep you comfortable.

---

### Post by mtibesar on 2006-12-17
Wow, thanks for the expeditious and super help Everyone!

With this kind of community support I feel more confident than ever in making the jump to Ubuntu.

Based on all of the great replies it appears that the only program I "may" have a problem with is Family Tree Maker (genealogy).

Does anyone know of a ged-com compliant genealogy program that works in linux/ubuntu?

THANK YOU ALL AGAIN!

Marc

---

### Post by aysiu on 2006-12-17
> **d3v1ant_0n3 said:**
> 
MS Office can be replaced with (in 90% of cases) Open Office. Comes as default with Ubuntu. There are some very specialist tasks that OO can't do, but I've never run into them personally. I've encountered one or two--changing case to anything except upper or lower (e.g., title case or sentence case) and making charts out of pivot tables. Other than that, OpenOffice is pretty robust... especially for a free product.

> Nero can be replaced with Gnomebaker (comes as default with Ubuntu) or k3b, which has a more nero-like feel, but needs to be installed seperately. Actually, [Gnomebaker's not in the list of packages *ubuntu-desktop* depends on](http://packages.ubuntu.com/edgy/metapackages/ubuntu-desktop). Are you sure about that?

---

### Post by mtibesar on 2006-12-17
Disregard my question re: Family Tree Maker. I see that this windows program has some linux alternatives (GRAMPS, geneweb and lifelines).

Wow. Simply amazing all the linux desktop software that is available!

THANKS TO ALL and Merry Christmas!

---

### Post by aysiu on 2006-12-17
> **mtibesar said:**
> 
Based on all of the great replies it appears that the only program I "may" have a problem with is Family Tree Maker (genealogy).

Does anyone know of a ged-com compliant genealogy program that works in linux/ubuntu? I listed you three pieces of genealogy software for Ubuntu. I'm not sure if they're GEDCOM-compliant, but there's definitely software that is (just may not be easily installable). This is what a Google search turned up: > Current status of Open Source genealogy software
Open Source genealogy software is still relatively new and there is still much work to be
done. However, because they are Open Source, you will find many of the newest innovations and
coolest features in these programs. You will also find that they will change and mature faster than
traditional programs. Following is a list of the top 10 genealogy projects on SourceForge.net
3
([http://sourceforge.net/softwaremap/trove_list.php?form_cat=284](http://sourceforge.net/softwaremap/trove_list.php?form_cat=284))
1. PhpGedView - PhpGedView parses GEDCOM 5.5 genealogy files and displays them on the
internet in formats and charts that you are familiar with. It is also allows relatives to edit their
genealogy online and collaborate together on their research.
[http://www.phpgedview.net](http://www.phpgedview.net)
2. phpmyfamily - phpmyfamily is a dynamic genealogy website builder allowing geographically
dispersed family members to co-ordinate and share research. Users can import and export
GEDCOM files, upload images and document transcripts and monitor changes to
individuals.
[http://www.phpmyfamily.net/](http://www.phpmyfamily.net/)
3. LifeLines - LifeLines is a genealogy program to help with your family history research. Its
primarily strengths are its powerful scripting language and the ability easily import and
Open Source Genealogy Software
John Finlay
Page 2 of 5
Page 3
export information in the GEDCOM format.
[http://lifelines.sourceforge.net/](http://lifelines.sourceforge.net/)
4. GDBI - Gedcom DataBase Interface - GDBI is a genealogy program integrator. It includes
an editor and the lifelines report language. It interfaces to 3 GEDCOM databases:
phpGedView, GenJ, and jLifelines. At the core is a common Java API to simplify adding
more databases and editors.
[http://gdbi.sourceforge.net](http://gdbi.sourceforge.net)
5. gramps - GRAMPS is a GNOME genealogy program for Linux and FreeBSD that allows
you to easily build and keep track of your family tree.
[http://gramps.sourceforge.net/](http://gramps.sourceforge.net/)
6. GenealogyJ - GenealogyJ (GenJ in short) is a full-featured standalone Java application that
can handle all of your genealogic information (GEDCOM compliant). It provides different
graphical components for working on your Family Tree.
[http://genj.sourceforge.net/](http://genj.sourceforge.net/)
7. Retrospect-GDS - A web app designed to display genealogy information. Data can be stored
in one of several databases including MySQL. Supports multiple languages. The look and
feel can be changed easily using the built in templating system.
[http://www.infused-solutions.com/retrospect/](http://www.infused-solutions.com/retrospect/)
8. GenerationX - A Cocoa Genealogy Tool - GenerationX is a genealogy tool for Mac OS X
written entirely in Cocoa and conforming to the GEDCOM 5.5 standard for storing
genealogy data.
[http://homepage.mac.com/nowhereman77/GenX](http://homepage.mac.com/nowhereman77/GenX)
9. Poplar Gedcom Viewer - View and edit genealogy dynamically on a web site with
PHP/MySql. Loads standard GEDCOM files. Includes both standard and tree views,
comprehensive searches, themes, privacy module, guest book, GEDCOM download,
GENDEX output, photo module, multi-lingual.
[http://poplar.sourceforge.net/](http://poplar.sourceforge.net/)
10. Genealogy - A Java app for the entry, storage, and networking of genealogical information.
Unlike most other genealogical database programs, Genealogy uses the rich GENTECH
model rather than a custom one or GEDCOM, and can network remote genealogical
databases.
[http://genealogy.sourceforge.net/](http://genealogy.sourceforge.net/) **Edit**: GRAMPS appears to be GEDCOM-compliant, too:
[http://gramps-project.org/gramps-manual/gramps-manual-en/ch03s05.html](http://gramps-project.org/gramps-manual/gramps-manual-en/ch03s05.html)

---

### Post by aysiu on 2006-12-17
> **mtibesar said:**
> Disregard my question re: Family Tree Maker. I see that this windows program has some linux alternatives (GRAMPS, geneweb and lifelines).

Wow. Simply amazing all the linux desktop software that is available!

THANKS TO ALL and Merry Christmas!
Please do take my advice about taking it slow, though. The #1 reason people get frustrated with migrating to Ubuntu is too-high expectations/taking it too quickly.

Really do start with GIMP, Firefox, OpenOffice, FileZilla, and Notepad++ on Windows first. And, as always, you can ask questions here if you have any--even for those programs on Windows.

---

### Post by macogw on 2006-12-17
> **mtibesar said:**
> Wow, thanks for the expeditious and super help Everyone!

With this kind of community support I feel more confident than ever in making the jump to Ubuntu.

Based on all of the great replies it appears that the only program I "may" have a problem with is Family Tree Maker (genealogy).

Does anyone know of a ged-com compliant genealogy program that works in linux/ubuntu?

THANK YOU ALL AGAIN!

Marc

GRAMPS directly edits the GEDCOM file.  It also has very pretty graphical reports it can print out, and it does webpage generating from the GEDCOM.  It's a great program.  It can also merge GEDCOM files together--something I had to do when I got in touch with a distant relative who had his part of the tree done.  His genealogy program either couldn't do it, or he didn't know how to use it right.

---

### Post by Simanek on 2006-12-17
Notepad: Gedit comes standard on Ubuntu and if you go through the preferences you'll find that it can be set up to be an excellent html editor. It blows away Notepad really. If you've used TextPad for Windows, it's more like that.

Genealogy: GRAMPS is excellent. It can import your GEDCOM files for sure. Like the post above stated. I have only recently started working on my family genealogy, but I've been delighted with the available features.

Web:Firefox, Konqueror and I think you can get Opera as well as many others.

FTP: gftp is nice and simple. The version with 6.10 is much more polished than the one on 6.06.

Photo Editing: the GIMP is a powerful application equivalent to Photoshop. The new F-Spot photo manager might be more like what you are looking for. It's pretty good and getting better.

All of these apps come with the standard Ubuntu install except for GnuCash, gFTP and GRAMPS. If you are looking for a larger html editor, check out Quanta Plus. It uses the Qt tools or libraries, so it's actually a KDE application (and it looks like a KDE app), but you can use it all the same with Gnome (Ubuntu's default, um, Desktop Environment). Lots of cool features.

Also, if you want a great music manager that also allows you to delete and add music to your iPod, I recommend getting Amarok. Rhythmbox is good, and you can play music off of your ipod, but you can't delete or add tracks with it. Amarok also has support for downloading album covers automatically if you have used iTunes 7. Though, it does not have a 'Cover Flow' view yet.

---

### Post by mtibesar on 2006-12-17
Thanks Everyone. All of your suggestions are really sound.

I will carefully draft up an inventory of Windows programs that I rely upon and then investigate thoroughly your recommended Linux alternatives (installing the "Windows" versions of all that are available).

I'll then draft a formal transistion plan that includes dual-boot implementation. I'll ensure the timing is right (i.e. after completing my 2006 taxes!) and then begin the move.

I'll study the forums and ensure my hardware is all compatible (AMD64; ATI Radeon 9600; 2gb DDR; 200gb harddrive; Nvidia network/ethernet; etc. etc.)

I used DOS and Unix many years ago so I am confident that I can make a successful transition without ever looking back.

I have been wanting to transistion for over a year now and based on the abundance of quality Linux desktop applications; I see no reason to put it off any longer. My New Years resolution will be to get off the Microsoft moneywagon once and for all!

Thanks and again, Merry Christmas to all.

Marc

---

### Post by Terryj1974 on 2006-12-17
To quote Obi-Wan Kenobi "You just taken the first step into a larger world".

I would recommend you go to sourceforge.net as they have an extensive list of software that is free that you can use. Most of the products that I have tried out there (esp phpMyAdmin) have been extremely helpful.

Best of wishes with your transition - we are here to help if you need us.

TJ

---

### Post by 3rdalbum on 2006-12-18
I'm surprised nobody mentioned this: Nautilus (the built-in file manager in Ubuntu) can be used as a simple FTP client. You go to the Places menu, then "Connect to Server". Put in your FTP login information, and the FTP site appears as a folder on the desktop. Double-clicking on the folder connects to the server and asks for your password.

What's even better is that you can save your passwords into a Keychain. Now you don't have to remember every single FTP site password - just remember the master password for your Keychain, and you're all set!

Getting off a proprietry operating system is a great New Years Resolution. Switching to Ubuntu was a great way to start my year :-)

---

### Post by steve.horsley on 2006-12-18
I was about to say that! Nautilus does pretty-much anything I would want of an FTP client.

It also burns data CDs and DVDs (Go -> CD/DVD Creator). Then drag files into that window from another window. Easy.

---

### Post by macogw on 2006-12-18
> **steve.horsley said:**
> I was about to say that! Nautilus does pretty-much anything I would want of an FTP client.

It also burns data CDs and DVDs (Go -> CD/DVD Creator). Then drag files into that window from another window. Easy.

One problem with Nautilus for burning though:  it doesn't allow super-low write speeds.  The slowest it would allow me is 9.1x, I think.  Gnomebaker lets you get 4x, which was what I needed to get livecds that worked.

---

