---
title: "merge tiff???"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by towsonu2003 on 2006-04-05
how do you merge tiff files into one? I know this is dumb, but I just couldn't find it on synaptic or in google?? maybe convert tiffs to pdf (with what??) and than merge them using pdftk? 

any pointers would be appreciated :) thanks.

---

### Post by rmjokers on 2006-04-05
I would suggest taking a look at the netpbm package.  It has lots of command line utilities for image manipulation.  You can, for instance, convert .tiff files to .pnm format, merge them, and then convert them back to .tiff or some other format.  If you want a GUI, the Gimp will probably work.

---

### Post by towsonu2003 on 2006-04-05
[QUOTE=rmjokers]I would suggest taking a look at the netpbm package.  It has lots of command line utilities for image manipulation.  You can, for instance, convert .tiff files to .pnm format, merge them, and then convert them back to .tiff or some other format.  If you want a GUI, the Gimp will probably work.[/QUOTE]
I ended up using gimp to convert tif to ps, ps2pdf to convert ps to pdf, pdftk to merge all 54 pdfs... was long and tiring. having a deadline didn't help ;)

thanks for the suggestions. gimp helped very much.

---

### Post by phetre on 2006-04-10
[QUOTE=towsonu2003]how do you merge tiff files into one?[/QUOTE]
Hi, sorry I didn't see this until now.  I had the same question a while ago, and a lucky search brought me to a tool called **tiffcp**.  It's included in the **libtiff-tools** package.  Use it from the command line as follows:
tiffcp input1.tiff input2.tiff [etc.] output.tiff
This will create a multipage .tiff file from any inputs you specify.  Wildcards are fine.

I even wrote a short, noobish script to create a PDF automatically from a directory full of TIFFs:
```
#!/bin/bash
# Create a PDF file from all the .tiff files in the current directory.
# The argument provides the name of the output file (with .pdf appended).
tiffcp *.tiff "${1}.tiff"
tiff2pdf "${1}.tiff" > "${1}.pdf"
echo "Created ${1}.pdf"
rm "${1}.tiff"
echo "Removed temporary file ${1}.tiff"
```
Hope this comes in handy!  It sure would have helped me a few months ago.  :)

---

### Post by towsonu2003 on 2006-04-10
[QUOTE=phetre]Hi, sorry I didn't see this until now.  I had the same question a while ago, and a lucky search brought me to a tool called **tiffcp**.  It's included in the **libtiff-tools** package.  Use it from the command line as follows:
tiffcp input1.tiff input2.tiff [etc.] output.tiff
This will create a multipage .tiff file from any inputs you specify.  Wildcards are fine.

I even wrote a short, noobish script to create a PDF automatically from a directory full of TIFFs:
```
#!/bin/bash
# Create a PDF file from all the .tiff files in the current directory.
# The argument provides the name of the output file (with .pdf appended).
tiffcp *.tiff "${1}.tiff"
tiff2pdf "${1}.tiff" > "${1}.pdf"
echo "Created ${1}.pdf"
rm "${1}.tiff"
echo "Removed temporary file ${1}.tiff"
```
Hope this comes in handy!  It sure would have helped me a few months ago.  :)[/QUOTE]
](*,) ](*,) ](*,) ](*,) 

Aaaaaargh... It took me 30 minutes to do this and I had that package installed.. ](*,) ](*,) ](*,) 

Thanks so much though. This will be useful in the future.

---

