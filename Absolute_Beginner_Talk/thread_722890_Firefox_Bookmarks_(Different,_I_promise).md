---
title: "Firefox Bookmarks (Different, I promise)"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by arenputt on 2008-03-12
Using [this method]("http://ilias.ca/blog/2006/04/customize-the-firefox-bookmarks-location/") I would like to setup my dual boot Vista and Ubuntu to use the same bookmarks file.

I successfully moved the bookmarks in Windows, and it looks like FF in Ubuntu is looking for another the new location, but not seeing the file. The file is located under Documents on the Vista partition, and I can see that both through Dolphin and terminal.

It seems to me that I am simply not pointing FF to the right place. 
This is where I tell FF to look
/media/sda1/Users/jwd0310/Documents/Firefox\ Bookmarks/bookmarks.html

Any ideas?

---

### Post by jimrz on 2008-03-12
simplest way to get them the same and keep them that way is to get the "Foxmarks" extension for FF, which provides synchroniziation of bookmarks files on multiple machines and works in both linux & win

---

### Post by arenputt on 2008-03-13
Yes, I know about that, but I would really like to know what I am doing wrong here.

---

### Post by bluewraith on 2008-03-13
Using foxmarks, you can sync from windows to the server, and then from the server to ubuntu. Pretty simple there. Takes about 5 minutes not including reboot times. 

My only problem now is that I have bookmarks that I only need under Windows, and bookmarks that I only need under Ubuntu. Not too big of a deal though, just set myself up with about 6 different folders in the bookmark menu. :)

---

### Post by kerry_s on 2008-03-13
> **arenputt said:**
> Using [this method]("http://ilias.ca/blog/2006/04/customize-the-firefox-bookmarks-location/") I would like to setup my dual boot Vista and Ubuntu to use the same bookmarks file.

I successfully moved the bookmarks in Windows, and it looks like FF in Ubuntu is looking for another the new location, but not seeing the file. The file is located under Documents on the Vista partition, and I can see that both through Dolphin and terminal.

It seems to me that I am simply not pointing FF to the right place. 
This is where I tell FF to look
/media/sda1/Users/jwd0310/Documents/Firefox\ Bookmarks/bookmarks.html

Any ideas?

it's your path->
/media/sda1/Users/jwd0310/Documents/Firefox**\ **Bookmarks/bookmarks.html
should be->
**/media/sda1/Users/jwd0310/Documents/Firefox/Bookmarks/bookmarks.html**

---

### Post by wnwek on 2008-03-13
Or you could us Google Bookmarks :)

---

### Post by harvestersel on 2008-03-13
this is a great deal of help for all the people who will visit this page thanks to all of you.

---

### Post by arenputt on 2008-03-13
> **kerry_s said:**
> it's your path->
/media/sda1/Users/jwd0310/Documents/Firefox**\ **Bookmarks/bookmarks.html
should be->
**/media/sda1/Users/jwd0310/Documents/Firefox/Bookmarks/bookmarks.html**

One thing, the name of the folder is "Firefox  Bookmarks". I use "\" to signify a space in a folder name. Is that wrong?

Thanks for the help thusfar!

---

### Post by arenputt on 2008-03-17
Ok, got it working for those still interested. FF does not like the Firefox\ Bookmarks folder name. I renamed it to Firefox_Bookmarks and everything works.

Both OS's use the same bookmarks file without having to synch to a server.

---

