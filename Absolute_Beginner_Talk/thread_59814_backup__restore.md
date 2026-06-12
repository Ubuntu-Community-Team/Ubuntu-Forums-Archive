---
title: "backup / restore"
date: 2005-08-25
forum: Absolute Beginner Talk
---

### Post by soonindallas on 2005-08-25
hi all,

Today I got the go-ahead to return my laptop for repair of a display problem under warranty.  There's a chance I won't get the same machine back, and in any case I don't want to leave all my work on it, so I'm considering wiping the HD before I send it back.

I will reinstall Ubuntu when it or the replacement comes back.  This thread [http://ubuntuforums.org/showthread.php?t=50736](http://ubuntuforums.org/showthread.php?t=50736) informed me on how to backup Evolution, I can store this in a non-windows-friendly format.  But there are other files that I will want to work on in the interim (yay for the guys at OOo for the windows version).

I will backup all this information over the network onto a windows box.

Question: what compression utility should I use to compress the files I might want to have access to before I get the Ubuntu laptop back ?  One that produces a format that WinZip can get into ?

I guess I'll be backing up my home folder, Desktop &c.  What else might I need, you all who have experience in this kind of operation ?

thanks for your help.

Peter

---

### Post by KingBahamut on 2005-08-25
Soon, you can tar and gzip em, and still open them in windows with winzip. 

Dump all your files into a folder, 
at command line do a 
cd to the directory with all your stuff in it

tar -cf nameofarchive.tar * 
(This will archive all files int he directory to your named file)

Then

gzip -9 nameofarchive.tar 

this will use best compression to gzip your tar archive , and create a 

nameofarchive.tar.gz 

there you have it.

---

