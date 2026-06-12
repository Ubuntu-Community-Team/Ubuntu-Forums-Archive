---
title: "Error while updating"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by hidey on 2007-05-02
Hi, first time poster and about a two week user here. I've gotten Feisty and all the extras to work for me with little to no problems and I've usually found solutions to my problems really easily, but today something went wrong with the update thingy and frankly I have no idea what I should be looking for. Here's the error it throws at me:

E: Problem parsing dependency Pre-Depends
E: Error occurred while processing frostwire (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

It also had an error about duplicate entry with some Beryl repos, but that was easily solved and it doesn't show up anymore.

---

### Post by zvacet on 2007-05-02
You did the upgrade with unofficial repos in your source list.That´s cose errors.Comment all unofficial repos(put # sign in front of the line).

```
sudo aptitude update && sudo aptitude upgrade
```

When you are finish you can comment out previous lines (remove # sign) and again

```
sudo aptitude update
```


You will edit your source list with this

```
gksudo gedit /etc/apt/sources.list
```

after every change you do save the file and exit

---

