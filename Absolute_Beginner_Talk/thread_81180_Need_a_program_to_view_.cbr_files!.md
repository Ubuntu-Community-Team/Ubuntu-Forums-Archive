---
title: "Need a program to view .cbr files!"
date: 2005-10-23
forum: Absolute Beginner Talk
---

### Post by Daniel Rehm on 2005-10-23
Comical won't compile (it won't let me do ./configure) and CDisplay under wine crashes if I try to open a file.

I don't want to have to extract the files out of my .cbrs and read them one by one. Please help!

---

### Post by rykel on 2005-10-23
Use **cbrPager**, a no-nonsense pager for comic book files.

Search for and download its autopackage [here]("http://www.autopackage.org/packages").

cheers!

---

### Post by Daniel Rehm on 2005-10-23
[QUOTE=rykel]Use **cbrPager**, a no-nonsense pager for comic book files.

Search for and download its autopackage [here]("http://www.autopackage.org/packages").

cheers![/QUOTE]
Thanks! I was a bit confused by the .package file, but once I figured out what to do with it, it installed smoothly.

It seems like a decent enough application, although I still miss CDisplay's style of navigation.

Anyway, I can now read comics! That's the important thing.

---

### Post by rykel on 2005-10-23
tat's great!!

do hope tat u can support autopackage.   :D 

btw, which types of comics r u reading?

i go for a couple myself... garfield/foxtrot types, marvel/DC, anime types and hong kong fighting comics (altho' these are really rare to find online!)

---

### Post by wmcbrine on 2005-10-24
Interesting, I never heard of these. Where would I find some?

Do you know why someone might use this format over, say, PDF?

---

### Post by rykel on 2005-10-24
[QUOTE=wmcbrine]Interesting, I never heard of these. Where would I find some?

Do you know why someone might use this format over, say, PDF?[/QUOTE]

you can find them under "comics" category on virtually all bittorrent search sites, such as torrentreactor.net.

as for the advantages of the format, i have no idea... but there must have been a good reason why cbr was chosen in the first place.

---

### Post by jdusablon on 2006-05-02
Comix.

Very similar to cdisplay. Just ```
sudo apt-get install comix
``` and you're on you're way. Nuff said.

It lives in Universe, so make sure that repository is enabled.

---

### Post by azazel- on 2006-05-03
I found that you might need to install unrar as well.  It was the only way I could get Comix and cbrpager to open some files.

---

### Post by arsenic23 on 2006-05-03
.cbr is just a rar file with a changed extention
.cbz is just a zip file with a changed extention

( yeah I like comix best myself )

Anyway, I think the big reason these are perfered over pdf is because just about anyone who can scan in a book can rar or zip the numbered pages into a file and rename the extention.  Not as many people would know or be able to make a pdf.  I'm fairly sure the idea is the increase the number of scanners in the pool.

---

### Post by MaX on 2006-05-09
[QUOTE=arsenic23].cbr is just a rar file with a changed extention
.cbz is just a zip file with a changed extention

( yeah I like comix best myself )

Anyway, I think the big reason these are perfered over pdf is because just about anyone who can scan in a book can rar or zip the numbered pages into a file and rename the extention.  Not as many people would know or be able to make a pdf.  I'm fairly sure the idea is the increase the number of scanners in the pool.[/QUOTE]

PDF Doesn't work well with different sized images (pages), thus it can't be shown in a good way on screen.

---

### Post by yesindeed on 2006-06-04
I'm having this same problem.

I'm trying to read a cbr file. I installed that comix program, but it couldn't read it.  Then I read the thing about unrar, so I tried to install that, but I couldn't find unrar, only unrar-free, so I installed that, then linked /usr/bin/unrar to /usr/bin/unrar-free. Still doesn't work. Anyone have any ideas how to get it to work?

---

### Post by HerrEkberg on 2006-06-05
I believe it is called **unrar** in Dapper and **unrar-nonfree** in previous versions of Ubuntu. Both seem to be in the multiverse.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=unrar&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=unrar&searchon=names&subword=1&version=all&release=all)

---

### Post by Gaijin on 2006-06-13
Strangely despite having both rar and unrar-free installed comix still fails to open cbr's?

I also cannot find unrar or unrar-nonfree in the archive despite the fact that they are listed there

Any clues?

Failing that if anyone can whip up a batch script using the apps I have to convert CBR's to cbz's that would keep me going and be most appreciated

---

### Post by HerrEkberg on 2006-06-14
I have no idea why you can't find unrar/unrar-nonfree, someone familiar with the Ubuntu package system has help you with that.

The **unrar-free** program does not have all the necessary features and is also unable to open many RAR-archives, especially newer ones. The **rar** program, on the other hand, is created by the same people who creates unrar, and it's features are essentially a superset of unrar's. While the extra features present in rar (support for RAR file creation) is not needed by Comix, there are no reasons why it could not be used only for unpacking. The next version of Comix will support both **rar** and **unrar** transparently.

In the meantime you could just uninstall unrar-free and create a symlink to `rar` called `unrar`, that should solve it.

---

### Post by Kilz on 2006-06-14
If anyone wants the latest version of comical I created a few .deb's for friends. They are available from my homepage. [http://tghc.org](http://tghc.org)

---

### Post by Gaijin on 2006-06-15
Thanks for the quick responses!

I solved this in the end by grabbing unrar-nonfree from a debian repository and installing from there, dont' know why I didn't think of this sooner!

If possible could someone update the multiverse repo with the above .deb, it would save others getting stuck

---

### Post by sh4d3z on 2007-01-11
i never heard of cbr until i found the lone wolf and cub series... 
i found this script 
[http://shii.org/cdisplay]("http://shii.org/cdisplay")
it will require unrar
```
sudo apt-get install unrar
```
works great just type cdisplay followed by the cbr file
-nic

---

### Post by ricardisimo on 2007-04-03
> **arsenic23 said:**
> .cbr is just a rar file with a changed extention
.cbz is just a zip file with a changed extention


Riddle me this, Batman:

I took several comics in rar archives, changed the extension to cbr, and voila - they open automatically with Comix, and even Nautilus previews them as comic books, with the front cover as the icon. However, try having nautilus sort by type, and the cbrs I created won't group with my existing cbrs in the same folder. They stay right next to the cbzs I created using "convert" in Comix. How does that work? Odd, no?

---

### Post by cloneofme on 2007-05-17
> **jdusablon said:**
> Comix.

Very similar to cdisplay. Just ```
sudo apt-get install comix
``` and you're on you're way. Nuff said.

It lives in Universe, so make sure that repository is enabled.

cheers for that! made my life alot easier

and now on to reading civil war :D

---

### Post by Blario on 2008-04-09
> **Kilz said:**
> If anyone wants the latest version of comical I created a few .deb's for friends. They are available from my homepage. [http://tghc.org](http://tghc.org)

I  would LOVE to have comical back again.  I used it on Edgy, but I can't get it to compile on Gutsy now....

Anyone know why the .8, .7, & .6 won't compile?  Or where I can find a deb of it.... ????

---

### Post by Nider on 2008-04-11
I have some problems with Comix... it doesn't open .cbr files... do I need to install "unrar" is this a application that allow to read .rar files, because I tried to change the extension of my .cbr files to .rar and still couldn't open them

EDIT: Yes, I needed to install unrar... :p ready to read comics

---

