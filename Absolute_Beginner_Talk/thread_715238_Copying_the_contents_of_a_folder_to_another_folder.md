---
title: "Copying the contents of a folder to another folder"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by SIXAXIS on 2008-03-04
I have a folder with about 100 files for fonts in it. I want to copy all the files to the font folder. How can I take just the contents to the fonts folder.

eg.

My Font Folder Contents:
blah blah.ttf
blah blah.pfb
whatever else

I want to copy all the files to the Fonts folder.

Right now I'm using the cp -r "Original Folder" "Destination Folder".
How can I make it like cp "All Files in the Original Folder" "Destination Folder"

---

### Post by Crooksey on 2008-03-04
```

$ sudo cp -r /path/to/folder/* /path/to/new/folder/ 
```

---

### Post by SIXAXIS on 2008-03-04
Thanks for the help Crooksey. But I've changed my mind now, I need to learn to use Deforma because I want to install my fonts. Do you know how to use Deforma? I need these fonts installed.

---

