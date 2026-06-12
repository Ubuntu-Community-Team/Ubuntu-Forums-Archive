---
title: "What DVD Authoring Software Is Recommended?"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by gigi1234 on 2007-05-22
I have some *.mpg files that I would like to burn onto DVD disks so that they will play with my DVD player + TV. It would be nice if there was some way to create menus too. 

I looked around Ubuntu town to see what people were using software-wise but really couldn't get a clear consensus. 

I would like something that is intuitive to use (with a GUI). Also I am still running Dapper (why fix what works?), if that makes a difference.

So, anybody, what is your fave app for this kind of thing?

Thanks!

---

### Post by aidanr on 2007-05-22
try out [dvd styler]("http://www.dvdstyler.de/") or [tovid]("http://tovid.wikia.com/wiki/Main_Page")

---

### Post by Inxsible on 2007-05-22
Give K3B a try. It is a good overall software.

---

### Post by ron999 on 2007-05-22
Hi
I use tovid from the command line (CLI). This is the link:- [http://tovid.wikia.com/wiki/Main_Page](http://tovid.wikia.com/wiki/Main_Page)

I do it in stages.

1) Use tovid to convert the file(s) to MPEG2, DVD compliant format.
2) Use makemenu to make a menu, if required.
3) Use makexml to make an xml file.
4) Use makedvd to author the DVD (Creates a VIDEO_TS folder containing IFO, BUP and VOB files).
5) Use K3B to create an ISO image file.
6) Use VLC to test view the ISO.
7) Use K3B to burn the ISO.

There's also a GUI option, but I haven't had any success with it yet. This is the link:-[http://tovid.wikia.com/wiki/Using_the_tovid_GUI#Usage]("http://tovid.wikia.com/wiki/Using_the_tovid_GUI#Usage")



I wrote myself a how-to, I've attached it.
I've also attached my first attempt at making a menu.

---

### Post by gigi1234 on 2007-05-22
Hmmm. Okay the tovid command line method seems like an option perhaps. Except I am going to have to do some work learning and getting up to speed. I don't know anything at all about DVDs. Like what is an XML file? What are BUP, IFO, and VOB files? I have used K3B for burning cds a lot, so I am familar with that. But I'll have to work on the concepts involved in creating the ISO image. 

Anyone know of a good link for a detailed HOWTO?

Thanks!

---

### Post by vanadium on 2007-05-22
DVDStyler probably would suit you best now. It is a graphical tool. It is not on the Ubuntu repositories but I have seen that there are .deb installation files on the website, so it should install rather easily. I just started in Linux and am finding my way in video, so I cannot be of more specific help for now. ToVid, though command line based, seems quite simple to use for basic DVD authoring, and probably will be by far the fastest solution if you regularly have a dvd of home videos to prepare.

---

### Post by gigi1234 on 2007-05-22
I think I will try the dvdstyler for now them maybe look into the tovid method when I am craving a new project. 

Thanks everyone!

---

### Post by ron999 on 2007-05-22
OK
Please let us know if you're successful with DVDstyler.
We'll compare menus maybe. :)

---

