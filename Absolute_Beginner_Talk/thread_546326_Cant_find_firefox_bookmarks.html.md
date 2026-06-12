---
title: "Cant find firefox bookmarks.html"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by luguber on 2007-09-08
help please, cant find the where bookmarks.html is installed, when i do e search i only find theoriginal one but the one i imported and want to replace with an updeted one, importing doesnt work asit it double the size of the file. please what to do?

---

### Post by annda on 2007-09-08
what do you mean imported/updated one?

to find all files with a certain name, the best way is to:

```
sudo updatedb
locate bookmarks.html
```

---

### Post by dondad on 2007-09-08
> **luguber said:**
> help please, cant find the where bookmarks.html is installed, when i do e search i only find the original one but the one i imported and want to replace with an updeted one, importing doesnt work asit it double the size of the file. please what to do?

I just did that. I am running Fiesty on one drive, and dual booting Gutsy on the  other. I wanted my bookmarks from the fiesty in Gutsy. It will be located in a hidden file in your home directory called .mozilla. Note the dot, that makes it hidden. You can enable hidden files in the view menu. Inside the .mozilla folder, go to firefox, then look for a funny number label. That is your profile and your bookmark file is there, called bookmark.htm. Take the one that you want to replace it with and put it in that folder, replacing the one there. You have to make sure that Firefox is not running when you do this, or it will put the old one back. Open Firefox, and your new bookmarks should be there.

---

### Post by luguber on 2007-09-09
> **dondad said:**
> I just did that. I am running Fiesty on one drive, and dual booting Gutsy on the  other. I wanted my bookmarks from the fiesty in Gutsy. It will be located in a hidden file in your home directory called .mozilla. Note the dot, that makes it hidden. You can enable hidden files in the view menu. Inside the .mozilla folder, go to firefox, then look for a funny number label. That is your profile and your bookmark file is there, called bookmark.htm. Take the one that you want to replace it with and put it in that folder, replacing the one there. You have to make sure that Firefox is not running when you do this, or it will put the old one back. Open Firefox, and your new bookmarks should be there.

thanx a lot dondad

---

