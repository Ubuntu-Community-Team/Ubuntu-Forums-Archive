---
title: "Copy a file to all subdirectories"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by ajmatsick on 2008-02-07
First off, I apologize if this has been answered already.  After searching the Web, I could only find Windows solutions.

Anyway, here's what I'm trying to do.  I have my index.html file in my web root directory, and I'm looking for a simple way to copy that file into every subdirectory (and every subdirectory's subdirectories, and so on).

I'm aware that I'll need some sort of loop to accomplish this, but I'm unable to come up with the right one.  I really appreciate any help anyone can offer.

Thanks a lot.

---

### Post by bobloblian on 2008-02-07
there has got to be a cleaner way to do this, it wouldn't work with just `ls -R`:

 for i in `ls -R | grep \: | cut -f 1 -d :`; do if [ -d $i ]; then cp index.html $i; fi; done

Run this command from the root directory

---

### Post by ajmatsick on 2008-02-07
Thanks for the reply.  That worked for the root's subdirectories as well as 2 or 3 random sub-subdirectories, but it didn't get everything.  Is there anything else I could do?

---

### Post by bobloblian on 2008-02-08
I expected that this would actually do the trick, but it was giving me grief when I tested it on my box, so that is why I added the extra.  but you can try it.

for i in `ls -R`; do if [ -d $i ]; then cp index.html $i; fi; done

In order to troubleshoot, it is necessary for there to be more information.  insert tasks into the loop so you can see what it is doing:

for i in `ls -R`; do echo $i; if [ -d $i ]; then echo "copying to $i"; cp index.html $i; echo "copy was a success"; fi; done

You might also experience problems if the directory that is being copied to is empty, seems to me there is some issue with that.  Maybe the random directories actually have something in common, like being empty?  If so, I can't think off the top of my head a way to work around that, maybe try touching the file before you copy it? And you might also have grief if there are spaces in your directory names.  Spaces are an awful habit for file names.  Also, try running ls -R by itself, so you can see for yourself what the value of $i should be, and make sure there are some $i values that are proper directory names.

Good luck

---

