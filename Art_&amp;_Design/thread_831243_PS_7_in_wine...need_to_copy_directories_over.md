---
title: "PS 7 in wine...need to copy directories over?"
date: 2008-06-16
forum: Art &amp; Design
---

### Post by calicat on 2008-06-16
I posted this in general and then found this forum...  If a mod could delete the other one I sure would appreciate it...thanks!

Im having a problem with PS 7 running in wine...I get a error message when I try to enter text. I searched the internet and found this as a fix:
[I]
I had an error every time I tried to enter text in PhotoShop that said default font not found and I could never enter text in PhotoShop. Well, I copied over the whole directory 'C:\WINDOWS\Fonts' to '/.wine/drive_c/windows/fonts' and now I can use text in PhotoShop 7. I just thought that I would post this incase anyone else had this problem too. Oh, and the 'C:\WINDOWS\Fonts' directory is my XP install on the other partition in case that was not clear.[/I]

But I don't really know how to copy over files from one directory to another and dont want to mess anything up.. Could someone give me simple, step-by-step instructions??

Thanks so much!

---

### Post by Ralphie on 2008-06-16
If you have a windows partition, those fonts should be located on your main HDD, ( usually c: )
So you should be able to find the fonts folder under: 
```
C:\Windows\Fonts
```
or it might be labeled as:
```
C:\Winxp\Fonts
```

Copy the contents of the Fonts folder to:
```
~/.wine/c_drive/window/fonts
```

the .wine folder is a hidden directory, you can unhide hidden folders in nautilus, or just copy and paste what i wrote up above in your nautilus address bar, which will take you to the fonts folder.

If you do not have access to your windows partition from ubuntu for some reason, copy the files over with a flash drive.

There is little room for error, believe me!

*edit*
It might ask to overwrite some fonts, allow it to overwrite them.

---

### Post by calicat on 2008-06-16
*If you do not have access to your windows partition from ubuntu for some reason, copy the files over with a flash drive.*

I can't find c drive except under the wine program (where the fonts folder is empty) and Im not sure what you mean by copy it over with a flash drive...?

---

### Post by Ralphie on 2008-06-16
Do you own windows?
if so, do you have it installed anywhere?
maybe a separate computer, or on a different hard drive?

You need to go to the actual Windows font directory, and copy those fonts.

If you have a flash drive, or a thumb drive, you can copy them onto there, and then from there, into wine's font directory.

---

### Post by calicat on 2008-06-16
I did...until I installed Ubuntu. I installed wrong and lost everything from Windows and now all I have is this

---

### Post by Ralphie on 2008-06-17
Well that would be an issue, as now you do not have access to the the native windows fonts.

If there is another computer that you can take them from, I'd say do that with a thumb drive or something like it. 

Optionally you could install windows on a new partition and get them that way. 

i'm not sure about this, but maybe they are somewhere on the windows install disk itself? you'd have to look.

This is a list of all standard windows fonts. 
[http://www.kayskreations.net/fonts/fonttb.html](http://www.kayskreations.net/fonts/fonttb.html)
(maybe look them up on google for download if you cant seem to get them off your disk, although i'm not sure its legal, but who knows, if you own windows it might be alright)??

---

