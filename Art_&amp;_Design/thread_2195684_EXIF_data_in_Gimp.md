---
title: "EXIF data in Gimp"
date: 2013-12-25
forum: Art &amp; Design
---

### Post by michael-piziak on 2013-12-25
I went to this page and downloaded the file, put it on my desktop, then typed the instructions into Terminal, but Terminal couldn't find the file

[http://registry.gimp.org/node/8839](http://registry.gimp.org/node/8839)

---

### Post by steeldriver on 2013-12-25
Did you remember to **c**hange to the the Desktop **d**irectory in the terminal first?

```
**cd** ~/Desktop
```

---

### Post by michael-piziak on 2013-12-26
I tried "cd ~/desktop" and then follow the steps at th webpage [http://registry.gimp.org/node/8839](http://registry.gimp.org/node/8839)

No luck yet.

Maybe I can find an exif reader in the software center

---

### Post by steeldriver on 2013-12-26
Please post the EXACT commands you are typing and the EXACT error messages (no paraphrasing) - you can copy from the terminal by selecting using the mouse and then pressing Ctrl-**Shift**-C

Linux is case sensitive so cd ~/desktop is NOT the same as cd ~/Desktop

---

### Post by michael-piziak on 2013-12-26
I moved exif-browser.tar.gz from download folder to the desktop then typed this in terminal and this is what happens:

michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ cd ~/Desktop
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~/Desktop$ gunzip exif-browser.tar.gz
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~/Desktop$ tar xcf exif-browser.tar
tar: You may not specify more than one `-Acdtrux' or `--test-label' option
Try `tar --help' or `tar --usage' for more information.
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~/Desktop$

---

### Post by steeldriver on 2013-12-26
Try 

```
tar x**v**f exif-browser.tar
```

or just

```
tar xf exif-browser.tar
```

if you don't want a **v**erbose listing of the archive contents ('c' is for **c**reating archives, not e**x**tracting them - the error message is telling you that you can't create and extract an archive at the same time)

FYI modern versions of tar are smart enough to gunzip automatically so you could have skipped a step and just done

```
tar xvf exif-browser.tar.gz
```

---

### Post by ofnuts on 2013-12-27
Most image browsers will display EXIFs. Among the ones I use (KDE desktop): Gwenview and Digikam, but I am fairly sure that their Gnome counterparts will also do it. For the command line, you can also use ExifTool. Using Gimp just to see EXIFs if a bit of overkill.

---

### Post by ssam on 2013-12-30
There is lots of metadata work going on in GIMP at the moment.
[https://mail.gnome.org/archives/gimp-user-list/2013-December/msg00225.html](https://mail.gnome.org/archives/gimp-user-list/2013-December/msg00225.html)

---

### Post by coldraven on 2013-12-30
Why not just double click the downloaded file? The archive manager will open, then click "Extract".
That must be quicker than typing a command, surely?

---

### Post by prokodine on 2014-01-08
Look for your file in either ~/Desktop or ~/Downloads.

The command is 'tar zxf your_file.tar.gz'.

GIMP is really not the tool you want for just viewing metadata. Aforementioned digiKam and Gwenview are the kind of tools that would work better. In GNOME and that Ubuntu thing you can also use EoG, or Eye of GNOME: press Alt+Enter to view properties.

---

### Post by alan-pater on 2014-04-08
> **michael-piziak said:**
> Maybe I can find an exif reader in the software centerThe default Image Viewer (aka EOG) has complete exif/iptc/xmp viewing capabilities. Open an image, right click it and go to properties.

---

