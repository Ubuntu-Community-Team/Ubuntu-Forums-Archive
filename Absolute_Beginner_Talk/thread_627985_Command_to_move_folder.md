---
title: "Command to move folder ?"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by Madj on 2007-11-30
Hi
i want to move a folder from my stockage hard drive /media/disk/Tar.gz to my hard drive  file system  /usr files.
What are the command ,please ,to move folder from the terminal?

---

### Post by Dr Small on 2007-11-30
```
mv -R /path/to/folder/ /path/to/new/folder/
```

---

### Post by Madj on 2007-11-30
So when i put
 mv -r /path/to/media/disk/Tar.gz/shrank/ /path/to/usr/apple/
the terminal respond:
mv: invalid option -- R
Try `mv --help' for more information.

Where is the mistake? thanks

---

### Post by Jaynix on 2007-11-30
looks like you put -r instead of -R

---

### Post by Madj on 2007-11-30
Also when wrote mv -R /path/to/media/disk/Tar.gz/shrank/ /path/to/usr/apple/
Te terminal respond:
mv: invalid option -- R
Try `mv --help' for more information.

So where is the mistake?Anyone know please

---

### Post by Dr Small on 2007-11-30
Hmm. There is no -R option, from what the man pages said. That is weird.

---

### Post by ray bot on 2007-11-30
Well, first of all, mv does not need -R or -r.  I think the person who posted that was thinking of cp.  Also, your paths should not include "/path/to".  That was just given as a generic example of a path.  Also, I'm assuming Tar.gz is a file and not a directory.  You should first extract it to get a folder, then move that folder.  And lastly, only root may write to /usr, so you need to add sudo to your command.  So, you should end up with something like this:
```
cd /media/disk
tar -xzf Tar.gz
sudo mv shrank /usr/apple

```
Hope that helps. :)

---

### Post by Dr Small on 2007-11-30
> **ray bot said:**
> Well, first of all, mv does not need -R or -r.  I think the person who posted that was thinking of cp.  Also, your paths should not include "/path/to".  That was just given as a generic example of a path.  Also, I'm assuming Tar.gz is a file and not a directory.  You should first extract it to get a folder, then move that folder.  And lastly, only root may write to /usr, so you need to add sudo to your command.  So, you should end up with something like this:
```
cd /media/disk
tar -xzf Tar.gz
sudo mv shrank /usr/apple

```
Hope that helps. :)
You have it right. My head is thumping from a headache, and I should stop for awhile. Yeah, I was thinking about cp.

Dr Small

---

### Post by Madj on 2007-11-30
To works i had to put the extension of it 

sudo mv shrank.tar.gz /usr/apple

and he move both folder :the already extract and the folder who wasn t ! Strange!

Anyway It works just great 

Thanks man!

---

