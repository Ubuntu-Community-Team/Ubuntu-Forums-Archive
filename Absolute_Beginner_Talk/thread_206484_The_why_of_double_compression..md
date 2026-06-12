---
title: "The why of double compression."
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by bbales on 2006-06-30
Ok, this is just a "I would like to know" question from some of you advanced linux folks out there.

First off, I am not asking how to unzip tar.bz2 files (I bunzip, then tar -xvf), that information is pretty much everywhere on the net, what is not on the net is the why. Why exactly are archives tarred AND bziped? Wouldnt it be easier just to bzip it and be done with it?

Inquiring minds want to know :wink:

---

### Post by Daniel0 on 2006-06-30
Now, I'm not sure. But I think that tarring (I don't know what to call it) just puts a lot of files together in one file without compressing it and that bzip2 only can compress one file (that'll be the tar file).

---

### Post by Arndt on 2006-06-30
[QUOTE=Daniel0]Now, I'm not sure. But I think that tarring (I don't know what to call it) just puts a lot of files together in one file without compressing it and that bzip2 only can compress one file (that'll be the tar file).[/QUOTE]

Yes. One often also sees package.tar.gz, where the archive has been compressed with gzip. This is also something that GNU 'tar' itself can do.

Even earlier, before 'gzip', the typical name was package.tar.Z, where the compresser 'compress' had been used. (I had to search my memory for the name of the program for a minute...)

---

### Post by FredB on 2006-06-30
Yes.

Tar do the archive, gzip / bzip2 compress it.

---

