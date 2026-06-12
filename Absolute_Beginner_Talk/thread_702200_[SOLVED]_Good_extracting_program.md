---
title: "[SOLVED] Good extracting program"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by articwolf939 on 2008-02-20
im looking for a program that extracts .r1 type files like the kind u download from torrent with the gnome extractor work or do i need to download one?

---

### Post by Kilz on 2008-02-20
> **articwolf939 said:**
> im looking for a program that extracts .r1 type files like the kind u download from torrent with the gnome extractor work or do i need to download one?

What exactly are you downloading from the torrent site that is broken up into parts?

---

### Post by emshains on 2008-02-20
> **Kilz said:**
> What exactly are you downloading from the torrent site that is broken up into parts?

yes i also have the prob...

Some downloads have a file split into 10-15 mb archives with the endings of .r[x]
x means the number of the archive, like i have .r1 .r2 .r3 and so on and so on.
So is there an archive extracter for these files ?

---

### Post by p_quarles on 2008-02-20
My guess is that you are both talking about split .rar files. Fileroller handles .rar files last I checked, but I don't know if/how well it handles split ones. If it doesn't, try installing the proprietary version of unrar:
```
sudo apt-get install unrar
```
You will need to have the universe repository enabled for this to work. If that doesn't work, you might try using WinRar with Wine (this is Shareware, and comes with a free trial period).

---

### Post by jordanmthomas on 2008-02-20
I can confirm that unrar + file-roller can handle split rars no problem.
Just tell it to extract the first in the series (though I think any would work) and it'll extract no problem.  It even works if the rars are passworded.

---

### Post by jordanmthomas on 2008-02-20
There's still the .01 percent that are legitimate rar files.

For example, my brother sent me some pictures from Christmas and packed them up as 10 MB-split rar files.  It was convenient and could travel through the mail, and now I have a backup in my mail.

---

### Post by p_quarles on 2008-02-20
> **jordanmthomas said:**
> There's still the .01 percent that are legitimate rar files.

For example, my brother sent me some pictures from Christmas and packed them up as 10 MB-split rar files.  It was convenient and could travel through the mail, and now I have a backup in my mail.
It's beside the point either way. Neither the torrent protocol nor the .rar archive format are in any way illegal, anywhere. 

@Kilz: There is no need to announce that you aren't going to help with something. Just don't help. And please don't take threads off-topic.

---

### Post by billgoldberg on 2008-02-20
Yep unrar works great with split up rar archives.

If unrar is installed you just right-click the first rar file, and choose extract here. That's it.

---

### Post by articwolf939 on 2008-02-20
i found one call peazip also work great :)

---

