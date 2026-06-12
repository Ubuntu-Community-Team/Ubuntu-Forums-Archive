---
title: "printing to pdf from command line"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by macdo on 2007-05-06
I have 119 MS Word documents to convert to pdf. 

I can't work out what command to use at the command line (obviously, I'm trying to write a script...)
I have managed to get things to print on a printer using this command ```
ooffice -pt printername file.doc
```
OpenOffice doesn't print to pdf, though, it exports. Abiword will do it (it uses wvWare), but it really munges the formating - not so good. 

A solution that gives me a PostScript file is cool too. 

Because there are so many docs, I really need them to keep the original file names.


Any ideas?

cheers!

---

### Post by Skrynesaver on 2007-05-06
catdoc will give you TeX output, this can be "compiled" to DVI then dvitops .
thus
```

for i in $(find ~/ -name *.doc);do
   catdoc -f tex $i >$i.tex
   tex $i.tex
   dvi2ps $i.dvi $i.ps
   rm $i.tex $i.dvi
done

```

---

### Post by klytu on 2007-05-06
> **macdo said:**
> I have 119 MS Word documents to convert to pdf. 

I can't work out what command to use at the command line (obviously, I'm trying to write a script...)
I have managed to get things to print on a printer using this command ```
ooffice -pt printername file.doc
```
OpenOffice doesn't print to pdf, though, it exports. Abiword will do it (it uses wvWare), but it really munges the formating - not so good. 

A solution that gives me a PostScript file is cool too. 

Because there are so many docs, I really need them to keep the original file names.


Any ideas?

cheers!

You can probably do this by 
1. Installing the cups-pdf package and setting up a virtual pdf printer:   > 1. Install the cups-pdf package (I used version 2.2.0-1)
   2. Go to System -> Administration -> Printing
   3. Doubleclick "New Pinter"
   4. Notice that there is no mention of a CUPS PDF printer
   5. Open a terminal and tpe "sudo nautilus" and then your password
   6. Go to Filesystem -> usr -> lib -> cups -> backend
   7. Rightclick "cups-pdf" and select Properties
   8. Go to the Permissions tab and click the "Set user ID" special flag
   9. Again try to add a new printer
  10. There is now a "PDF Printer" detected, select it
  11. Select the Generic, Postscript Color Printer (Rev 3b)
  12. Give it a name, like PDF Printer
  13. Right click on the newly created printer, and select Properties
  14. Click "Print a Test Page"
  15. The file should be in your Home folder, under the PDF folder Copied from [[COLOR="Red"]**_this thread_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=188860")

2. Making  that printer the default printer 

Now the command ```
ooffice -p filename
```

creates the file filename.pdf in the PDF folder in your home directory.  You could then set up your script based on that command. I tried this on a couple of individual files, all PDFs generated as expected, but I kept getting the warning > ** (process:1845): WARNING **: Unknown error forking main binary / abnormal early exit .... I don't know if this would be a serious problem for a batch script, but it's probably worth a try.

---

### Post by macdo on 2007-05-06
Thanks! 

I found a different way, though:

First I installed a virtual pdf printer via cups, using instructions here: [http://cuasan.wordpress.com/2007/03/01/print-anything-to-a-pdf-document-in-gnulinux/](http://cuasan.wordpress.com/2007/03/01/print-anything-to-a-pdf-document-in-gnulinux/)


Then the script I wrote: ```
	for file in $*

	do

		ooffice -nologo -p $file 
		mv ~/PDF/firstline.pdf ~/${file/.doc/}.pdf


	done
	#we now exit the program

	exit 0
```
I don't currently have any real printer on my system, so the virtual printer (called virtualpdf) was the default. If that hadn't been the case, I could I think have used the command ```
ooffice -pt virtualpdf $file
```
The mv just renames the file and puts it in the right place. All the files had an identical first line, and the virtual PDF printer uses that to create the filename. So without the mv line, yu only get one file - the last one.

When I ran this, a couple of files were skipped (119 originals; 115 results). I'm not sure why. Also, there were a couple of rtf files in the original folder, and ooffice printed them with correct file names, so the mv command didn't work. That wasn't really a big problem, I just had to copy them over from ~/PDF/ afterwards.

---

### Post by macdo on 2007-05-06
Klytu: we seem to have found the same solution. I can confirm that the errors aren't a problem - they just make it longer to run :-) It does look bad though!
```

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(process:13273): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:13273): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:13273): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:13273): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:13273): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:13273): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:13273): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:13273): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:13273): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:13273): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:13273): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:13273): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:13273): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:13273): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:13273): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:13273): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:13273): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:13273): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:13273): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:13273): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:13273): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:13273): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:13273): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:13273): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:13273): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:13273): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:13273): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:13273): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:13273): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:13273): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:13273): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:13273): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

** (process:13257): WARNING **: Unknown error forking main binary / abnormal early exit ...

```

---

