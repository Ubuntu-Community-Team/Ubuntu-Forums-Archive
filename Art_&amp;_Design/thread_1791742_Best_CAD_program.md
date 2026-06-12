---
title: "Best CAD program?"
date: 2011-06-27
forum: Art &amp; Design
---

### Post by Supergibbon on 2011-06-27
Hi,

I'm looking to turn some designs I've scanned in from PDF files into DXF or DWG files so that I can get them laser cut.  Can anyone recommend the best program to do so.  I've just downloaded qCAD but that doesn't give you an option of importing PDF's or Jpeg's and I could really do without having to draw the designs from scratch.
Any ideas?

Cheers,

Iain

---

### Post by jerrrys on 2011-06-27
don't have a clue, but this may help your quest :)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=cad+pdf+jpg+import&sa=Search&cof=FORID:9#1076](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=cad+pdf+jpg+import&sa=Search&cof=FORID:9#1076)

---

### Post by prokoudine on 2011-06-27
PDF or JPEG > Inkscape > DXF

---

### Post by Ievoigh0 on 2011-07-05
I've heard good things about BricsCAD. It's proprietary, but it ain't no $2K

---

### Post by e00878 on 2011-08-12
Draftsight | Dassault Systemes

free Ubuntu native CAD package.

[http://www.3ds.com/products/draftsight/download-draftsight/](http://www.3ds.com/products/draftsight/download-draftsight/)

---

### Post by TheManno1 on 2011-08-12
Anyone willing to share their DraftSight all deb file the one that works in ubuntu 64 bit.

---

### Post by Kira_Belka on 2011-08-14
Brics CAD vs Blender Architect :P also AutoCAD 2005 under wine :)

---

### Post by BK Baal on 2011-08-31
LibreCAD is also good.

---

### Post by arkmundi on 2011-09-09
Not a question of best CAD but file conversion.  I'm using LibreCAD, a branch of QCAD community version and recommend that.  But I too have file conversion problems.  I'd like to convert DWG (native Autocad) to DXF (native everyone else, including QCAD and LibreCAD and most of the rest of the open-standards CAD community, which requires inter-change.)  I've been working on this problem a while and would appreciate any tips if someone has found a solution.  

As for PDF->DWG ... not a clue. Sorry.

---

### Post by Gemnoc on 2011-11-12
Hi,

About PDF to DXF conversion, this may help: [http://linuxaideddesign.blogspot.com/2011/08/how-to-work-with-pdf-files-with-ares.html](http://linuxaideddesign.blogspot.com/2011/08/how-to-work-with-pdf-files-with-ares.html)

As for DXF to DWG conversion, look for TeighaViewer from the Open Design Alliance: [http://opendesign.com/guestfiles/teigha_viewer](http://opendesign.com/guestfiles/teigha_viewer)

Only a 32 bit package is available. If you have trouble installing/using it, you may want to try the Windows version in Wine, it works pretty well.

---

### Post by prokoudine on 2011-11-15
> **arkmundi said:**
> I'd like to convert DWG (native Autocad) to DXF (native everyone else, including QCAD and LibreCAD and most of the rest of the open-standards CAD community, which requires inter-change.)  I've been working on this problem a while and would appreciate any tips if someone has found a solution.

Just use DraftSight

---

### Post by MG&amp;TL on 2011-11-15
IDK if it does the file formats you want, but you could run google sketchup under wine.

---

### Post by Gato303co on 2012-01-04
Are there more differences between Qcad and LibreCad, or the only differences are that LibreCAD is written in Gtk and under a GPL licence?

The DXF support stills in version 2000?
Has a more complete printing layout managing (simlar to model/paper space in AutoCAD)?

Just asking

---

### Post by Gemnoc on 2012-01-04
Hi,

A couple things wrong there!

[LIST]
[*]QCad Community Edition *is* licensed under the GPL, same as LibreCAD.
[*]LibreCAD is not programmed in Gtk. It's using Qt3-Qt4 transitional libraries, while it's being completely ported to Qt4.
[/LIST]

The core functionality between QCad CE and LibreCAD is exactly the same, apart from LibreCad having the polyline tool which is only available in the professional version of QCad.

There is no higher support than DXF 2000 because the DXF format after this version is not documented by Autodesk. There is currently a project to offer a GPL DWG library, called LibreDWG, but after 3 years of existence it's still in Alpha state and no binaries have been published yet.

If you're looking for page layout management comparable to AutoCAD, look at DraftSight (free but not open source).

*Edit: I talked about LibreDWG assuming it could read/write DXF as well, but now I'm not so sure.*

---

### Post by kleinempfaenger on 2012-03-02
From my experience I do not recommend QCad and LibreCad. Those programs are still limited, so most of the time (several months of use last year) I was searching for work-arounds for problems. In fact, there are no great problems, but workflow is limited by little, but important, problems and thousands of unneccesary clicks. Just to mention one problem: creating hatches. QCad (in my version) didn't support automatic boundary recognition, so I had to mark every corner of my hatch boundaries. Impossible! Maybe this problem is solved in the payed version (I don't really know because when I wanted to buy it didn't recognize my VisaCard), but there are several problems like this one in the community version.
Thank God I discovered DraftSight last year, because with QCad I would have never finished my exams in arqhitecture. Try it!

---

