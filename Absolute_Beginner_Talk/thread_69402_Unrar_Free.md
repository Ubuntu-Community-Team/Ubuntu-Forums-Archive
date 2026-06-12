---
title: "Unrar Free"
date: 2005-09-26
forum: Absolute Beginner Talk
---

### Post by toledo64fx on 2005-09-26
... why it cannot be easy with linux ????

unrar is installed and... i cant find a way to extract my .rar file 


damnnn

---

### Post by bored2k on 2005-09-26
Install unrar and rar.
Then right click on your file browser and click on extract here.
From a terminal, its just rar e file.rar

---

### Post by nucflash on 2005-09-26
Hello list!

I dont know if this is the right place to write this, but I didn't find anywhere better. Anyhow, here it is:

About the unrar, and unrar-non-free, I use unrar-non-free because rar and unrar provided by Ubuntu 5.04 (Hoary) doesn't handle well my multi-parted files. Yet, unrar-non-free got me in great trouble while I was trying to extract some files I packaged with Windows rar while I was moving my files from Windows to Ubuntu. The problem was that unrar-non-free 3.4.3.-1 I use does not handle the UTF8 filenames correctly, in result to be unable to create the extracted files in the ext3 filesystem I use and comes by the default installation of Ubuntu. The result was a crippled directory structure from the predictable one. After some weeks of searching I found that UnRar ([http://www.rarlab.com/rar_add.htm](http://www.rarlab.com/rar_add.htm)) gives unrar source to compile and send them back the binary for any distribution they don't have at the URL above. 

The compilation was pretty straight-forward by just typing in my terminal:
```
make -f makefile.unix
```
just after doing a change directory where the unrar sources where unpackaged. (Although, I didn't a ```
make install
``` to see what happens!)

I tested my Windows made rar archives, and everything behaved perfectly, and all UTF8 filenames were created as they should, the directory structure too! 

Hope that helps somebody!

Cheers,
Manos._

PS: while trying to resolve the problem I tried to change the Terminal encoding, the locale settings, as also to pipe the unrar-non-free output through iconv to convert explicitly the filenames in UTF8 (but the most I did was just to see the filenames displayed correctly) :) (stupid huh?)

---

### Post by nucflash on 2005-09-26
Hello list!

I dont know if this is the right place to write this, but I didn't find anywhere better. Anyhow, here it is:

About the unrar, and unrar-non-free, I use unrar-non-free because rar and unrar provided by Ubuntu 5.04 (Hoary) doesn't handle well my multi-parted files. Yet, unrar-non-free got me in great trouble while I was trying to extract some files I packaged with Windows rar while I was moving my files from Windows to Ubuntu. The problem was that unrar-non-free 3.4.3.-1 I use does not handle the UTF8 filenames correctly, in result to be unable to create the extracted files in the ext3 filesystem I use and comes by the default installation of Ubuntu. The result was a crippled directory structure from the predictable one. After some weeks of searching I found that UnRar ([http://www.rarlab.com/rar_add.htm]("http://www.rarlab.com/rar_add.htm")) gives unrar source to compile and send them back the binary for any distribution they don't have at the URL above. 

The compilation was pretty straight-forward by just typing in my terminal:
```
make -f makefile.unix
``` just after doing a change directory where the unrar sources where unpackaged. (Although, I didn't a ```
make install
``` to see what happens!)

I tested my Windows made rar archives, and everything behaved perfectly, and all UTF8 filenames were created as they should, the directory structure too! 

Hope that helps somebody!

Cheers,
Manos._

PS: while trying to resolve the problem I tried to change the Terminal encoding, the locale settings, as also to pipe the unrar-non-free output through iconv to convert explicitly the filenames in UTF8 (but the most I did was just to see the filenames displayed correctly) :) (stupid huh?)

---

