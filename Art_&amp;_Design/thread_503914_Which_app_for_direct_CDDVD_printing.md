---
title: "Which app for direct CD/DVD printing?"
date: 2007-07-18
forum: Art &amp; Design
---

### Post by Coolit on 2007-07-18
I have an Epson RX700 multi purpose printer/scanner which I've setup and it works great under Ubuntu.

It also has a CD/DVD printing tray which if I go to the printer settings tabs I can select as the "tray" so the driver would seem to fully support it :) 

My question is what software would I be able to use for printing to this tray? I've had a look at Glabels but there is no media type for direct CD/DVD printing. I've also had a look at the Gimp's templates and cant see anything.

Any help would be greatly appreciated

Thanks:)

---

### Post by jaffamuffin on 2007-07-19
Depending how you want to do it :)

You could just use gimp / inkscape /scribus / iinsert editor of choice, create a template throurgh trial and error, then edit it as needed.

Or use glabels?

A cooler way would be a little script that you could run eg.  cdprint --name=My\ Album --tracks=tracklist.txt --bgimage=image.png and it would print it to the printer.
You'd need to use maybe imagemajick, and various other tools to handle the input data and create an image.  That might be a lot of work though

---

