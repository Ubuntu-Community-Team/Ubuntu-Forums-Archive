---
title: "How do I import my FF bookmarks into FF in ubuntu? File &gt; import doesn't work..."
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by Jaimes_Phazon on 2007-12-28
When I try to import bookmarks with firefox in ubuntu I get the message "No programs that contain bookmarks, history or password data could be found."

I would just copy the bookmarks.html file manually except I don't know where to go in ubuntu.

---

### Post by dondad on 2007-12-28
> **Jaimes_Phazon said:**
> When I try to import bookmarks with firefox in ubuntu I get the message "No programs that contain bookmarks, history or password data could be found."

I would just copy the bookmarks.html file manually except I don't know where to go in ubuntu.

Open the file manager to your home directory. Click "view" then select "show hidden files". look for a folder called .mozilla (note the dot in front of the name, that is what makes it a hidden file). In that folder is one labeled Firefox, and in that folder is a funny number with default at the end of it. That folder is the one that you need to copy the bookmarks.html from your other installation. Make sure that Firefox is closed when you do this or it will overwrite the file you just copied.

---

### Post by silviur on 2007-12-28
That is a Firefox "problem". Start Firefox, choose Bookmarks from the menu, and then Organize Bookmarks. Choose then from the "new" menu which appears File, then Import, then import your html file, This way works :)

---

### Post by bodhi.zazen on 2007-12-28
go to bookmarks -> Organize Bookmarks

On that window go to file -> import .... -> From file -> hit the "next" button

The same window will flash briefly, then navigate to your exported book marks ...

Ubuntu saves bookmarks in /home/user_name/.mozilla/firefox/xxyyzz.default/bookmarks.html

The .mozilla directory is hidden , go to show hidden in nautilus

---

### Post by lackhead on 2007-12-28
I'd also recommend using the FoxMarks plugin- I use it to keep my bookmarks in sync on all my machines (Mac, several Linux boxes, etc).  Super easy to set up, and immensely useful! 

[http://www.foxmarks.com/](http://www.foxmarks.com/)


-c

---

### Post by digga on 2007-12-28
after you get that done, check out the [foxmarks]("http://www.foxmarks.com/") plugin. it will store your bookmarks on a server that you can retrieve later on, or on another pc.

---

### Post by Jaimes_Phazon on 2007-12-28
Okay thankyou everyone. Very helpful.

---

