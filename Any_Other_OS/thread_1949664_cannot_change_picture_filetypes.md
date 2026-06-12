---
title: "cannot change picture filetypes"
date: 2012-03-30
forum: Any Other OS
---

### Post by HappyLinux on 2012-03-30
I've got a problem with saving pictures through several programs, minus one.

To get it out of the way, I can save pictures off websites through Firefox, Opera and Chrome.

The file saving that doesn't work is through dedicated graphics programs. Here's a method for example; Create a screen grab which only saves in a .png file type and save to wherever. Open the .png file in either Gimp or Gnome Image Viewer and try to save as a .jpg.

Image Viewer will only save as the file type as the original. Gimp only saves as .xcf

Is there something I'm doing wrong?

---

### Post by papibe on 2012-03-30
Hi HappyLinux.

Gimp's option to save the current image in other formats is usually collapsed. To open that functionality when saving a picture click on the bottom of the screen where it says:
```
+ Select File Type (By Extension)
```
A list will open, and will let you choose the formats (including the typical gif, jpep, png, etc).

Hope that helps, and tell us how it goes.
Regards.

---

### Post by HappyLinux on 2012-03-31
I've already tried that through Gimp and Image Viewer. I select the file type I want, and the program saves as the type it wants.

---

### Post by gordintoronto on 2012-03-31
Did you change the file type in the file name in the save-as window?

For example, I edit sample.png, I change the name to sample.jpg

---

### Post by HappyLinux on 2012-03-31
Yes, they do one of several things. either ask to replace the original, which means that it's trying to as the original file type, crop up with and error message saying that the file is unrecognised, or just revert to what file type that it wants to, which for Gimp is the .xcf.

---

### Post by qyot27 on 2012-03-31
Install ImageMagick

In Terminal:
```
convert input.png output.jpg
```

That'd be the simplest way if the other programs aren't working.

---

### Post by HappyLinux on 2012-04-01
Using the terminal would be too much hassle, and would the file size change as the image has been modified for the change in file type, rather than just changing the extension?

---

### Post by qyot27 on 2012-04-01
> **HappyLinux said:**
> Using the terminal would be too much hassle, and would the file size change as the image has been modified for the change in file type, rather than just changing the extension?
ImageMagick's convert command converts the format to whatever you tell it to, and beyond that depends on IM's defaults for that format or the compression level the user selects (there are options to tweak compression levels, but the defaults are fine, IMO).  Depending on how good the PNG compression was when saved by the screenshot program, you'd even see a filesize difference if you told it to save as another PNG.

Granted, I'm under Windows right now, but since I can use ImageMagick on here too, a demonstration.  avatar_24_1333105690.png is the original, avanew.png is the file outputted by ImageMagick (I simply did a *convert avatar_24_1333105690.png avanew.png*).  I've omitted the permissions data from the output for privacy reasons, but the filesize is still there.
```
ls -l *.png
42558 Apr  1 03:33 avatar_24_1333105690.png
37248 Apr  1 17:23 avanew.png
```
avanew.png is 5.31 KB smaller.  I also did a *convert avatar_24_1333105690.png avanew.jpg* and the result of that is:
```
7561 Apr  1 17:25 avanew.jpg
```
34.997 KBs smaller than the original.

---

### Post by HappyLinux on 2012-04-02
I already have ImageMagick installed according to Software Manager, but I can't find it in my menu system.

---

### Post by qyot27 on 2012-04-03
> **HappyLinux said:**
> I already have ImageMagick installed according to Software Manager, but I can't find it in my menu system.
That's because you use it through the Terminal.  It's a collection of commands - the one for convert is 'convert'.

---

### Post by HappyLinux on 2012-04-04
> **gordintoronto said:**
> Did you change the file type in the file name in the save-as window?

For example, I edit sample.png, I change the name to sample.jpg

I've managed to get this option to work with a bit of fiddling. For example, in Gimp, I select the file type in the drop-down menu, before manually changing the file extension in the file-name box. However, Gimp recognise 3 different file extension names for the same type. Gimp has .jpg, .jpeg, and .jpe for the image type that I wanted.

So, if it won't save as .jpg, then I try the other 2. However, it seems to be playing the guessing game. It doesn't stick to just 1 of the extensions. So far I've managed to save as 2 of the extensions; .jpeg and .jpe.

---

