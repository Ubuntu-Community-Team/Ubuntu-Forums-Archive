---
title: "Embedding Evince in Ff 1.5.0.1"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by FISHERMAN on 2006-04-02
I used Automatix to install Ff 1.5.0.1.(with all the plugins)
But I would prefer to use Evince(preferably embedded) instead of Adobe Reader.
I followed [this]("https://wiki.ubuntu.com/EvinceMozilla?highlight=%28evince%29") instruction page and I completely deleted Adobe from my system.
I choose Mozplugger in Edit->Preferences->...
But when I try to open a PDF I get <view attachment>
Apparently Mozplugger keeps looking for Adobe Reader. I have now idea how to change it to Evince.
What should I do?

---

### Post by dcstar on 2006-04-02
[QUOTE=FISHERMAN]I used Automatix to install Ff 1.5.0.1.(with all the plugins)
But I would prefer to use Evince(preferably embedded) instead of Adobe Reader.
I followed [this]("https://wiki.ubuntu.com/EvinceMozilla?highlight=%28evince%29") instruction page and I completely deleted Adobe from my system.
I choose Mozplugger in Edit->Preferences->...
But when I try to open a PDF I get <view attachment>
Apparently Mozplugger keeps looking for Adobe Reader. I have now idea how to change it to Evince.
What should I do?[/QUOTE]
Change your preferences to use the Evince application for PDF files.

---

### Post by FISHERMAN on 2006-04-03
[QUOTE=dcstar]Change your preferences to use the Evince application for PDF files.[/QUOTE]
Already did that, it didn't help.

---

### Post by mal on 2006-04-03
As far as I know, there is no option to embed Evince in Firefox to enable it to view pdf files within the Firefox window.  I also would like this cability, so I would be happy if someone comes up with a way to do it.

Mal

---

### Post by mellon85 on 2006-04-13
There is a way!
mozplugger. ( i found it in another post )

you just need to install it and setup /etc/mozpluggerrc

```

application/pdf: pdf: PDF file
application/x-pdf: pdf: PDF file
text/pdf: pdf: PDF file
text/x-pdf: pdf: PDF file
        repeat noisy swallow(evince) fill: evince "$file"   <-- line I added
        repeat swallow(documentShell) fill: acroread -geometry +9000+9000 +useFrontEndProgram "$file"
        repeat noisy swallow(Xpdf) fill: xpdf -g +9000+9000 "$file"
        repeat noisy swallow(gv) fill: gv --safer --quiet --antialias -geometry +9000+9000 "$file"

```

similar is done for Postscript. This gives me an error each time I try to open a pdf within firefox however... evince gives always an error since it doesn't handles application/octect-stream... I can't figure out why the mime type is incorrect...

---

