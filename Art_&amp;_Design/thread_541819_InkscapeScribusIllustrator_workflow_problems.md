---
title: "Inkscape/Scribus/Illustrator workflow problems"
date: 2007-09-03
forum: Art &amp; Design
---

### Post by nikkkko on 2007-09-03
Hi,

About a year ago I started producing a colour brochure in Inkscape for our company.  Artwork went to the printers, printing happened and all was good. We are a small part of a larger group who recently asked us re-design some technical manuals and to use the look from the brochures.  All is no longer good.

Firstly, the manuals are several pages long, a job better suited to Scribus.  Can Scribus open any output from Inkscape in any format that retains a semblance of the original look?  Not on my Kubuntu install.

Secondly, neither Scribus, nor Inkscape, (nor Xara for that matter), can open any output from a recently contracted independent graphic artist who uses Illustrator on her Mac.

What I desperately need is some kind of base file format for the transfer of work from Inkscape to Scribus to Illustrator and back again.  Which one, (eps or svg perhaps?), and what do I need to get it to work?

Thanks in advance for any suggestions.

---

### Post by bakermiller on 2007-09-04
i think if you save as plain .svg and not native inkscape .svg, scribus will import it no problem.

---

### Post by nikkkko on 2007-09-04
You are right - going from Inkscape to Scribus is possible with plain svg, except that many errors are produced and text layout is different. I can correct by hand.  I haven't yet managed to import .svg from Illustrator.

However, I imagine that I am not the first person to come up against these problems and wonder if I should invest my time in a plain .svg solution.

---

### Post by nikkkko on 2007-09-11
Is there no one out there who uses Scribus and has to exchange files with an Illustrator user on a regular basis?

Help!

---

### Post by bakermiller on 2007-09-11
scribus and illustrator contain all types of objects: text, bitmaps, tables, vectors. ...some elements migrate well, others not so well or not at all.... what are you trying to edit from the .ai file? Please give more info...

...have you tried exporting .eps from illustrator to import in scribus?

earlier, you mention text layout to be off when you import .svg into scribus... You can make paths from the fonts, it should import ok in scribus as plain .svg....also you should keep things seperate: gimp for bitmap, inkscape for vector, and scribus to assemble the final layout with the text....then export as .pdf,..as in, don't use inkscape or gimp for text unless you really have to...

---

### Post by kayosiii on 2007-09-13
You will probably want to convert all text to curves before exporting (path->Object to path) as the main difficulties with Inkscape->Scribus are with the sizing of text elements. As said before plain SVG is more compatible. I don't know if scribus supports SVG filters so blurs might  not translate over.

Or

 Since you probably know the output resolution of the booklet you are creating you can simply export as bitmap from inkscape and insert that into Scribus this shouldn't cost you much if anything in terms of quality.

With regards to an external artist using Illustrator. First of all the bad news Illustrator is a very complex and proprietory file format as far as I know there are no specs available for developers to write import filters for it meaning everything would have to be reverse engineered taking considerable time and effort.

The good news however is... Illustrator also supports SVG (unless adobe dropped that completely in the very recent past) so you can ask your outside artist to send the file as an SVG. (You might also want them to convert text to curves for this)....

Also just like Inkscape if you know your output size and resolution you can request an exported bitmap file (say a tiff) in addition to the svg and ai files.

Hope this helps....

---

### Post by bakermiller on 2007-09-13
i had found this before, but never got to get it working. maybe you would have more luck...

