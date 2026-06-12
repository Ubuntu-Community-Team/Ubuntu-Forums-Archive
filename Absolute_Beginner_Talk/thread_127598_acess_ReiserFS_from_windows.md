---
title: "acess ReiserFS from windows"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by Hotchilli on 2006-02-09
I have software that can access Ext2 file system but cannot find software to acess
the ReiserFS file system from windows.

hc


:cool:

---

### Post by TrendyDark on 2006-02-09
I don't believe the ReiserFS is supported yet. I suggest using ext3, more reliable, but a small decrease in speed performance.

---

### Post by Hotchilli on 2006-02-09
i was wondering how change to ext2 or 3 does it a reformat and new install?

hc
;)

---

### Post by JAwuku on 2006-02-09
Before you reformat :eek: , try a utility called Yareg. It allows you to access ReiserFS files and directories from Windows 2000/XP.

Check out [http://yareg.akucom.de/]("http://yareg.akucom.de/")

You'll need to download the Microsoft .NET framework for it to work (see the bottom of the link page for the download) 23MB

and a program called *rfstool* [http://p-nand-q.com/download/rfstool.html]("http://p-nand-q.com/download/rfstool.html")

Put the rfstool program in the same directory as Yareg.exe.

After installation, you can access ReiserFS files in Windows, and drag&drop files.

---

### Post by lha on 2006-02-10
[Rfsd]("http://rfsd.sourceforge.net/") provides an experimental filesystem driver for reiserfs.

---

