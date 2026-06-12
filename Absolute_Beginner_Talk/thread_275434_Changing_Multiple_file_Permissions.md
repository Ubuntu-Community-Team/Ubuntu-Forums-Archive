---
title: "Changing Multiple file Permissions"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by think13 on 2006-10-11
So, for some reason, this folder I have and everything in it has only root permissions.  It is a folder with a program I want to run a lot, without root logon, in it.  Is there a way I can change all the files' permissions that are in this folder at once?

---

### Post by PriceChild on 2006-10-11
What program is it and how did you install it?

You may change permissions like this:
```
sudo chown <<username>>:<<username>> -R /path/to/folder
``` to change the user, or
```
sudo chmod ### -R /path/to/folder
```
where ### are numbers e.g. 775. 664 etc.

The -R means "recursive" and will apply it to everything within the targetted folder also.

I suggest you post your intentions so we can check you won't experience any breakages.

---

### Post by Rhubarb on 2006-10-11
From memory I think it's something like this:
```
sudo chmod -r 777 NameOfFolder
```
The "-r" bit should make it recursive, so it applies to everything in "NameOfFolder".

Please don't take my word for it, as I'm at work using horrible m$.
I'm still learning this stuff myself, so you might need to use the "chown" command aswell.
For info just type in "man chmod", or "man chown".

Edit: Arrgghhh, someone has already beaten me to it.

---

### Post by think13 on 2006-10-11
When I try what you both suggested, I get this:

~/$ sudo chmod -r 777 /usr/local/bin/StepMania-3.9
chmod: cannot access `777': No such file or directory
~/$ sudo chmod 777 -r /usr/local/bin/StepMania-3.9
chmod: cannot access `777': No such file or directory
~/$

---

### Post by PriceChild on 2006-10-11
Big lesson... Linux is case sensitive :)

that -r should be a -R

---

### Post by dabear on 2006-10-11
> **PriceChild said:**
> Big lesson... Linux is case sensitive :)

that -r should be a -R

Well, it's not. However, ext3,reiserfs etc are. And offcourse, programs decide them self if their options should be case sensitive.

In Edgy, you can do this graphically, by right clicking a file and choose properties.

---

### Post by think13 on 2006-10-11
Thanks, that worked.
I assumed -r would work, because that is what is used for rm when you want to delete an entire folder, and yes I am aware that that is dangerous.

---

### Post by PriceChild on 2006-10-11
> **dabear said:**
> Well, it's not. However, ext3,reiserfs etc are. And offcourse, programs decide them self if their options should be case sensitive.

In Edgy, you can do this graphically, by right clicking a file and choose properties.Point taken :) Thanks for the correction.

---

### Post by Frankenchrist on 2006-10-29
What are the numerical codes for User and Group, but not Others?

I am assuming that 777 gives everybody permissions, but how can I give just my group permissions?

---

