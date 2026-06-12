---
title: "Directory is suddenly ureadable"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by petroskhan on 2007-06-23
Ok, here's the problem.  I have a directory in my home directory, called Docs.  I store a lot of un- and semi-important things in there.  I made a subdirectory, to store some other files.  I was in the process of moving some files from the Docs directory to this new subdirectory, when suddenly the directory display went blank, and just idles there, like it's trying to do something, and I can't see or access any files in the Docs directory, or the subdirectory, of course.  I rebooted, and still had the same problem.  I deleted the whole directory, then tried to look at it from the trash bin, and was able to see the files, but as soon as I tried to open one of them, it went into its meditation routine, and showed me a blank directory again, which I had to force close.  I tried moving the directory from the trash to the desktop, same results.  Some of these files would be a minor pain to replace, but I could, others not.  The main thing is, I would like to know what happened, and why, and how to fix it.  Any thoughts out there in Ubuntuland?

---

### Post by Malibu Illusion on 2007-06-23
Try:

```
chmod 755 -R ~/Docs
```

If not, can you access it via the CLI?

```
cd ~/Docs
```

Or view its contents?

```
ls -al ~/Docs
```

---

### Post by petroskhan on 2007-06-23
Ok, I tried all the things you listed, and they all worked normally, but still, when I go to the directory and just click on it, I can't get to it.  This is confusing.

---

### Post by Malibu Illusion on 2007-06-24
Err..

```
mkdir ~/Docs2
cp ~/Docs/* ~/Docs2
nautilus ~/Docs2

```

If that is freezing, do you see any error outputs in the terminal window while its doing so?

---

### Post by petroskhan on 2007-06-24
Strange.  I did what you said, and as it copied it, it said "Omitting directory /home/arioch/Tahome, then it went back to the cursor.  That subdirectory is the one I was trying to copy things to.  THEN, when I went ahead and executed the Nautilus command, it opened a window showing me the contents, but when I went to click on one of the items, it froze up like the original directory did, so now I have two directories that I can't access.  LOL..but I feel like I'm getting somewhere, actually.

---

### Post by petroskhan on 2007-07-04
Well, no one seems to care, and no one should anymore.  After starting 30 times, and running that automatic disk check that Ubuntu does, it's now working fine.  I don't really know what happened, or why, but it seems to have fixed itself.  Is there a way to run that disk check manually?  Seems handy, if it fixes problems like that.

---

