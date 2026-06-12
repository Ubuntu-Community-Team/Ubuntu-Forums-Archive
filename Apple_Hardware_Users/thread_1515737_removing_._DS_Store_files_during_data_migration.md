---
title: "removing ._DS_Store files during data migration"
date: 2010-06-22
forum: Apple Hardware Users
---

### Post by GROwen on 2010-06-22
Hi all, 

I'm migrating data (music and videos mainly) from a NAS server that was being used as my iTuens Media Folder onto a fresh install of Ubuntu 10.04 and I'd like to get rid of all the ._DS files as well as other files that os x 10.4 has been creating such as duplicates of mp3 files but prefixed with "._".

The reason I'm keen to remove all of these files is because I stumbled across a corrupted ._DS_Store file that caused me all sorts of head aches and I don't want them causing any problems in linux.

I've used the search function in Nautilus to search for ._ but it returns no results, even when I'm searching in a directory that I know for certain has those files in it. I have 'View hidden files' selected.

Thanks for any help you can give me with this.

---

### Post by phildini on 2010-06-22
How deep are the directories you're trying to remove the offending files from?

In any one directory, you could do 

```
rm -rf ._*
```

---

### Post by GROwen on 2010-06-22
in the music folder it could go down 3 directories ie music > artist > album> file, the video directories can go deeper because of structure maybe 4 or 5 levels.

is there a way to have the same command remove the files from sub-directories?

and would I inadvertently be removing Ubuntu system files?

---

