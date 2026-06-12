---
title: "How much space for Home directory?"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by ravenus on 2007-10-20
For the first time I have kept a separate partition for Home (4GB space, 8 GB for root, is that a good way of doing this?) and I wanted to know how much space is generally used up for a Home directory. In my case I don't store docs/movies/music there since I want to access them in Windows as well. What other data is stored in Home? Will my allocated space be sufficient?

---

### Post by sstusick on 2007-10-20
/home is the equivalent of My Documents and Application Data in Windows. So if you store your docs/movies/music and stuff somewhere else, then 4 GB should be a good amount of space for /home.

---

### Post by ravenus on 2007-10-20
Oh excellent. Thanks for the useful reply :)

So does that mean I can even keep it much less, like say 500MB and still get all the functionality I need from it?

---

### Post by hvc123 on 2007-10-20
Yer but you gotta remember that all your profile ( settings) for eveything as a normall user will be in there so you dont want it to run outa space. 
on the flip side of that you really really dont want root '/' to get to big either.
at work we had a logger going nuts and filled var up but the dill that installed the o/s (sunos 10) never gave var a seperat partition so that when var fills up so did root.  the machine death until we could get in and remove logs.

always always a good idea to have /home, /usr /var as different file systems sometimes even /opt.

---

### Post by ravenus on 2007-10-20
Actually I don't have a proper clue as to what each of these different directories contain. Some quick guide perhaps as to what category of data goes into each of them, would be highly appreciated :). Guess I'm too used to only C:\Program Files, Windows and DOcs & Settings.

---

### Post by sstusick on 2007-10-20
Here,[ this]("http://blog.wired.com/monkeybites/2007/09/newbie-help-map.html") might help you out.

---

### Post by mivo on 2007-10-20
Where do you plan to keep videos, songs, etc. at? :)

---

### Post by ravenus on 2007-10-20
Oh keep them on separate media partitions (NTFS). That way I can access them in both Windows and Linux.

---

### Post by mivo on 2007-10-20
Okay, so you only need a relatively small /home partition. Without media files, the stuff in my /home occupies roughly 2.2 GB, including about 200 MB of Windows programs that run in Wine (those are saved in your /home as well). This also includes about 1 GB of mail, which is also stored in your /home. So if none of these apply, just one gig for /home would probably be perfectly sufficient for your purpose, though in your case I would consider not using a separate /home partition at all since you could simply backup the /home directory on an USB stick if you ever need to reinstall the core system. :) Just 10 GB for / would cover you, everything included.

---

