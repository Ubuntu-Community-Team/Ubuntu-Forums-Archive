---
title: "Viewing local and compressed .html files"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by DonQuixote on 2006-02-01
Hello all,

I'm running into an interesting error and am hoping for some information on it.

I have downloaded a .tgz file that contains .html files.  Now, I have tried viewing them directly from the "Archive Manager" but whether I "View" or "Open" them with a right-click on any of the .html files I get this error:

"Could not perform the operation
Error launching command"

I'm trying to view/open these files in Firefox.  They will open in an editor, but not in Firefox.  Is there something I am missing?

Thanks!

John

---

### Post by Enter on 2006-02-01
hmm unzip it then
right click and run it in a different program?

---

### Post by saubz on 2006-02-01
try this

system-> prefrences-> preferred applications

select FIrefox as your default web browser

---

### Post by DonQuixote on 2006-02-01
Thanks for the replies.

I have Firefox as my prefered browser in my prefered applications, and even if I unzip the .html file and then try viewing it, I get this error:

"Couldn't display "/home/john/downloads/index.html"
There was an error launching the application."

hmmmm..... on further investigation, I seem to have a pathing problem...

In my prefered application command line under "browser" I had, "firefox %u" (can anyone tell me what '%u' represents?), so I changed it to "/usr/firefox/firefox %u".  That did not work, so I took off the "%u" and tried several different ways from the right-click on the file, as well as double clicking it.

Double clicking the file, did not work.

Selecting the "Open with Firefox web browser" right click option did not work.  I got the same error as double clicking.

'Open with->Open with "firefox"' worked.

Interesting.

Anyone know why double clicking and the first right click option would not work, but the other would?

Thanks!

John

---

### Post by Enter on 2006-02-02
im not sure but i think you set the default program in file properties, cant tell you now cu im in win2k

---

