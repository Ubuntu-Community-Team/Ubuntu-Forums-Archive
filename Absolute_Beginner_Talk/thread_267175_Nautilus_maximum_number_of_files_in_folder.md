---
title: "Nautilus: maximum number of files in folder?"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by stig on 2006-09-28
Is there a maximum number of files that can be listed in a folder in Nautilus?

I have taken the files (documents) from several folders and placed them in one folder, which now has 627 files and weighs 70 MB. Every time I open the folder in Nautilus file manager it freezes and I have to Force Quit. But it opens OK in XFE file manager, and the previous individual folders gave no problems.

I have never had this problem before. I'm using a 2.8 GHz Pentium PC with 1024 MB RAM and 80 GB hard disk (with plenty of unused space) and Ubuntu Dapper 6.06.

The only reason I can think of is that I have exceeded the maximum number of files that Nautilus can handle. Has anyone else got thoughts on this theory?

---

### Post by orb9220 on 2006-09-28
No i have browsed pic folders in the 900-1200 range just fine. It may be a wierd corupt document file. Did you browse in thumbnails,details,icons? Try different ones.

On this kind of problems I would send everything to the trash and then start copying files back to that directory until it breaks then look at the last batch I copied there.

---

### Post by slimdog360 on 2006-09-28
Ive always had problems with Nautilus, hence why I use konqueror, but Im also at the moment looking into using [krusader]("http://krusader.sourceforge.net/").

But yeah I think you might be onto something there with the maximum amount of files nautilus can handle before crashing.

---

### Post by stig on 2006-09-28
It looks like orb9220 was right and it is not a result of having too many files but due to a corrupt file - or at least a file that Nautilus does not like.

I was using file detail view, so I tried icon view and the folder was OK. Using XFE, I switched half the files to another folder and tested them in Nautilus. That worked OK, so then I halved the remaining files and so on, until I got down to a small group of 5 files that had to contain the troublemaker. I deleted these because none of them was sufficiently important to keep.

Now I have almost all my files and they list OK in Nautilus. Logic triumphs over panic again!

Thanks for the help :D

---

