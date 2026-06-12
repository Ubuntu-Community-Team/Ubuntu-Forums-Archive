---
title: "Bookmarks"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-12-27
So I just got a brand new HP Pavilion dv6000 for christmas. It came with Windows XP (obviously). Well on my old computer I have Ubuntu Dapper Installed and I have hundreds of  bookmarks and stuff for Firefox on there. How would I go about transferring these from the old computer to this new one? I assume it would just be with a data CD or something but I don't know where to locate them either so... help?

---

### Post by riven0 on 2006-12-27
Just open firefox >> Bookmarks >> Organize Bookmarks >> File >> Export

Then save it wherever you want. Good luck!

---

### Post by taurus on 2006-12-27
Just copy the bookmarks.html in ~/.mozilla/firefox/**<some random letters & numbers>** to the new machine...

---

### Post by AndyCooll on 2006-12-27
Or you could copy that whole folder onto some backup source, then (provided you're running the same version of Firefox) paste it into your new home folder on your new pc.

As mentioned by Taurus, FF stores your stuff here:
```
 /home/yourname/.mozilla/firefox/<some random letters & numbers> 
```

Or ...you could even network the two machines ...

:cool:

---

### Post by voodoonirvana on 2006-12-27
> **AndyCooll said:**
> 

Or ...you could even network the two machines ...

:cool:

And how would i go about doing that? The new one has Windows and the other has Ubuntu Dapper.

---

### Post by voodoonirvana on 2006-12-27
Okay screw the networking thing. Uhhh for some reason that's beyond me, there is no such thing as .mozilla unless your in the terminal.:confused: So I've located the "bookmarks.html" with the terminal but now what? How do I get that onto a data CD?

---

### Post by AndyCooll on 2006-12-31
Networking Ubuntu and Dapper requires the use of Samba (and there are plenty of threads which explain how to do this).

.mozilla is a hidden (by default) folder. If you're viewing your home folder, CTRL+H will display the hidden folders.

And then if you have a CD-burner you can burn the file to a CD (Go > CD/DVD creator).

:cool:

---

### Post by imbill3 on 2007-01-17
Hi Folks .. Well I'm just a noobie .. but, after searching for about an hour on the net, I came to the conclusion that importing/exporting of ie bookmarks into Ubuntu was more trouble then it was worth. And since I'm not a programmer or anything like that, I decided that this was going to require some creativity on my part .. (since I have a ton of bookmarks)

IN THE MEANTIME ... THIS IS WHAT I DID ...

Opened up xp, fired up ie, exported bookmarks to a file called bookmark.html, saved, went to geocities.com (see where I'm going yet?) created a free 'homepage' which took about 5 mins.  Imported bookmark.html and made it a page. (called bookmark.html what else !) closed all geocities pagemaker stuff, and ... 

Rebooted into ubuntu, opened up firefox, went to my 'free' geocities bookmark page .. opened it up and simply added it to my favorites .. so if i want to access it, i now click  bookmark under favorites and bang! there they are !

OK, OK !!!  I know that this is not a real solution, but hey it works for me until I find an easier way !!

Bill

---

