---
title: "cannot install printer driver"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by jerrallan on 2006-10-11
I downloaded a tar.gz driver to the desktop from the lexmark website.  I followed the directions in a July/August thread about installing this driver.

When I enter tar -xvzf CJLZ600LE_CUPS_1_0_1.TAR.gz in the terminal I get:

tar: CJLZ600LE_CUPS_1_0_1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

What do I need to do?  


Earlier, I had a bin file on the desktop and when I executed a command it also
stated there was no such file or directory.

I am a very new newbie and trying to learn ubuntu (6.06), but it is a hard go.  Familiar and worked with DOS in the windows 3.1 and 95 days.

Thanks
Jerry

---

### Post by steve.horsley on 2006-10-11
Maybe you didn't give the proper path to the file. If it's not in the current directory, you need to say where to find the file, e.g.  tar xvfz /home/steve/whatever.tar.gz.

Or maybe you mis-spelled the file name - Linux is case sensitive, and tar files are usually .tar, not .TAR. When typing long filenames, remember that <Tab> will try to complete filenames for you - this saves lots of slow keyboard pecking and lots of spelling errors.

You could also unpack the file by right-cliking it with the file explorer and choosing Extract Here.

When you try to execute a command, two conditions have to be met:

1) you may have to give the full path - the current directory is not in your path, so you may have to say **./filename** to launch executables in your curretn directory.

2) The file must be marked as executable. Unlike Windows, this is a property much like the read-only property. Right-click the file in the explorer and choose properties (Permissions tab) or from the command line, it's **chmod +x filename**.

---

