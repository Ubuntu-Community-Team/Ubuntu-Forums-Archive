---
title: "Copying a file from Linux to Windows (invalid filename)"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by svk on 2008-03-26
Hello,

I dual boot Linux and Windows Vista.  I'm currently on Windows and I'm trying to copy some files I have stored on the Linux partition.  I can view the files using [fs-driver]("http://www.fs-driver.org").  However, because Linux is far less restrictive on filenames, I'm having trouble copying files that contain invalid characters in their filenames.  There's seemingly nothing I can do (move, rename, or copy) unless I log back into Linux and rename the files myself from there before being able to copy them.

Is there a way to copy a file stored on an ext3 Linux partition whose filename Windows considers invalid?  I don't mind changing the destination filename.  I *do* mind having to shut down Windows and boot into Linux, renaming, then shutting down and booting back into Windows every time I need to copy such a file.

Thanks in advance for any help.

---

### Post by keratos on 2008-03-26
> **svk said:**
> Hello,

I dual boot Linux and Windows Vista.  I'm currently on Windows and I'm trying to copy some files I have stored on the Linux partition.  I can view the files using [fs-driver]("http://www.fs-driver.org").  However, because Linux is far less restrictive on filenames, I'm having trouble copying files that contain invalid characters in their filenames.  There's seemingly nothing I can do (move, rename, or copy) unless I log back into Linux and rename the files myself from there before being able to copy them.

Is there a way to copy a file stored on an ext3 Linux partition whose filename Windows considers invalid?  I don't mind changing the destination filename.  I *do* mind having to shut down Windows and boot into Linux, renaming, then shutting down and booting back into Windows every time I need to copy such a file.

Thanks in advance for any help.

I think you've answered your own question.

ext3 on linux
ntfs (I presume) on XP

erm, cough !!

rename the files.

---

### Post by Saint Angeles on 2008-03-26
linux can access ntfs partitions or drives... its way easier than logging in and off over and over.

---

### Post by svk on 2008-03-26
> **keratos said:**
> I think you've answered your own question.

ext3 on linux
ntfs (I presume) on XP

erm, cough !!

rename the files.

Thanks for the reply.

I'd love to rename the files, but perhaps I wasn't clear enough: I want to rename files stored on Linux (ext3) while I am running Vista (ntfs?).  This does not seem to be possible (not with fs-driver, not with the Windows command line, not with Cygwin command line).

My only option is to shut down Windows, boot into Linux, rename, then shut down Linux, boot back into Windows, and only then copy.  I was hoping for a quicker method (hopefully one that won't require shutting down at all), if one exists.

---

### Post by Bölvaður on 2008-03-26
> **Saint Angeles said:**
> linux can access ntfs partitions or drives... its way easier than logging in and off over and over.

That is,   you should move the linux files from linux. It has worked for me in the past.

Your windows program understands ext2 but not ext3 (the one ubuntu has).

But if you can avoid using Windows to make files and.. well any kind of document, that would be the best. Much easier to have work and school related stuff on linux and games and some other less safetycritical stuff on Windows.

But your question isn't Ubuntu related at all. You are asking how you can do something on Windows which most people here don't know any more how to work on. You might want to check out the Windows forum.

(just fun to tell: I was playing COD4 on XP when the screen froze and the same sound repeated it self over and over again, everything locked down. So I restarted to go back to Ubuntu and here I am :D )



we all love you :)

---

### Post by aktiwers on 2008-03-26
Maybe this can help you?
[http://ubuntuforums.org/showthread.php?t=236274](http://ubuntuforums.org/showthread.php?t=236274)

---

### Post by rkd on 2008-03-26
Have you tried doing the copy from the Windows command line and using wildcard characters in the filename you enter on Windows?  

? matches any single character and * matches a variable number of characters.  So if the filename you want to copy is abcXdef, where X is a character that Windows won't let you enter, you should be able to type abc?def or abc*def as the input file name for the copy.  Since you'll be giving the output file of the copy a new name, this will only work if you can make the wildcard filename match only one of your files.  Depending on the set of filenames you have, that might not be possible.

Of course, you'll have to specify the full path before the filename; I left out that part.

---

### Post by keratos on 2008-03-27
> **Bölvaður said:**
> That is,   you should move the linux files from linux. It has worked for me in the past.

Your windows program understands ext2 but not ext3 (the one ubuntu has).

But if you can avoid using Windows to make files and.. well any kind of document, that would be the best. Much easier to have work and school related stuff on linux and games and some other less safetycritical stuff on Windows.

But your question isn't Ubuntu related at all. You are asking how you can do something on Windows which most people here don't know any more how to work on. You might want to check out the Windows forum.

(just fun to tell: I was playing COD4 on XP when the screen froze and the same sound repeated it self over and over again, everything locked down. So I restarted to go back to Ubuntu and here I am :D )



we all love you :)

DITTO that one.

If you love 'em, be with 'em.
[http://www.microsoft.com/windowsxp/expertzone/related/default.mspx](http://www.microsoft.com/windowsxp/expertzone/related/default.mspx)

Of course, linux being far superior can read AND write to NTFS paritions thus if you wish to perform anything useful, easily and quickly, use Linux ... returning to Windowze to perform the less complicated tasks (with Vista you'll probably need an upgrade!!)

:lolflag:

---

### Post by hyper_ch on 2008-03-27
> **Bölvaður said:**
> Your windows program understands ext2 but not ext3 (the one ubuntu has).
Ext3 is backward compatible to Ext2.. basically it's Ext2 with journaling... So the fs-drivers work on ext3 also...

---

