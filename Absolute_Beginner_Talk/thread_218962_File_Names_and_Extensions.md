---
title: "File Names and Extensions"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by noynac on 2006-07-19
In another thread, a forum member posted a link to the linuxcommand.org site. It has a lot of helpful information, although it did raise a few questions for me.

This site states:

*Linux has no concept of a "file extension" like legacy operating systems. You may name files any way you like. The contents/purpose of a file is determined by other means.*

This surprises me because when I create a file with OpenOffice Writer and look at it in Nautilus, the file name always shows the extension "odt." And when I create a screenshot in Ubuntu with the included utility, the extension "png" is always added. So, are these extensions simply added for informational purposes? And, if so, can I delete them if I wish? I personally would prefer not to see the extensions if they are superfluous. 

The linuxcommand.org site also states:

*While Linux supports long file names which may contain embedded spaces and punctuation characters, limit the punctuation characters to period, dash, and underscore. Most importantly, do not embed spaces in file names. If you want to represent spaces between words in a file name, use underscore characters. You will thank yourself later.*

I was also a bit surprised by this, as I have been creating file names with spaces and have yet encountered any problems. What issues can arise from using spaces in file names?

Thanks for the help.

---

### Post by avtolle on 2006-07-19
Have no answer to your second (rhetorical?) question. As to first, suspect that certain apps, such as open office, the app wants the extension to determine how to open the file later. In OO Writer, there are many options for file format on saving a doc, which leads me to the guess above. Anyone have any better ideas?

---

### Post by Brunellus on 2006-07-19
you can delete extensions without worry or penalty.  As a practical matter, however, having an extension gives you something to grep, so you can search for all files having a certain extension, for instance.  

having spaces in filenames is no big issue if you're willing to live with either passing the filename to the shell as a literal (enclose it in "double quotes").  Usually, you use a backslash to indicate to the shell that there is a space in a filename, so

/home/me/this\ is\ a\ really\ long\ name\ for\ a\ subdirectory/and\ this\ is\ how\ you\ use\ spaces\ in\ filenames

---

### Post by noynac on 2006-07-19
I deleted the extension from the Open Office document and the file type changed to "ZIP archive." I opened this file through Nautilus, and it loaded in the File Roller archive utility and was in fact an archive consisting of numerous files/folders. So, apparently, "odt" is an overlay extension of some sort that is actually needed. I deleted the extension from the PNG file, and the file type is still shown as "PNG image." 

So, it appears that the extension is important with some files but not with others. It's not clear to me how this is a better way of doing things. :confused:

---

### Post by Brunellus on 2006-07-19
didn't know that about .odt, but it makes sense:  the whole point of .odt is to act as a wrapper.  One 'file' is the text entered, another 'file' is its formatting information, and so forth.

---

### Post by aeto on 2006-07-19
i tried clearing away extensions before..ran them & they still worked. so it is true. but like the above statement, extensions are helpful..one of the cases being when u want to search for files ending with a particular extension. when i first got started with Linux, Ubuntu i had problems renaming, copying, cutting, pasting, moving files through the terminal. But now i know u just have to use the double quotes.

And for those like the OpenOffice files, i think its because OpenOffice reads & writes to many formats. In this case, the files are dependent on the extensions. But for stuff like images, music, etc they are not really dependent since they can be viewed, editted, listened to by many applications.

---

### Post by geco on 2006-07-19
> **noynac said:**
> In another thread, a forum member posted a link to the linuxcommand.org site. It has a lot of helpful information, although it did raise a few questions for me.

This site states:

*Linux has no concept of a "file extension" like legacy operating systems. You may name files any way you like. The contents/purpose of a file is determined by other means.*

This surprises me because when I create a file with OpenOffice Writer and look at it in Nautilus, the file name always shows the extension "odt." And when I create a screenshot in Ubuntu with the included utility, the extension "png" is always added. So, are these extensions simply added for informational purposes? And, if so, can I delete them if I wish? I personally would prefer not to see the extensions if they are superfluous. 


This means that if you rename your file without extension you just change it's name, not it's contents... so if you do
```

mv mydocument.odt mydocument

```
where "mydocument.odt" has been created with openoffice, you are still able to read and modify it with openoffice (or some similar porgram).
extensions are useful to you OS to know which program to use to open a certain file, that's all.
with mswindows you can "mask" file extensions, so they are there but you don't see them... I guess it is also possible in KDE and Gnome, on the contrary with a terminal you will always see the complete name of a file


> **noynac said:**
> 
The linuxcommand.org site also states:

*While Linux supports long file names which may contain embedded spaces and punctuation characters, limit the punctuation characters to period, dash, and underscore. Most importantly, do not embed spaces in file names. If you want to represent spaces between words in a file name, use underscore characters. You will thank yourself later.*

I was also a bit surprised by this, as I have been creating file names with spaces and have yet encountered any problems. What issues can arise from using spaces in file names?

Thanks for the help.

Special charaters as "?","space","!" etc are somehow deprecated in linux, you can use them but linux must know that they are part of a file name, so they are preceded by a backslash "\"
You can see that in a terminal.
"cd" to a directory where you have such files and type "ls": a "file with spaces" is viewed as "file\ with\ spaces", Konqueror and Nautilus mask this thing, but when you create files with spaces they automatically put the \ in.

byebye

---

### Post by shanepardue on 2006-07-19
don't we also need extensions for nautilus to know which program to open the file by default?

---

### Post by Christmas on 2006-07-19
As a matter of fact I encountered problems with the file extensions. I think it was either LinuxCommand or TuxFiles.org where I read the same thing about file extensions as you, but without the extensions I had problems compiling C source files with gcc. Example:
```
christmas@kubuntu:~$ gcc hel
hel: file not recognized: File format not recognized
collect2: ld returned 1 exit status
christmas@kubuntu:~$
```
And the same file but with extension:
```
christmas@kubuntu:~$ gcc hel.c
christmas@kubuntu:~$ ./a.out
Viva Pink Floyd!
christmas@kubuntu:~$
```
The same with other applications. I guess it's good to use file extensions with every file you have, just like on Windows.

---

### Post by Oler1s on 2006-07-19
> **noynac said:**
> I deleted the extension from the Open Office document and the file type changed to "ZIP archive." I opened this file through Nautilus, and it loaded in the File Roller archive utility and was in fact an archive consisting of numerous files/folders. So, apparently, "odt" is an overlay extension of some sort that is actually needed. I deleted the extension from the PNG file, and the file type is still shown as "PNG image." 

About the odt file. It *is* a zip file. It contains formatting data as well as the text you actually typed. All that data is stored in various xml files, which are then zipped. Neat isn't it? So OpenOffice is effectively unzipping the file when you open it.

---

### Post by noynac on 2006-07-19
Thanks everyone. I now understand the space-in-filename issue. Just to be certain, I created a text file with the name: this is a file. I then went to a terminal window and typed ls. The terminal showed a text file with the name: this is a file. I then typed the command...

cp this is a file test1

...and (as expected) it didn't work. I then typed the command...

cp "this is a file" test1

... and I have a new file with the name test1. I then typed...

cp this\ is\ a\ file test2

...and I have a new file with the name test2. 

Pretty neat!

I still don't completely understand the extension issue. If I delete the ODT extension from an open office file I get a ZIP file, and if I delete the HTML extension from an HTML file I get a text file. However, if I remove the extensions from other files--such as PNG and text files--I still have PNG and text files. This is not important, as I have no reason to change extensions, but it just seems a bit messy.

Thanks again.

---

