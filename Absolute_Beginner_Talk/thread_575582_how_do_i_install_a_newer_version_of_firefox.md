---
title: "how do i install a newer version of firefox"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by watkinsted on 2007-10-14
How do I install a newer version of firefox.  I downloaded FF 2.0.0.7 and have 1.5.0.12 on my system.  Been getting more and more errors with 1.5.0.12 and would like to see how well 2.0.0.7 works.  I've down loaded and extracted to a folder on my desktop, and would like to install it.  What else do I need to do?

---

### Post by klytu on 2007-10-14
> **watkinsted said:**
> How do I install a newer version of firefox.  I downloaded FF 2.0.0.7 and have 1.5.0.12 on my system.  Been getting more and more errors with 1.5.0.12 and would like to see how well 2.0.0.7 works.  I've down loaded and extracted to a folder on my desktop, and would like to install it.  What else do I need to do?

I would suggest trying the script here first: [http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

If the prospect of using a script makes you uncomfortable, then use the method detailed here: [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by alienexplorers on 2007-10-14
I just went to the mozilla site and downloaded the tar.gz file.  Un tared the file and setup a launcher to load the program.  The first time I ran it I went to the firefox directory and entered ./firefox -profilemanager and set up a profile for firefox.  From there I created a launcher to load firefox.

---

### Post by watkinsted on 2007-10-14
Ok this is what I did, I downloaded the newer version, following the guide that was first posted in response to this, it worked well, except......lol, well now i need to somehow, get my plugins back and history, and bookmarks, lol, saved all of them to a folder on my system, do I need to move that folder and/or its files to the firefox folder where this is installed?

---

### Post by nanotube on 2007-10-14
> **watkinsted said:**
> Ok this is what I did, I downloaded the newer version, following the guide that was first posted in response to this, it worked well, except......lol, well now i need to somehow, get my plugins back and history, and bookmarks, lol, saved all of them to a folder on my system, do I need to move that folder and/or its files to the firefox folder where this is installed?

well, that all depends on which of the guides posted in response to this you followed. :)

generally, if you saved the whole profile, then just point your new firefox to the backed up profile directory with the profile manager; or copy the contents into the new profile dir.

btw, if you use ubuntuzilla it will automatically use your old profile and plugins and etc, so you don't have to do anything...

---

### Post by Therion on 2007-10-14
I don't know about your History files and Extensions, but if you used the Export function in Firefox to create the bookmarks.html file, use the Import function to get your Bookmarks back:

Open Firefox.

Navigate to: Bookmarks/Organize Bookmarks/File/Import  (navigate to your saved bookmarks file and select it).

Again, the above assumes you used the Export function from the beginning.

I also recommend the FoxMarks extension.  It saves your booksmarks to a server so you can retrieve them any time, or synch your bookmarks between computers: [http://www.foxmarks.com/]("http://www.foxmarks.com/")

---

