---
title: "Save Options In Gimp are a real time waster"
date: 2011-09-24
forum: Art &amp; Design
---

### Post by PayPaul on 2011-09-24
When you wish to save a file in the GIMP with a particular name and type the case is that you need to choose both the file type below and the extension of the filename above. If I save an image with the .xcf extension first and then go back and try to save the file with the same name as the .xcf file that I just saved and remove the .xcf extension from the filename above and change the type below in the "save as file type" drop down to jpeg, the dialog box reverts the file to the extension of .xcf automatically and then I get asked if I want change the file. So I find I have to change the file extension to .jpg in the filename that I'm saving as well in order to save that same file as a jpeg. 

Not only is the file naming and saving functions of GIMP absolutely ridiculous but here's another bad example in file naming. I do an additional edit on a file, save as a jpeg and change both the name and the file extension to .jpg on top and save it. After that I still have the file I was working on open. In the title bar of that file, with all the layers visible to my eyes, the title bar on the image box says *filename.jpg*. Does this make any sense at all? No it doesn't and is quite confusing. It shouldn't be. Now what do I do? if I click control-s to save any further changes I'm going to get a dialog box telling me to flatten a jpg or replace the previously changed jpeg file that contained my prior editing. Now I want to just save the file as I thought it was, a gimp image file.

Is there any way to stop the program from automatically adding an extension to a filename even when I remove it? It's most illogical if I choose a file type and then have the program change it without any action from me. It's a serious time waster.
](*,)

---

### Post by WasMeHere on 2011-09-24
There are two options,

a. Edit the file-name-line at the top of the 'Save' window: In order to select a new file-type, simple change the file extension
(eg. png-->xcf)

b. Enter the menu 'Choose file type' and select the file-type you want and save it (this way the extension will be changed automatically). See the attached screen-dump.

I think that you are trying to use the menu that only filters what file-type that is shown (All or png, jpg, xcf ...) in the current directory.

This works for me and I hope it will help you.

Have fun
Olle

---

### Post by PayPaul on 2011-09-24
My screen looks different than yours. What's the best way to do a screen dump so I can illustrate what happens?

---

### Post by WasMeHere on 2011-09-24
> **PayPaul said:**
> My screen looks different than yours. What's the best way to do a screen dump so I can illustrate what happens?
Use the keys Alt + PrtScrn (press both at the same time) to dump the window!

Is there other differences than the language? I use Lucid Lynx with Gimp version 2.6.8.

---

### Post by SecretCode on 2011-09-24
I'm not sure if I've fully understood what you would like to happen ...

To save as a specific type, use the "select filetype" dropdown (marked as "1 choose" in Olle Wiklund's attachment). If you leave this as "by extension", then you type .jpg in the Name: box at the top. The other dropdown on the right doesn't control the save type or name.

If you have a full GIMP image (multiple layers etc) and you want to save a jpg but keep working with the layers and so on, use "Save a copy". You'll get the 'flatten image' dialogue but the open image will remain a .xcf.

If you only ever want it to be a jpg and you don't need the layers, you could flatten it *before* saving. Otherwise GIMP treats the in-memory file as a full image with all GIMP features, like layers, *even though* the filetype says .jpg. Perhaps you would prefer this not to be allowed?

---

### Post by ofnuts on 2011-09-24
> **SecretCode said:**
> I'm not sure if I've fully understood what you would like to happen ...

To save as a specific type, use the "select filetype" dropdown (marked as "1 choose" in Olle Wiklund's attachment). If you leave this as "by extension", then you type .jpg in the Name: box at the top. The other dropdown on the right doesn't control the save type or name.

If you have a full GIMP image (multiple layers etc) and you want to save a jpg but keep working with the layers and so on, use "Save a copy". You'll get the 'flatten image' dialogue but the open image will remain a .xcf.

If you only ever want it to be a jpg and you don't need the layers, you could flatten it *before* saving. Otherwise GIMP treats the in-memory file as a full image with all GIMP features, like layers, *even though* the filetype says .jpg. Perhaps you would prefer this not to be allowed?The coming version of Gimp will have "Save" always save to XCF. Other formats will be obtained by "Export".

---

### Post by WasMeHere on 2011-09-24
> **ofnuts said:**
> The coming version of Gimp will have "Save" always save to XCF. Other formats will be obtained by "Export".

Well, that makes sense, because it decreases the risk of destroying the original file. But would it make saving files slower for me? I often save a file using 'ctrl + s' overwriting a jpeg file to save space. I backup my computer fairly well, so I think I don't need several versions of edited pictures in my photo directory (unless I do some art-work or change the resolution of the picture).

---

### Post by ofnuts on 2011-09-25
> **Olle Wiklund said:**
> Well, that makes sense, because it decreases the risk of destroying the original file. But would it make saving files slower for me? I often save a file using 'ctrl + s' overwriting a jpeg file to save space. I backup my computer fairly well, so I think I don't need several versions of edited pictures in my photo directory (unless I do some art-work or change the resolution of the picture).
Actually it reduces the risk of losing your work. If you make a complicated images with layers, paths, and selections and save it as JPEG, currently the image is marked "saved" and you can quit Gimp without confirmation. And if you do, you lose your work (layers, paths, selection...).

---

### Post by PayPaul on 2011-09-25
> **ofnuts said:**
> The coming version of Gimp will have "Save" always save to XCF. Other formats will be obtained by "Export".


I remember years ago using graphics programs that would use that phrase "export" when saving files to any other type but the native format. Rather old fashioned but truthful in a way. It would clarify the file saving process for sure if that was the default operation.

---

