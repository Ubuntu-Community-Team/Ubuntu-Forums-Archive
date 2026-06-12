---
title: "Path ? File not found issue"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by genesain on 2006-09-30
I have some simple local html pages that I use as a menu, home page, navigation for Firefox.  I copied the pages over to a new folder named HTML in my user home directory.  I can open individual html pages with Firefox, but the main page has an uppper and lower frame .... top displays contents either the default or selected menu item, and across the bottom I have a simple menu of 2 rows of links. When I try and open "new menu home.htm" it gets file not found for "search.htm" eventhough they are both in the same folder so the page will not display. The permissions on the html files are set to read and write.  Is this a path issue ?  Normally within Windows I can put these in any directory, as long as in the same one, and the navigation works ok and everything is found.  Somethin I have to define differently or better place to put these so they resolve finding each other correctly ?

---

### Post by daller on 2006-09-30
It seems like a relative-path issue!

When hovering the link, what path does it display in the status-bar?

---

### Post by genesain on 2006-09-30
The main page with the 2 frames does not open at all ... gives error msg in Firefox that it can not find search.htm. 

The normal default src (what's displayed) for the upper frame is search.htm to be displayed in the frame "contents.htm" and the lower frame "menu2.htm" displays menu.htm.  Normally, as long as the .htm files and their graphics file are all in the same directory, you do not need the full path.

I tried editing the frame page with NVU to re-establish and save the links. Opening it in graphics modes generates the same file not found message ... leaving the file in un-editable mode although you can display the source html.

So, I tried editing the html page just using the system text editor and change the src reference "search.htm" to ///home/ubuntu/html/search.htm" to see if that helps ... still does not find it.  The specific action I am doing with Firefox is File - Open ... navigating to the /home/ubuntu/html folder and selecting new homes frames.htm.  The error message is Firefox can't find the file at /home/ubuntu/html/search.htm .... does not have ///home ..., just the single slash. Tried also using //home as the starting reference point.  So I agree it's probably a relative reference issue, the question is how to fix it ?

Move the files to another location that is part of the system's path, e.g outside the home directory ??

---

### Post by genesain on 2006-09-30
Left out one point ... I can open the lower frame file from Firefox and just display the menu. When I hover over Search it displays file:///home/ubuntu/html/Search.htm  and search will launch when you select it ... but you lose the menu bar page.  I can open and edit menu.htm in NVU and display links to the individual .htm pages for each item ... simple 2 row table with 5 entries each. Link is to the file.  This would work before I did anything with NVU ... so it is resolving the path ... just the dual frame page that is stuck.

---

### Post by genesain on 2006-10-03
Resolved ... for some reason when it copied search.htm from Windows to my Ubuntu folder it changed its case to Search.htm .... resolved everything by making all of the htm file names lower case.

---

