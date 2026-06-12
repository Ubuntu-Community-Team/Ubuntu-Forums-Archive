---
title: "Changing permissions of files and folders"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by jigantor on 2006-02-21
I've just copied my entire music collection from windows via DVD (all 30GB of it!), and obviously the copied files are all marked as read-onle (having come straight from DVD-R). I was wondering if there was any way of making all the files in the subsidiary folders (thanks to iTunes there's a separate folder for each artist) writable without opening up each individual folder, selecting the files and changing the permissions? Because doing it that way will take many tedious hours...

---

### Post by kaamos on 2006-02-21
Hello!

As nautilus does not yet handle recursive permissions, you can do this from the terminal. Applications->Accessories->Terminal

```
chmod +w /path/to/the/music/root -R
```
And if that does not work
```
sudo chown jigantor:jigantor /path/to/the/music/root -R
chmod +w /path/to/the/music/root -R
```

---

### Post by BoyOfDestiny on 2006-02-21
[QUOTE=kaamos]Hello!

As nautilus does not yet handle recursive permissions, you can do this from the terminal. Applications->Accessories->Terminal

```
chmod +w /path/to/the/music/root -R
```
And if that does not work
```
sudo chown jigantor:jigantor /path/to/the/music/root -R
chmod +w /path/to/the/music/root -R
```[/QUOTE]

I usually do:

sudo chmod 777 -R /blah/blah

I will be a happy camper when/if nautilus has support for setting folder permissions recursively... I even started a few threads about it... I'm sure more people will run into it, especially those who use dvd+rw and cdrw with nested folders... :)

---

### Post by kaamos on 2006-02-21
Hopefully it soon will. Thunar got this some time ago.

---

