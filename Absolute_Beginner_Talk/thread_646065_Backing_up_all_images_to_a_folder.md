---
title: "Backing up all images to a folder"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by taddy_porter on 2007-12-20
I know this should be so easy, but I can't seem to get it to work.

I have a bunch of pictures on my linux drive in separate directories. I'd like to make 2 copies in another folder on a mounted network drive. 1 an exact duplicate and another that has all images moved to a single folder.

I tried this:

rsync -a /home/taddy/download/Pictures/ /home/taddy/c

and it copies a bunch but then starts erroring out and complaining like this:

cp: cannot create regular file `/home/taddy/c/Pictures/2006, October, 4/2007-12-07/2007-12-07T23:05:56-000004.JPG': No such file or directory

That message is from a cp command but the usage is the same, and the error is the same as well.

What am I missing here? Are the file names too long?

I'm trying to back up from Ubuntu to mounted windows network share. I have write access and the command moves about half my pictures over, but then it stops.

---

### Post by qpieus on 2007-12-20
> /home/taddy/c/Pictures/2006, October, 4/2007-12-07/2007-12-07T23:05:56-000004.JPG

I can't tell here what the filename is and what the directory is. Assuming the forward slashes are part of the directory path, I'd say the 2 colons are causing the problems.

Try making a duplicate of that file and then renaming it to remove the colons and then try the cp again.

---

### Post by taddy_porter on 2007-12-21
Yep, it's the colon's. I was able to tar it and the tar changed the colon's to underscores.

Is there a way to use rename to get rid of the colons?

---

### Post by JackS on 2007-12-21
Space characters in the directory or filenames can cause a problem too.

Remove the spaces or change them to the underscore _ character, or
some other character you can live with.

-Jack

---

### Post by taddy_porter on 2007-12-28
> **JackS said:**
> Space characters in the directory or filenames can cause a problem too.

Remove the spaces or change them to the underscore _ character, or
some other character you can live with.

-Jack

Is there a way to do this in a script or bash command?

---