[http://wiki.inkscape.org/wiki/index.php/PDF_Tools]("http://wiki.inkscape.org/wiki/index.php/PDF_Tools")

---

### Post by nikkkko on 2007-09-14
Thanks for all that input.  I will concentrate on getting simple svg working between Inkscape and Scribus and lower, (forget), my expectations for Illustrator.  

The fact is, I have this week discovered that my workflow problems go so deep that exchanging files efficiently between Illustrator and Scribus/Inkscape is now irrelevant.  I just discovered that the .pdf files the Illustrator user has been sending me for proofing show different colours depending on whether I use Ghostview, KPDF or Acroreader to view them. Somtimes none of them show the correct colours. Green doesn't become red, but RGB percentages are seriously off and I effectively lost a couple of week of work. I have no idea why this is happening, but I do feel pretty silly [..wipes egg off face..] for even suggesting we might be able to work in a mixed environment.

---

### Post by maruchan on 2007-09-15
Sounds like color management problems - is the Illustrator designer working in CMYK? Because you're working in RGB, so you'll definitely see color differences. If I were you, I'd have the artist work in RGB (easy to switch in Illustrator) and tell her to send you PNGs at 300 dpi instead of PDF. You'll be able to use the PNGs just fine in Scribus/Inkscape. Print shops will be able to work with that just fine.

Once you start working with PDFs, it's *very* easy to get in over your head; PDF is a powerful medium for printing but you need to know what you're doing.

---

### Post by nikkkko on 2007-09-16
The designer is working in Pantone colours, which probably doesn't help. I've switched to png's as you suggest, but the colour differences on pdf are baffling.  For example, I've opened the files on another kubuntu distribution, (I'm running Fiesty, the other one Dapper), and they look OK.  I'm betting they would look OK under windows too, although I haven't tried it, and am tempted to point the finger at my hardware/software setup.  

I'm not going to worry about it, just stick to png's until Adobe decide to embrace open source and liberate their ai format.

---

### Post by maruchan on 2007-09-18
Yeah, Pantones are meant to be used in a color-calibrated workflow, so unless you've spent the time setting up your system to respond to the needs of a pantone workflow, you are going to see some whack colors. I work with another print designer all the time, and PNGs are the "when everything else may fail" solution.

---

### Post by nikkkko on 2007-09-19
To be perfectly honest, I am discovering that outside of the open source world, (where I've been living for the last 4 years), I am somewhat lost.  Easy enough to create artwork and go to print without stepping outside of linux, incredibly difficult when it comes to dealing with Mac/Adobe users.

Having said that, I am now able to import Illustrator svg files into Inkscape, and I am now using png to verify colours. 

If you have any pointers or references to material which tells me how I can better set up my system with regard to colour and pantone, I would be grateful.

---

### Post by maruchan on 2007-09-19
Here's a very good article about Pantone colors and Linux:

[http://www.linux.com/articles/49236](http://www.linux.com/articles/49236)

Linux color management:

[http://en.wikipedia.org/wiki/Linux_color_management](http://en.wikipedia.org/wiki/Linux_color_management)

Check out the "External Links" section on that last one.

Also, the folks at linuxprinting.org and the Scribus developers tend to be very knowledgeable when it comes to color printing and Pantone/CMYK issues. The Scribus wiki is incredibly helpful.

---

### Post by nikkkko on 2007-09-21
I am starting to realise just how little I know about colour, however...

The designer is now sending me .svg files and the colours are accurate when they are opened in Inkscape in that the rgb values match - as you would expect.  I also have a laser printout by the designer which went through a professional print shop and when I compare this to the image in Inkscape on my screen, the colours appear very close. Then, when I print from another professional print shop from my own Inkscape derived files, the colours also match.

So far so good.

I would like to use my own HP Colour Laserjet 2605 for proofing, but when I print to this, the colours are off, as if cyan values are too high. I will read more over the weekend, as I'm sure the answer as to how to calibrate my system is out there, but please do let me know if I'm barking up the wrong tree.

---

### Post by maruchan on 2007-09-21
You can use the HPLIP software for Linux to color-calibrate your printer, last I checked. You probably already have it installed.

Here's a page with information and test images for manually calibrating your printer, assuming you can access the controls in HPLIP: [http://www.normankoren.com/printer_calibration.html](http://www.normankoren.com/printer_calibration.html)

Might be a good idea to click the link near the top of the page to "go back a step" and calibrate your monitor first.

---

### Post by nikkkko on 2007-09-21
Thanks again. 

Nick

---

### Post by nikkkko on 2007-09-24
Still learning...

I think I've understood a bit about colour space and ICC profiles, but am not sure if Ubuntu uses any colour management system at os level. If it did, then I presume I could provide or create a profile for my printer that produced the 'right' colours.  I mostly use Inkscape at the moment, (still can't get Scribus to load .svg's or to save without crashing), and Inkscape apparently doesn't support colour management at the application level.

So, skipping colour management, I decided to use a couple of reference images provided on the link you gave me, (very useful by the way), get them printed out at my local print shop and do a comparison with the images printed by my printer. The result is that it appears I am printing a little too much cyan and not quite enough yellow, which corresponds with the proofing problems I am having with my designer colleague. The next step would therefore be to tweak my printer.

However, I have had absolutely no luck whatsoever playing with hplip.  Playing with brightness and gamma works, but altering hue and saturation levels does nothing, there are no gui instructions I can find and so far messages sent to the mailing list and left on the printing forum at the linux foundation have yielded nothing.

Just to cap things off, I discovered that Inkscape will only print 100% opacity, which means I am currently saving everything out to png before I can print. 

Closer, but still no cigar.

---

### Post by nikkkko on 2007-09-25
I can now transfer plain .svg files between Inkscape, Scribus and Illustrator. It turns out that the version of Scribus in the Ubuntu repositories - 1.3.4 - is on the 'ng' fork and, for me anyway, not at all stable.  Following the instructions on the Scribus web site, I added some new repositories and am now running 1.3.3.10cvs, which is very stable.  For some reason, imported text loses it's font information, but once this is re-established manually, text colour, size, orientation and so on comes over fine. 

I also had issues with colour management, (seeing the same thing as the Illustrator user), and printing transparencies.  For the transparencies, it turns out that postscript doesn't support it and I have to save as pdf 1.4 then print from there. 

Colour management problems are becoming clearer but are not yet resolved.  It appears that I cannot adjust the CMYK levels on the otherwise flawless HP Color Laserjet 2605 I am using, and my colours are coming out too cool.  I am trying to get colour management going in Scribus so that I don't have to tweak the printer, but for a novice it's a steep learning curve.

---

### Post by kayosiii on 2007-10-04
Inkscape supports converting image to a bitmap before printing rather than going straight to postscript You might want to experiment with this option.

Also you will be pleased to know that the linux printing system is being revamped to be based on PDF rather than postscript though I have no information as to when this work will be complete.

---

### Post by nikkkko on 2007-10-04
> Inkscape supports converting image to a bitmap before printing rather than going straight to postscript.

Do you mean manually export an image as a bitmap and print from that, or a print process whereby Inkscape internally creates a bitmap from which it prints?  If it's the latter, how do I do that?

> Also you will be pleased to know that the linux printing system is being revamped to be based on PDF rather than postscript

I'm not sure what that means...

---

### Post by kayosiii on 2007-10-05
In the print dialog (well the one I am looking at) it gives you two choices...

Print with postscript operators (default) or 
Print as bitmap...
The second option converts the image internally to a bitmap before printing.

To explain the second part - currently the linux print system converts files to Postscript as intermediate format hence the difficulty with object transparency using pdf as the intermediate format would aliviate this problem and then some.

---

### Post by nikkkko on 2007-10-05
> Print as bitmap...
I've been using Inkscape for about a year and I never noticed that. (I wonder what else I haven't noticed).

Concerning printing, I was unaware that all documents went through postscript before being sent to the printer. If documents do go through pdf first, that would be great as I currently have to save to pdf before printing as I'm using a postscript printer.

---

