---
title: "backin up bookmarks"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by dmichaels on 2006-11-04
ok so i have to wipe edgy off my hard drive after upgrading to it. never have i had to downgrade after an upgrade but yea theres a first time for everything. anyhow all im askin is if there is a way to back up my bookmarks i have in firefox before i completely wipe my system and start from scratch all over again...oh yeah how do i back my data up if all i can use is the fail safe terminal?

---

### Post by adam.tropics on 2006-11-04
If you look at the bookmarks menu at the top, you can 'Organise bookmarks'. From there, in the file menu, you are able to export and import your bookmarks to a file.

oops...didn't read the whole thing sorry. The bookmarks are kept in an html file which you will find in /home/<username>/.mozilla/firefox/?????.default/bookmarks.html so from terminal you coulkd copy it to wherever you like.

---

### Post by bulldog on 2006-11-04
Use the live cd to mount your partition and backup your data.
```
sudo mkdir /mnt/rescue
```
```
sudo mount /dev/hd0,? /mnt/rescue
```

And backup,your bookmarks should be in your firefox profile.

---

### Post by Jellicletrb on 2006-11-04
If you go up to the top toolbar on Firefox, you'll see "Bookmarks".  
When you click that, you'll get a drop down menu, go to "manage bookmarks"....then when the bookmarks manager opens, go to "file" and then "export bookmarks".  You can send it where ever you want as a file  :KS

---

### Post by localuser on 2006-11-04
> **dmichaels said:**
> if there is a way to back up my bookmarks i have in firefox before i completely wipe my system and start from scratch all over again

I found Foxmarks to be a great little add-on...

[http://www.foxmarks.com/](http://www.foxmarks.com/)

---

