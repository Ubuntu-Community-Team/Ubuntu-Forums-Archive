---
title: "WIne &amp; WOw"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by cold-peak on 2006-11-18
Hi all,

right, ive installed WOW with Wine - followed all the official instructions for (Ubuntu 6.10 Edgy Eft)

However i cannot see where it has been installed into the wine directory.

I cd'd to the directory and did the 

```

ls

```

and it showed that the World of Warcraft directory existed, however i cannot CD to it through terminal or see it in the main browser...

any ideas?:-k

---

### Post by LLRNR on 2006-11-18
Just curious... you mean you installed World of Warcraft through Wine (I don't know what you're talking about, I didn't do this myself) and that you try to get IN the folder where it's actually installed to do ... let's say something like "wine wow.exe" I suppose. If you DO see the folder, it's usually located at ~/.wine/drive_c/Program\ Files/NameOfWoWFolder/wow.exe.

Now from what I understand you can get on the upper level (this being "Program Files" or something similar, "Games", I don't know) and when you **ls** you can see *NameOfWoWFolder* but when you try to **cd** to that directory, you're not allowed to get in, right?

Ok, _if_ I got it correctly, I think you could try the following: stop in the upper level (this being "Program Files" or "Games" or where ever you installed it) and type **ls -al**. You should then try to locate the game's install dir (suppose it's called *NameOfWoWFolder*) and check its corresponding row, the leftmost column. Here you should see 10 little... thingies starting with letter '**d**' which stands for "directory". Next there are 9 little... thingies; in fact these are the bytes representing the permissions to the file. (r is for read, w is for write and x is for executable) 

Check and see if you have read and execute permissions on the folder; you need both of them since you a) want to read from it and b) you also want to enter it (that being "execute"). You can change permissions by

```
sudo chmod +rx NameOfWoWFolder
```

I think this should do it, you can then enter the folder and from inside you can issue "wine wow.exe".

HTH,

LLRNR

---

