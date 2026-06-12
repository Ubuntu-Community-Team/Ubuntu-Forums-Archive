---
title: "installing printer using command line"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by Dalkantrell on 2007-01-01
I am trying to use HPLIP self extracing archive with installer.  These are the instructions found on [http://hplip.sourceforge.net/downloads.html:](http://hplip.sourceforge.net/downloads.html:)

To use the self-extracting file, follow these steps:

   1. Download the file to a convenient location (e.g., home directory or desktop, etc).
   2. Open a console/terminal and cd to the download directory.
   3. Type in and run this command: 'sh ./hplip-1.6.12.run'

I saved the file in the desktop folder and I have no idea how to do what they are asking.
Any help would be greatly appreciated!

---

### Post by Sef on 2007-01-01
Why don't you install via System > Administration > Printing?

Read H[ow to install anything]("http://monkeyblog.org/ubuntu/installing/") in Ubuntu. (note: it is still not loading, but once it times out, you can look it it (in google) by clicking on the cached version.)

---

### Post by Dalkantrell on 2007-01-01
It doesn't recognize the printer.  It's an all-in-one.  I have already found the file to make the printer work and placed it in /usr/share/cups/model and got the printer to work.  However, it doesn't recognize the scanner functionality.  So I went back and got this installer that is supposed to add the functionality as well.  I just don't understand how to change directories to do what it instructs.

---

### Post by Sef on 2007-01-01
What is your make and model of your all-in-one?   Sorry I didn't ask it before.

For the scanner, have you tried Applications > Graphics > Xsane Image Scanner?

---

### Post by Dalkantrell on 2007-01-01
HP Deskjet F335.  Yeah, I already tried XSane.  I even tried to run it as root.  That's why I am trying to run this file. But, I don't understand the directions.  I don't know how to get it to change to the directory the file is stored (desktop).

---

### Post by Dalkantrell on 2007-01-02
Okay I figured out how to change directories and got the installer to run in the terminal.  Not it says an apt-get program is running and I need to cancel it to continue.  Sigh.  Why is nothing ever simple?  The only thing I have running is the terminal.  What could it be talking about?

---

### Post by Sef on 2007-01-02
Have you checked out the [HPLIP Support]("http://hplip.sourceforge.net/supported_devices/inkjet_aio.html") Page?

---

### Post by 11hjpphty76lkjj on 2007-01-12
Do this:

```
sudo apt-get install lsb
```

then

```
sh hplip-1.6.12.run
```

The docs say to run sh ./hplip-1.6.12.run, I've removed the ./ and updated the docs. They will be updated at the next release.

Aaron

---

### Post by Dalkantrell on 2007-01-13
Thanks that worked perfectly.  What was the install lsb for and how did you know that would fix it?  I'm so new at this and I just want to understand what I'm missing when I do things like this...

---

### Post by 11hjpphty76lkjj on 2007-01-19
Sorry for the delay.  The lsb is used in several of the init scripts I believe.  I'd have to check with the backend engineer for specifics.

It isn't anything you should have known to do.  I provide support for HPLIP and as such have a good deal of experience with it. :)

All the best,

---

