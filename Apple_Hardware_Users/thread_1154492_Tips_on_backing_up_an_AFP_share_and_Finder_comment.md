---
title: "Tips on backing up an AFP share and Finder comments?"
date: 2009-05-09
forum: Apple Hardware Users
---

### Post by learningcurb on 2009-05-09
Hi, I've just set up my Ubuntu machine as a home fileserver for my mac using netatalk.  Basically the Ubuntu machine takes the place of a external hard drive.

I'm wondering what is the best way to back up the files stored on that server.  I would like to preserve Apple's ability add comments and color labels to files (comments that tell you where you've downloaded a file from are very useful).

1. Which of Apple's hidden HFS files are actually important to keep?  I know that finder comments are stored in the .DS_store so that needs to be saved, but I'm not sure about the others. .AppleDB, .AppleDesktop, .AppleDouble Network Trash and Temporary Items are starting to clutter up my filesystem and I would like to get rid of them if I can do so safely.

2. Are there any tools capable of extracting the comments from a .DS_store file into a plain text file?  While part of the .DS_store file is readable as plaintext, usually there are a few characters which are garbled.

3. What's the best way to incrementally back up an AFP share while preserving Finder metadata?

4. Are there any other gotchas to be aware of with netatalk?  I've noticed that symbolic links inside an afp share will sometimes result in directories that disappear on the afp client's side.  The data seems intact on the Ubuntu server's side, but it makes you wonder there is a bug that might corrupt your data.

---

### Post by tiresia on 2009-05-10
Maybe you have already read this
[http://en.wikipedia.org/wiki/.DS_Store](http://en.wikipedia.org/wiki/.DS_Store)
But have a look on the references

---

