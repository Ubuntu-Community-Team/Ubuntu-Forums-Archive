---
title: "Looking for a Program to help me clean up music files"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by thefoolisme on 2007-04-14
Hi all, 

This may seem like a silly question, but I thought I'd pick your brains.  I have a music folder on my hard drive that is full of mp3s, separate folders with mp3s in them, and backup folders with MP3s.  This is not an efficient storage method, but what has happened is there have been too many cooks, meaning different people have converted, downloaded, etc. different music files, and stuck them all into one place, with no organization. 

I'd like to clean the files up - delete the duplicates, and have one method of storage (i.e. folders by artist, etc)  The problem is, I don't want to take all the mp3s out of folders just so I can go through them all.  We are talking TONS of mp3 files here, probably close to 100GB.  

Is there a program that will go through a directory, subfolders, and all, sniff out duplicates, and organize all of the files by a specific method, i.e. by artist?  Am I asking for too much?  I just want to get it all cleaned up to save space, and organize the collection.  Most already have good tags in place, so something that read tags might be good.  Thanks in advance.

---

### Post by spin2cool on 2007-04-14
If they're exactly the same file, just copied two different places, you can remove them with a duplicate file detector, like fdupes:
[http://ubuntu.wordpress.com/2005/10/08/find-duplicate-copies-of-files/](http://ubuntu.wordpress.com/2005/10/08/find-duplicate-copies-of-files/)

If you're looking for more intelligent removal, based on ID3 tags, there are other options:
This is one:  [http://pyfdupes.sourceforge.net/](http://pyfdupes.sourceforge.net/)
and googling for something like "ubuntu remove duplicate mp3s id3" turns up other interesting results.

---

### Post by russell.h on 2007-04-14
EasyTag is a nice little program too, at least once you figure out how to use it. I'm not sure how it handles duplicates, but you can have it write id3 tags based on the directory structure and file names of the music, or you can have it organize the directory structure and file names based on the id3 tags (sounds more like what you want).

I'm just not sure if it is "intelligent" enough for what you want, you might have to nurse it along quite a bit. It also always seemed a tad slow for some reason, took it at least several minutes just to write the tags of my small collection of ripped CDs (~10GB last I checked, but very high bitrate files).

---

