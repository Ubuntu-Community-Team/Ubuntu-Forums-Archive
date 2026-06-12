---
title: "How to find which package provides a file"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by flabbah on 2005-12-29
Hi,
How can I find out which package provides a special file that I need ? The package is _NOT_ already installed on my system.

For example, I'm trying to compile MrScheme v300 from source, and the compilation blows up because it can't find:

/usr/include/X11/bitmaps/gray

I installed all the X-related development libraries I know, but I must be missing something.

So I need to figure out which package provides this, and then install it. How can I do that ?

Thanks

---

### Post by narcolept on 2005-12-29
```
 sudo apt-cache search <string> 
```

will generally provide you with the information you're looking for, if it's available form any packages in the respositories you're using.

---

### Post by az on 2005-12-29
packages.ubuntu.com

Under the first search box there is a "search contents of packages" box.

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=%2Fusr%2Finclude%2FX11%2Fbitmaps%2Fgray&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=%2Fusr%2Finclude%2FX11%2Fbitmaps%2Fgray&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386)

"You have searched for usr/include/X11/bitmaps/gray in breezy, architecture i386.
Found 1 matching files/directories, displaying files/directories 1 to 1.

FILE                                                       PACKAGE

usr/include/X11/bitmaps/gray				    x11/xbitmaps
"

---

### Post by flabbah on 2005-12-30
Excellent - xbitmaps was the culprit.

thank you very much. 

Do any of the command line tools like dpkg-* have this ability? How about while being disconnected from the network?

Thanks again

---

