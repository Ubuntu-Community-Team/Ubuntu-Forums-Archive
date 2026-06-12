---
title: "open office file saving and dragging"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by resistantgnome on 2007-07-24
Well...initially I liked open office word processor but now it has started irritating me.
Whenever I save a file with some pictures, it takes a hell lot of time to save. And sometimes while I drag the pages, it stucks and does not let me do anythin. Then after 10-15 seconds it allows me to drag. This behaviour of open office word processor is really irritating.

---

### Post by Lycaon on 2007-07-24
Hello resistantgnome,

I friend of mine gave me a document about making ubuntu faster, just some configurations etc.
So i have no clue if this will help with your problem, but on my old laptop Open Office reacts now within some millisecons/seconds:) So this is what you'll have to change:

> openoffice disable java:
1. start up openoffice (writer, for example)
2. go to Tools->Options
3. in the options tree on the left-hand side of the panel, navigate to OpenOffice.org->Java
4. uncheck the box that says "Use a Java runtime environment"
5. close all openoffice windows and restart


Make OpenOffice snappier.
To make OpenOffice snappier, you can adjust the way it uses memory. To do this, launch the OpenOffice word processor and go to the Tools menu and select Options. Highlight &#8220;Memory&#8221; on the left panel.

On the right side of the panel, reduce the number of Undo steps to a figure lower than 100. Adelstein suggests 20, but I use 30 steps, just to be safe. I don&#8217;t think I&#8217;ll have to undo more than that many commands.

Under graphics cache, set &#8220;Use for OpenOffice.org&#8221; to 128 MB (up from the original 6MB).
Set memory per object to 20MB (up from the default .5MB).
Set the number of objects under &#8220;Cache for inserted objects&#8221; at 20.
Check OpenOffice.org Quickstarter.

Click the OK button and close OpenOffice. Start it up again to experience the change in speed.


I take no credits for these tips, these are just from this forum or the net:)

Hope it helped ya!

---

### Post by resistantgnome on 2007-07-24
Open  office now opens faster but my previous problems still exist.

---

### Post by tombott on 2007-07-24
Cheers for those tips, Open Office opens really quickly now!

---

### Post by Lycaon on 2007-07-24
> **resistantgnome said:**
> Open  office now opens faster but my previous problems still exist.

Sorry for you, i thought it mayb was some memory issue. I've personally never experienced your problems, hopefully someone else can help ya.

In worst case, reinstalling OOo?

---

### Post by AndyCooll on 2007-07-24
You could try Abiword and Gnumeric.

Unfortunately the biggest complaint against oOo has always been its slow response times, the above two apps are GNOME's Writer and Calc equivalents and are alot lighter apps.

:cool:

---

### Post by resistantgnome on 2007-07-24
> **tombott said:**
> Cheers for those tips, Open Office opens really quickly now!

I never had any opening problems. It takes lot of time while saving and sometimes stucks for few seconds during dragging.

---

