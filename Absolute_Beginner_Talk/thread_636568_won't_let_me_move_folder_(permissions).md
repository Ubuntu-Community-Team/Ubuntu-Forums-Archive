---
title: "won't let me move folder (permissions)"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by mikehtiger on 2007-12-09
I get error message "you do not have permissions to write to this folder" when trying to copy songs to frets on fire video game folder... any suggestions???

---

### Post by twistedbydesign on 2007-12-10
Right Click the folder you are trying to move,then go to properties, Then go to the permissions Tab.
It should say "owner" then have your username beside it
Directly under that it should say "Folder Access", try switching it to "Create and delete files". or one of the others if that doesnt work
If that doesnt work you may have to try it with the individual files. (try selecting them all).
Good luck!

---

### Post by ssmithy on 2007-12-10
You could also open up a terminal and use the cp command with sudo.

---

### Post by nikoPSK on 2007-12-10
no. That won't work

```
sudo chown -R username foldername
```
then go to the folder and move the file there manually.

example:

sudo chown -R niko /usr/share

---

