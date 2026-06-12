---
title: "Clearing Hard Drive Space - Unbelieveable!!!"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by chewit on 2008-02-06
This is amazing! I was googling for away to clear some hard drive space. I came across this app called SCRUB.

Heres the webpage:
[http://www.ubuntugeek.com/securly-clear-free-hard-drive-space-with-disk-scrub-utility.html]("http://www.ubuntugeek.com/securly-clear-free-hard-drive-space-with-disk-scrub-utility.html")

This app is amazing. I installed it on ran it in the terminal. It first filled all my free space, at this point I was slightly worried, I thought I have now messed up my PC. So I carried on. Next thing I had to do was remove this "junk" it called it.

When I did that, I saved about 600mb of my hard drive. 600mb saved on a 7GB drive. Unbelieveable.

I recommend you all should try this!

---

### Post by mikewhatever on 2008-02-06
According to the info on the page you provided, the program writes random data to already free disk space. I am not sure why you got 600 Mb freed. Hope it did not delete something useful.

---

### Post by insane_alien on 2008-02-06
its for securely deleteing data. it doesn't actually free up space. not sure what you done.

---

### Post by chewit on 2008-02-06
Lol, but the article does say it will free up space. My PC still works fine. If anything, its slightly quicker, due to the more HDD space.

---

### Post by prabbit237 on 2008-02-06
> **chewit said:**
> Lol, but the article does say it will free up space.

Ummm, no, it does not. It says it will fill the free space and then it'll delete the temp files used to fill it. So if you had to "remove this "junk"" afterwards, then (1) something didn't run properly and you might have had to remove the temp files yourself and (2) in the process, you might have deleted something else that wound up giving you more room.

---

### Post by yaknowwat on 2008-02-06
I have a feeling I know what it deleted.

When you download from the repo's it will save a copy of the tarball so the next time it wants to download it has a back up also useful for a reinstall.
I may be wrong on the repo back ups but it seems that way when i normally do a reinstall something all that gets downloaded is one 40kb thing or so on a 10 Mb app.

---

### Post by chewit on 2008-02-06
Well what ever its deleted, its seems to have do it safely and nothing has damaged my PC.

---

### Post by emarkd on 2008-02-06
Yes, apt keeps downloaded .debs (they're not tarballs) in /var/cache/apt.  You can clear them out by running:

```
sudo apt-get autoclean
```

---

### Post by mysticrider92 on 2008-02-06
From the description, I would guess that program is meant to be used after you have deleted files you don't want people to access. For example, you delete some old finantial documents with personal info on them, but they can still be recovered if someone is really trying to get to them. Run that program, and it overwrites the traces of the documents, cleaning out your information and replacing it with empty space..

This has nothing to do with freeing up hard drive space. Kmandla has a few very useful tips in his "speed up Ubuntu" guides ([found here]("http://kmandla.wordpress.com/2007/10/20/howto-set-up-gutsy-for-speed/")) that are much better suited for cleaning out unneeded files.

---

