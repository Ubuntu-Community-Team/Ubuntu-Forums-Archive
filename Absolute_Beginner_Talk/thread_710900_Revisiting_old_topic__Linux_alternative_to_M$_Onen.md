---
title: "Revisiting old topic:  Linux alternative to M$ Onenote or annotating PDFs"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by michael37 on 2008-02-29
There were several threads on this subject, but none of them really talk about the find I made.

I am back to school and I couldn't seem to live without M$ OneNote.  Professors distribute class notes in PDFs (occasionally in PPTs), and I find it very efficient to take notes directly on the lecture notes by freehand annotation of PDFs.  OneNote 2007 has this feature build in and I ALMOST switched to Windows until I discovered.... (suspense)

Please note the following
[LIST=1]
[*]I do not have a tablet PC.  I use mouse/touchpad for freehand drawing and keyboard for text entry
[*]I do not care about freehand notes on empty piece of paper.   I only take notes on existing PDFs or PPTs.
[/LIST]

Here are products that I tried and they either don't have this feature or I haven't found the feature.
[LIST]
[*]NoteCase
[*]BasKet Notes (KDE)
[*]Tomboy Notes
[/LIST]

So I thought I was out of luck until I found [Xournal]("http://xournal.sourceforge.net/").  Installation on modern versions of Ubuntu is trivial: ```

sudo apt-get install xournal

```

Start **Applications / Accessories / Xournal**, select **File / Annotate PDFs** and go for it.

It says it works on tablets/freehand writing, but I don't have one so I can't try.

OpenOffice 2.3.1 doesn't have any problems opening PPTs, but it struggles often with PPTXs (import works but slides are kinda broken).    The latter are very uncommon for now.  Print to PDF is standard Ubuntu feature.

---

### Post by gimfred on 2008-02-29
I'd hazard your best bet is to run Windows in a virtual machine and use Onenote that way.

---

### Post by michael37 on 2008-03-01
> **gimfred said:**
> I'd hazard your best bet is to run Windows in a virtual machine and use Onenote that way.

Does it work well for you?  Do you use Onenote 2003 or 2007?  Btw, 2007 is the only one that has integrated PDF annotation capabilities.  

I have Virtual Box running and M$ Office 2007 does not work well in it.  I think it has to do with the inefficient graphics implementation of the Virtual Box, but AFAIK M$ Office 2007 is very graphics intensive and simulated graphics drivers of virtual machines is not that good.

---

### Post by jethro amalgamation on 2008-03-05
Just wanted to say thank you for the xournal recommendation. I feel like onenote was my final holdout in vista, not anymore

---

### Post by gimfred on 2008-03-15
I don't own any microsoft products sorry. It was just an observation.

---

