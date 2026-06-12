---
title: "Can you update v5.04?"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by andrewsco on 2005-12-28
Hi guys.

My first post! I am just wondering whether it is possible to update an existing version of ubuntu to the new version (I have 5.04) as I dont have a cd burner. I could always ask for another CD through the post, but a) I don't really want to wait, and b) I'd like to save you guys some money. I suppose its not essential that I update, its just nice to keep up to date I guess.

Thanks
Andy

---

### Post by Lord Illidan on 2005-12-28
> 

My first post! I am just wondering whether it is possible to update an existing version of ubuntu to the new version (I have 5.04) as I dont have a cd burner. I could always ask for another CD through the post, but a) I don't really want to wait, and b) I'd like to save you guys some money. I suppose its not essential that I update, its just nice to keep up to date I guess.



Nice thoughts. However, rest assured that getting 10 cds of Ubuntu is not going to break the bank, especially if you give them a donation afterwards. ;) However, yes, it is a loong wait. You can essentially change the repos, and update to breezy badger like that, but it can be troublesome. I would recommend shelling out for a cd/dvd burner. Prices are really low, and probably, you will need one in the near future for back ups and the like.

---

### Post by DevilsAdvocate on 2005-12-28
Go into your source.lst file.  In every line, where you see hoary -> change it to breezy.  Save and close.  Open up a terminal and do:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

This isn't foolproof, so it's a good idea to have a Hoary disk around just in case.

---

### Post by DevilsAdvocate on 2005-12-28
path to sources.list

/etc/apt/sources.list 

The Wiki also has instructions for this.

---

