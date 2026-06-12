---
title: "unzipping and untarring"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by lwalper on 2007-03-11
I downloaded a copy of WP8 (I'm a longtime WP fan -- best word processor ever!--even if a couple of years old). I unzipped the file to a folder on the desktop and everything looks intact. It came with these instructions . . .

How do I (1) "untar" the files, and (2) run the Runme script in a /bin/sh environment?

I tried double clicking the file which opened a window asking what to do with the file, Run, Run in terminal, etc. I first selected "Run" -- which it did not. The tried "Run in terminal," which ran the program but did not install the software -- couldn't find folders and such like stuff.

*****************
Corel WordPerfect FTP Download Instructions

This file has been written to document the steps required to install
the FTP downloaded version of Corel WordPerfect.

1) Download the file(s) from the web into an empty directory.
2) Unzip each downloaded file(s).
3) Untar each downloaded file(s) (tar xf <file>).
4) Run the newly created Runme script.

Note: In order for the GUI installation to work, your display environment
must be set correctly.

The Runme script will launch the Corel WordPerfect installation for you.
At this point, simply answer the questions you are prompted for during
the install.

Note: The Runme script must operate in the /bin/sh environment.
If you encounter problems, start the Runme script using "sh Runme".

We hope you enjoy using Corel WordPerfect for Unix.  If this is a demo
version, and you like it, then buy it.

---

### Post by diatribe on 2007-03-11
well, you would type

tar zxvf tar_file.tar.gz

then all that should be required is ./Runme

---

### Post by Bachstelze on 2007-03-11
For zip files :

```
unzip filename.zip
```

(if you get "command not found", do an *apt-get install unzip*)


For .tar files :

```
tar xvf filename.tar
```


For .tar.gz or .tgz files :

[cod&#8364;]tar xzvf filename.tgz[/code]


For .tar.bz2, .tbz or .tbz2 files :

```
tar xjvf filename.tbz
```

---

### Post by lwalper on 2007-03-11
Type where? In the terminal? (is that equivalent to the DOS prompt?)

---

### Post by diatribe on 2007-03-11
yes in the terminal and yes it is the quivalent of the DOS prompt

---

### Post by lwalper on 2007-03-11
OK, so my prompt displays

leslie@leslie-desktop:~s

at the prompt I typed--

tar xvf wp8/b_ins00.tar

assuming that wp8 would direct to the folder on my desktop. No go.

---

### Post by diatribe on 2007-03-11
if the wp8 folder is on your desktop, type

tar xvf ~/Desktop/wp8/b_ins00.tar

if that doesnt work post error messages

---

### Post by lwalper on 2007-03-11
Old option 'f' requires an argument

---

### Post by diatribe on 2007-03-11
intriguing.  
sudo apt-get install file-roller
use file-roller to do it for you ;) it's akin to winzip

---

### Post by lwalper on 2007-03-11
OK. I'll give it a try. Where do I get file roller? I don't see it in the list of apps to install.

---

### Post by diatribe on 2007-03-11
just go to a terminal and type 

sudo apt-get install file-roller

or you could go to synaptic and install it through there

---

### Post by lwalper on 2007-03-11
OK. Got file-roller. It runs great, installed, no problem. But now I'm back where I was -- with a folder of files in the wp8 folder on the desktop. In the file browser I see that the internal folders are still listed as tar archives.

---

### Post by maniacmusician on 2007-03-14
To be honest, I tried to resist, but I have to say this; There really are better alternatives than WP nowadays. Have you at least tried some alternatives? Two good ones for word processing are OpenOffice (complex, full-featured) and AbiWord (simple, not as many features). Both can be installed through the terminal or through Synaptic.

If you've tried those and still don't like them, you could provide a link to the file and I or someone else could figure out how to install it and help you out. But honestly, please at least try some alternatives :)

---

