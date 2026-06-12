---
title: "Quick Question - Ubuntu not mounting Harddrives??"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Goldeneye on 2007-01-12
Alright, I admit this is a total n00b question, but can you mount harddrives without actually installing Ubuntu? I swear (I might have been hulucinating) my harddrives were mounted with the Live CD.



The message:

[INDENT]**Unable to mount the selected volume**

error: device /dev/hda1 is not removable

error: could not execute pmount[/INDENT]

---

### Post by rai4shu2 on 2007-01-12
To mount using the live CD you have to do something like this in a console:

sudo mkdir /mnt/linux 
sudo mount /dev/hda1 /mnt/linux

---

### Post by redsox59 on 2007-01-18
I'm having the same problem except after that I get an error: "mount: you must specify the filesystem type" The harddrive I tried mounting was my ubuntu drive. Its the only haddrive and only partion in my computer. Could my harddrive be fried?

---

### Post by taurus on 2007-01-18
Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by redsox59 on 2007-01-18
Nothing comes up with that command just goes to a new line in terminal. Odd because I've definatly used that command before and gotten a response.
Its sorta like sudo isn't working or something

---

### Post by rai4shu2 on 2007-01-18
sudo fdisk -l <-- note this is a lower case L

---

### Post by bugster on 2007-01-18
[QUOTE=Goldeneye;2001514]Alright, I admit this is a total n00b question, but can you mount harddrives without actually installing Ubuntu? I swear (I might have been hulucinating) my harddrives were mounted with the Live CD.



I'm glad someone else mentioned this.  I am sure that the first time I tried the live cd I could see my windows disk data.  Since installing though I'm still working on finding it again.  Thought I must be going senile or something ...

---

### Post by redsox59 on 2007-01-18
> **rai4shu2 said:**
> sudo fdisk -l <-- note this is a lower case L

yes I know what im doing but no dice

---

### Post by taurus on 2007-01-18
Take a screenshot of a terminal with that command (with a return) and see exactly what's going on unless you don't have a harddrive on the machine or the harddrive is dead!

---

